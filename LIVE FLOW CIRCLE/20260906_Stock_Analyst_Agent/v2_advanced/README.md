# AI Portfolio Analyst

A multi-agent stock review system built in Claude Cowork. Five agents read your previous decisions, pull fresh prices, analyse, decide Buy/Hold/Sell, and write back to Excel.

**Classroom exercise. Not investment advice.**

---

## Before you start

Two things. Both take about a minute.

**1. Get a free Alpha Vantage API key**

Go to **https://www.alphavantage.co/support/#api-key**, click **Get Free API Key**, and fill the short form. It asks for a name, an email, and a website. Use any email you are comfortable sharing — a personal one, a work one, or a spare account, it makes no difference. Any website is fine too, your own or `example.com`. The key appears on screen straight away.

Copy it somewhere handy. You will paste it once, in Step 3.

**2. Download the Excel file**

Download **`portfolio_state_starter_template.xlsx`** from this repository. Leave it in your Downloads for now — Step 2 tells you where it goes.

---

## Step 1 — Set up the folder

Create one empty folder on your computer. Call it `ai-portfolio-analyst`. Select it in Claude Cowork.

Paste this prompt. Run it once.

```
Set up a multi-agent stock analysis system inside the folder I have selected
in Claude Cowork. Do not analyse any stocks yet. Only create the folders and
instruction files.

## RULE 0 — STAY INSIDE THE SELECTED FOLDER

Everything you create goes inside the folder I selected in Cowork. Nothing
goes anywhere else. Not my Desktop, not my Documents, not my home directory,
not a temp directory, not a scratch folder of your own choosing.

Every path you write is relative to that selected folder. Before you write
any file, confirm the path sits inside it. If a task seems to need a file
outside it, stop and ask me instead of doing it.

This rule outranks every other instruction in this prompt.

## CREATE THESE FOUR FOLDERS

  01_input/       Everything I give you goes here.
  02_output/      Everything you generate goes here.
  03_archive/     Superseded files go here.
  04_dashboard/   The HTML dashboard goes here.

Create these four inside the selected folder and nothing else. Do not create
extra folders — no src/, no data/, no temp/, no scripts/. If you need
scratch space, use 02_output/.

The Excel template and my API key do not exist yet. I will add both after
this prompt finishes. Do not create a template, and do not look for either
one now.

## THREE RULES

  1. Anything I give you is stored in 01_input/.
  2. Everything you generate is written to 02_output/.
  3. NEVER DELETE. If I say delete, remove, clear or drop a file, MOVE it to
     03_archive/ with a timestamp suffix and tell me what you moved.
     No exceptions.

## STOCKS

NVDA, AAPL, GOOGL, MSFT, AMZN, TSM, SPCX, AVGO, META, TSLA

## API BUDGET — HARD LIMIT

Alpha Vantage free tier = 25 calls per day.
Agent 02 is the only agent allowed to call the API. It makes one call per
ticker (TIME_SERIES_DAILY, compact) = 10 calls, and saves the raw responses
to 02_output/raw_cache_<YYYYMMDD>.json. Agent 03 computes every indicator
from that cache in Python and never calls the API. If today's cache already
exists, Agent 02 reuses it and makes zero calls.

## THE API KEY

Stored at 01_input/api_key.txt — the file contains the key and nothing else.
Agent 01 creates it by asking me. Agent 02 reads it.

Never print the key in full, never write it into a workbook, a dashboard, a
log, a filename, or any file in 02_output/. When you need to confirm it, show
the last four characters only.

## THE FILE EVERY AGENT WORKS ON

01_input/portfolio_state_starter_template.xlsx
Sheet "Portfolio State". Header in row 4, data from row 5. Twenty columns:

  A Ticker              H Current Date        O Fundamental Detail
  B Company             I Current Price ($)   P Final Decision
  C Position Status     J Change ($)          Q Confidence (1-5)
  D Last Review Date    K Change (%)          R Rationale
  E Reference Price ($) L Technical View      S Updated Status
  F Previous Decision   M Technical Detail    T Decision Timestamp
  G Previous Notes      N Fundamental View

C, F and G are filled in by me. D and E come pre-filled. J and K are
formulas — read them, never overwrite them with values. Row 5 is a greyed
EXAMPLE row that I delete before the first run.

## CREATE CLAUDE.md IN THE SELECTED FOLDER

Containing: purpose, Rule 0 verbatim, the three rules verbatim, the API key
handling rules, the stock list, the API budget, the column list above, the
agent table, and the disclaimer that this is a classroom exercise and not
investment advice.

## CREATE FIVE AGENT FILES IN agents/

  agent-01-state.md      Setup check and read previous state
  agent-02-data.md       Fetch market data
  agent-03-analysis.md   Technical + fundamental analysis
  agent-04-decision.md   Decide and update state
  agent-05-save.md       Save, archive, dashboard

Each file uses exactly these headings:

  # Agent <NN> — <Name>
  ## Activation      the exact phrase, e.g. "Activate Agent 02"
  ## Inputs          exact file paths it reads
  ## Steps           numbered and concrete
  ## Outputs         exact file paths it writes
  ## Guardrails      what it must never do, starting with Rule 0
  ## Done when       how I know it finished

## WHAT EACH AGENT DOES

Agent 01 — Setup check and read previous state
  Step 1. Check 01_input/portfolio_state_starter_template.xlsx exists. If it
  does not, STOP and tell me to download it and put it there. Do not create
  a replacement.
  Step 2. Check 01_input/api_key.txt exists. If it does not, ask me:
  "Paste your Alpha Vantage API key." Wait for my reply, save exactly what I
  paste to 01_input/api_key.txt, and confirm with the last four characters
  only. If it already exists, say so and move on — do not ask again.
  Step 3. Read the newest workbook in 02_output/, or the starter template if
  02_output/ is empty. Report each stock's previous decision, reference
  price and last review date. If column C, F or G is blank, say which stocks
  are missing them and ask me. Never guess.

Agent 02 — Fetch market data
  Read the key from 01_input/api_key.txt. One API call per ticker. Save the
  raw cache to 02_output/. If the API returns a rate-limit or invalid-key
  message, stop and tell me plainly which one it was. Report calls used and
  budget remaining. Write columns H and I.

Agent 03 — Analysis
  Read the cache only. Compute in Python: 20 and 50-day moving averages,
  RSI(14), MACD, 20-day support and resistance, volume trend, 1-month
  momentum. Write columns L and M. Then assess growth, margins, valuation
  and risks and write columns N and O. Show the numbers behind both. Say
  "insufficient history" instead of guessing.

Agent 04 — Decide and update
  Combine the two views into Buy / Hold / Sell plus confidence 1-5 and a
  written rationale — columns P, Q, R. Publish the combination rule as a
  table so I can audit it. Then carry this run backward: H into D, I into E,
  P into F, R into G. Write S and T.

Agent 05 — Save
  Write 02_output/portfolio_state_<YYYYMMDD>.xlsx and move the superseded
  copy to 03_archive/. Recalculate and confirm zero formula errors. Build a
  self-contained HTML dashboard at 04_dashboard/dashboard_<YYYYMMDD>.html
  showing decision counts, one card per stock, and every decision that
  changed since the last run.

## THEN

Show me the folder tree and the five activation phrases. Confirm that every
path you created sits inside the folder I selected. Do not analyse any
stocks.
```

---

## Step 2 — Move the Excel file in

Put `portfolio_state_starter_template.xlsx` into the `01_input/` folder that Step 1 just created.

Open it. The first tab tells you what to fill in — three yellow columns, then save and close.

---

## Step 3 — Read previous state

```
Activate Agent 01
```

It will ask you to paste your Alpha Vantage API key. Paste it and press enter. It saves the key and never asks again.

---

## Step 4 — Fetch market data

```
Activate Agent 02
```

---

## Step 5 — Run the analysis

```
Activate Agent 03
```

---

## Step 6 — Make the decision

```
Activate Agent 04
```

---

## Step 7 — Save and build the dashboard

```
Activate Agent 05
```

---

## Running it again

Repeat Steps 3 to 7. Nothing else. Agent 04 fills the yellow columns for you, so every run after the first is a review of the last one.

Your key is yours — keep `01_input/api_key.txt` off GitHub and out of screenshots.

---

## Disclaimer

Market data may be delayed or wrong. The analysis is generated by a language model and is not reviewed by any qualified person. Nothing here is investment advice, a recommendation, or a solicitation to trade. Do not risk money on it.
