# AI Portfolio Analyst

A multi-agent stock review system built in Claude Cowork. Five agents read your previous decisions, pull fresh prices, analyse, decide Buy/Hold/Sell, and write back to Excel.

**Classroom exercise. Not investment advice.**

---

## Step 1 — Set up the folder

Create one empty folder on your computer. Call it `ai-portfolio-analyst`. Connect it in Cowork.

Paste this prompt. Run it once.

```
Set up a multi-agent stock analysis system in this folder.
Do not analyse any stocks yet. Only create the folders and instruction files.

## CREATE THESE FOLDERS

  01_starter_template/   Input. The Excel template will be placed here.
  02_output/             Output. Everything you generate goes here.
  03_archive/            Archive. Superseded files go here.
  04_dashboard/          Dashboard. The HTML dashboard goes here.

The Excel template does not exist yet. I will download it and put it in
01_starter_template/ after this prompt finishes. Do not create one, and do
not look for it now.

## THREE RULES — these override anything I say later

  1. Anything I give you is stored in 01_starter_template/.
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

## THE FILE EVERY AGENT WORKS ON

01_starter_template/portfolio_state_starter_template.xlsx
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

## CREATE CLAUDE.md

Containing: purpose, the three rules verbatim, the stock list, the API
budget, the column list above, the agent table, and the disclaimer that
this is a classroom exercise and not investment advice.

## CREATE FIVE AGENT FILES IN agents/

  agent-01-state.md      Read previous state
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
  ## Guardrails      what it must never do
  ## Done when       how I know it finished

## WHAT EACH AGENT DOES

Agent 01 — Read previous state
  First, check that 01_starter_template/portfolio_state_starter_template.xlsx
  exists. If it does not, STOP and tell me to download it and put it there.
  Do not create a replacement.
  Then read the newest workbook in 02_output/, or the starter template if
  02_output/ is empty. Report each stock's previous decision, reference
  price and last review date. If column C, F or G is blank, say which stocks
  are missing them and ask me. Never guess.

Agent 02 — Fetch market data
  One API call per ticker. Save the raw cache. Report calls used and budget
  remaining. Write columns H and I.

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

Show me the folder tree and the five activation phrases. Do not analyse
any stocks.
```

---

## Step 2 — Download the template

Download **`portfolio_state_starter_template.xlsx`** from this repository and put it in the `01_starter_template/` folder that Step 1 just created.

Open it. The first tab tells you what to fill in — three yellow columns, then save and close.

---

## Step 3 — Read previous state

```
Activate Agent 01
```

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

---

## Disclaimer

Market data may be delayed or wrong. The analysis is generated by a language model and is not reviewed by any qualified person. Nothing here is investment advice, a recommendation, or a solicitation to trade. Do not risk money on it.
