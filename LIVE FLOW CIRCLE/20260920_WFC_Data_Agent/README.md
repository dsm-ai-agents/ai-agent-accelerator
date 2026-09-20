# Data Analyst Agent

Four agents. They read your eCommerce Store data, explain it, chart it, and put it online.

You run one delegation prompt to set everything up. Then you type `Activate Agent 1`, `Activate Agent 2`, `Activate Agent 3`, `Activate Agent 4`, one at a time.

## Dataset

Project: `eCommerce`
Connect with: Supabase connector and Vercel connector in Claude

**tbl_customers** (1,000 rows)
`Customer_ID`, `Customer_Name`, `Customer_Email`, `Customer_Number`, `Age`, `Gender`, `Location`

**tbl_transactions** (3,000 rows)
`Transaction_ID`, `Date_of_Purchase`, `Customer_ID`, `Product_Category`, `Product_Name`, `Units`, `Price`, `Discounts`, `Returned`, `Mode_of_Payment`, `Purchase_Channel`

The two tables join on `Customer_ID`. Data covers March 2021 to March 2023.

---

## V1 - Delegation Prompt
```
Create a four-agent e-commerce reporting pipeline using the `eCommerce` database connected through Supabase MCP.

Important rules:

* Use read-only queries.
* Quote mixed-case column names.
* Convert `"Date_of_Purchase"` from `DD-MM-YYYY`.
* Join the customer and transaction tables using `"Customer_ID"`.
* Never expose customer names, emails, or phone numbers.

First, propose the architecture, workflow, folders, agent responsibilities, and outputs for my approval.

After approval, create `CLAUDE.md` and these agents:

* `agent1.md` — explore, clean, join, and validate the data.
* `agent2.md` — produce KPIs, trends, segments, exceptions, and business insights.
* `agent3.md` — build a single-file offline HTML dashboard.
* `agent4.md` — validate privacy and deploy the dashboard through the Vercel connector after my approval.

Agents must share results through files, not chat. Give every agent clear inputs, steps, outputs, rules, completion criteria, and escalation instructions.

Create files only. Do not run any agent. After creation, show the folder tree and wait for `Activate Agent 1`.

```

## V2 Detailed Prompt

Paste this once. It builds everything and then stops.

```
Role: You are a data analyst setting up a four-agent workflow in this folder.

Context:
My data is in the eCommerce, schema public, connected through the Supabase MCP connector. There are two tables:

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
   - dashboard holds the dashboard HTML file.

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
   summary.json must use exactly this shape, because Agent 3 reads these exact keys:
     {
       "kpis": { "revenue": 0, "transactions": 0, "customers": 0, "avg_order_value": 0, "return_rate_pct": 0 },
       "revenue_by_month":    [ { "label": "2021-03", "value": 0 } ],
       "revenue_by_category": [ { "label": "Toys", "value": 0 } ],
       "revenue_by_channel":  [ { "label": "Online", "value": 0 } ],
       "revenue_by_payment":  [ { "label": "UPI", "value": 0 } ],
       "top_products":        [ { "name": "Product name", "revenue": 0, "transactions": 0 } ]
     }
   Every value must be a plain number, not text. Supabase returns totals as text like "14623.75", so convert them. No currency symbols or commas inside the numbers. revenue_by_month must list every month in date order.
   Rules: every number comes from a query, never a guess; say which table each number came from; never name an individual customer; keep the opening summary under 150 words.
   Done When: both files exist, the numbers match, and the revenue formula is stated.

   agents/agent3.md - Build the dashboard
   Purpose: show the summary as charts in a single HTML file I can open on my laptop.
   Inputs: output/summary.json and output/schema.json.
   Steps:
     - Build one file, dashboard/index.html. Everything goes inside it: the HTML, the CSS, the JavaScript and the numbers. No build step, no server, no npm.
     - Do not use any charting library and do not load anything from a CDN or the internet. If that script fails to load, every chart goes blank. Draw the charts yourself with plain HTML, CSS and SVG:
         bar charts: one row per item, a div bar whose width is a percentage of the largest value, with the label and the number beside it
         monthly trend: an SVG polyline, with the first and last month labelled under it
     - Do not use fetch() and do not load summary.json from disk. Browsers block that when a file is opened by double-clicking, and the page comes out blank. Instead, copy the full contents of output/summary.json into the file as: const DATA = { ... };
       Write out every value. No placeholders, no "...", no comments like "add the remaining months here".
     - Read only these keys from DATA: kpis, revenue_by_month, revenue_by_category, revenue_by_channel, revenue_by_payment, top_products.
     - Build these six visuals: KPI cards (revenue, transactions, customers, average order value, return rate); revenue by month as a line; revenue by Product_Category as bars; Purchase_Channel as bars; Mode_of_Payment as bars; top products as a table.
     - Wrap the code for each visual in its own try/catch. If a visual fails or its data is empty, write a red message inside that card saying what is missing. A card must never be silently blank, and one broken chart must not stop the others.
     - Before you say you are done, read dashboard/index.html back and check all of these:
         there is no <script src= tag and no fetch( anywhere in the file
         DATA contains all six keys, and every list in it has at least one item
         revenue_by_month has the same number of months as summary.json
         every key the drawing code reads exists in DATA with the same spelling
       Fix anything that fails, then check again. If you can open the file in a browser, do that too and confirm every card shows data.
   Outputs: dashboard/index.html and output/dashboard_notes.md telling me what each visual shows.
   Rules: one file only; no external scripts, no CDN, no fetch; no Supabase keys anywhere in it; no customer names, emails or phone numbers; it must work by double-clicking the file with no internet.
   Done When: all the checks above pass and double-clicking dashboard/index.html opens a page with every card filled in.

   agents/agent4.md - Put it online
   Purpose: deploy the dashboard to Vercel using the Vercel connector in Claude.
   Inputs: the dashboard/ folder and the Vercel connector.
   Steps:
     - Check dashboard/index.html opens and every chart renders. Stop if it does not.
     - Search dashboard/ for any keys, .env files, or customer names, emails and phone numbers. Stop if you find any.
     - Ask me for the project name and whether the link should be public. Wait for my answer.
     - Deploy to Vercel through the Vercel connector. Do not use the Vercel CLI or npm. If the connector is not connected, stop and tell me to connect it.
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
Show me the folder tree, confirm each agent file in one line, then wait for me to type Activate Agent 1.
```

---

## Activation

Run these one at a time. Check the output files exist before moving on.

```
Activate Agent 1
```

```
Activate Agent 2
```

```
Activate Agent 3
```

```
Activate Agent 4
```

To start over:

```
Archive the current output and start a new run.
```
