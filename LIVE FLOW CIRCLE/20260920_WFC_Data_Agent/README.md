# Supabase Data Agent

Four agents. They read your Supabase data, explain it, chart it, and put it online.

You run one big prompt to set everything up. Then you type `ActivateAgent1`, `ActivateAgent2`, `ActivateAgent3`, `ActivateAgent4`, one at a time.

## Dataset

Supabase project: `Weekly_Flow_Circle`
Connect with: Supabase MCP connector

**tbl_customers** (1,000 rows)
`Customer_ID`, `Customer_Name`, `Customer_Email`, `Customer_Number`, `Age`, `Gender`, `Location`

**tbl_transactions** (3,000 rows)
`Transaction_ID`, `Date_of_Purchase`, `Customer_ID`, `Product_Category`, `Product_Name`, `Units`, `Price`, `Discounts`, `Returned`, `Mode_of_Payment`, `Purchase_Channel`

The two tables join on `Customer_ID`. Data covers March 2021 to March 2023.

---

## Master Prompt

Paste this once. It builds everything and then stops.

```
Role: You are a data analyst setting up a four-agent workflow in this folder.

Context:
My data is in the Supabase project "Weekly_Flow_Circle", schema public, connected through the Supabase MCP connector. There are two tables:

tbl_customers, 1000 rows, primary key Customer_ID
  Customer_ID, Customer_Name, Customer_Email, Customer_Number, Age, Gender, Location

tbl_transactions, 3000 rows, primary key Transaction_ID
  Transaction_ID, Date_of_Purchase, Customer_ID, Product_Category, Product_Name, Units, Price, Discounts, Returned, Mode_of_Payment, Purchase_Channel

Four things about this database that will break your SQL if you ignore them:
1. Column names are mixed case. Always put them in double quotes: select "Customer_ID" from public.tbl_customers. Without quotes the query fails.
2. Date_of_Purchase is text in DD-MM-YYYY format, not a real date. Convert it before any date work: to_date("Date_of_Purchase", 'DD-MM-YYYY'). Sorting it as text gives the wrong order.
3. There is no foreign key between the tables. tbl_transactions.Customer_ID matches tbl_customers.Customer_ID, but the database does not enforce it, so check it yourself.
4. Row Level Security is on with no policies. The MCP connector works fine. If you ever get zero rows, that is a permissions problem, not an empty table.

Task:
Set up the project. Create files only. Do not run any agent yet.

1. Create four folders: input, output, archive, dashboard. And a folder called agents.
   - input is where I put questions for you. You only read it.
   - output is where every agent writes its results.
   - archive holds old runs.
   - dashboard holds the dashboard app.

2. Create CLAUDE.md with these rules:
   - Read only. Never INSERT, UPDATE, DELETE, DROP or ALTER.
   - Always quote column names. Always convert Date_of_Purchase with to_date.
   - Agents read each other's files in output/, not the chat.
   - Customer_Name, Customer_Email and Customer_Number are personal data. Never put them in output/, in the dashboard, or online. Counts and groups only.
   - Explain things in plain English. No jargon.
   - If something is unclear, ask me before continuing.

3. Create four files in agents/. Each one needs these sections: Purpose, Inputs, Steps, Outputs, Rules, Done When, and Ask Me If.

   agents/agent1.md - Explore the database
   Purpose: work out what is in the database before anyone summarizes it.
   Inputs: the Supabase connection.
   Steps:
     - List both tables with their columns, data types and row counts.
     - Check the Customer_ID link: count transactions whose Customer_ID has no matching customer. Report that number.
     - Say how many customers actually have transactions, and the average and highest number of transactions per customer.
     - For Gender, Location, Product_Category, Mode_of_Payment and Purchase_Channel, list the distinct values and how many of each.
     - Count nulls in every column.
     - Report the earliest and latest purchase date using to_date.
   Outputs: output/schema_report.md for me to read, and output/schema.json for the other agents.
   Rules: read only; quote every column name; for the name, email and phone columns report counts only, never the values.
   Done When: both files exist and the Customer_ID link is backed by the orphan count.

   agents/agent2.md - Summarize the data
   Purpose: turn the data into numbers a business person can act on.
   Inputs: output/schema.json, the Supabase data, anything in input/.
   Steps:
     - Revenue is ("Price" * "Units") - "Discounts". Write this formula in your summary so I know what you counted.
     - Half the transactions in this data are marked Returned. Decide whether returned transactions count as revenue, say which you chose, and show the total both ways so I can see the difference.
     - Report: total revenue, total transactions, how many customers bought, average order value, and return rate.
     - Break revenue down by Product_Category, by Purchase_Channel, and by Mode_of_Payment.
     - Show revenue by month using to_date, so I can see the trend.
     - List the top 10 products by revenue.
     - Group customers by age band and by Location.
     - Count how many customers bought once versus more than once.
     - Flag anything that looks wrong: nulls, zero or negative prices, discounts bigger than the sale.
     - Answer anything I put in input/.
   Outputs: output/summary.md and output/summary.json with the same numbers in both.
   Rules: every number comes from a query, never a guess; say which table each number came from; never name an individual customer; keep the opening summary under 150 words.
   Done When: both files exist, the numbers match, and the revenue formula is stated.

   agents/agent3.md - Build the dashboard
   Purpose: show the summary as charts on a page that runs on my laptop.
   Inputs: output/summary.json and output/schema.json.
   Steps:
     - Build a Next.js app in dashboard/.
     - Put the numbers in dashboard/data.json, copied from summary.json. The page reads that file, so the browser never touches the database.
     - Build these six visuals: KPI cards (revenue, transactions, customers, average order value, return rate); revenue by month as a line; revenue by Product_Category as bars; Purchase_Channel split; Mode_of_Payment split; top products as a table.
     - Install what you need, start it, and open it to check every chart shows data.
     - Run npm run build and fix anything that fails.
   Outputs: a working dashboard/ and output/dashboard_notes.md telling me how to start it.
   Rules: no Supabase keys in the dashboard; no customer names, emails or phone numbers in data.json; one page; the build must pass.
   Done When: the page opens on localhost with every chart filled in, and npm run build passes.

   agents/agent4.md - Put it online
   Purpose: deploy the dashboard to Vercel.
   Inputs: the dashboard/ folder.
   Steps:
     - Run npm run build. Stop if it fails.
     - Search dashboard/ for any keys, .env files, or customer names, emails and phone numbers. Stop if you find any.
     - Ask me for the project name and whether the link should be public. Wait for my answer.
     - Deploy to Vercel.
     - Open the live link and check it looks like the local one.
   Outputs: output/deploy_report.md with the live link.
   Rules: never deploy before I confirm; never upload .env or anything in input/.
   Done When: the live link works and matches what I saw locally.

4. End every agent file with this block:

   ## Ask Me If
   Stop and ask before continuing if:
   - a column or table does not make sense
   - the numbers look wrong, empty or duplicated
   - a connection or credential is missing
   - something could change or expose data
   Ask one question at a time. Give me 2 or 3 options to pick from. Wait for my answer.

Rules:
- Create files only. Do not run any agent.
- Copy the four database facts above into each agent file so each one works on its own.
- Do not make up credentials. If the Supabase connection is missing, tell me what to connect.

Output:
Show me the folder tree, confirm each agent file in one line, then wait for me to type ActivateAgent1.
```

---

## Activation

Run these one at a time. Check the output files exist before moving on.

```
ActivateAgent1
```

```
ActivateAgent2
```

```
ActivateAgent3
```

```
ActivateAgent4
```

To start over:

```
Archive the current output and start a new run.
```
