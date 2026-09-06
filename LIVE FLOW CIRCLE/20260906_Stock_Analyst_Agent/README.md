# AI Portfolio Analyst — Multi-Agent Build

Build a multi-agent stock review system in Claude Cowork. It reads the previous run's decisions, pulls fresh prices, runs technical and fundamental analysis, decides Buy/Hold/Sell, and writes back to Excel.

**Classroom exercise. Not investment advice.**

---

## Step 1 — Create the folder

```
ai-portfolio-analyst/
├── 01_starter_template/     INPUT
├── 02_output/               OUTPUT
├── 03_archive/              ARCHIVE (nothing is ever deleted)
└── 04_dashboard/            DASHBOARD
```

Put `portfolio_state_starter_template.xlsx` in `01_starter_template/`. Connect the folder in Cowork.

---

## Step 2 — Run the setup prompt

Paste this into Cowork. Run it **once**. It creates `CLAUDE.md` and nine agent files.

```
You are setting up a multi-agent stock analysis system in this connected folder.
Do not analyse any stocks yet. Create the instruction files only.

## FOLDER RULES — these override any later instruction

  01_starter_template/   INPUT. Every file the user supplies goes here.
  02_output/             OUTPUT. Every workbook and artifact goes here.
  03_archive/            ARCHIVE. Superseded files go here.
  04_dashboard/          DASHBOARD. The HTML dashboard goes here.

  RULE 1 — Anything the user supplies is stored in 01_starter_template/.
  RULE 2 — Everything you generate is written to 02_output/.
  RULE 3 — NEVER DELETE. If the user says delete, remove, clear, or drop a
           file, MOVE it to 03_archive/ with a timestamp suffix
           (filename_YYYYMMDD_HHMMSS.ext) and report what you moved.
           You never issue a delete. No exceptions.

## STOCK BASKET

NVDA, AAPL, GOOGL, MSFT, AMZN, TSM, SPCX, AVGO, META, TSLA

## API BUDGET — HARD CONSTRAINT

Alpha Vantage free tier allows 25 calls per day.

  - Agent 03 is the ONLY agent allowed to call the API.
  - Agent 03 makes ONE call per ticker (TIME_SERIES_DAILY, compact = 100 days
    of OHLCV). Ten tickers = ten calls.
  - Agent 03 writes raw responses to 02_output/raw_cache_<YYYYMMDD>.json.
  - Agents 04a and 04b compute ALL indicators (RSI, MACD, moving averages,
    support, resistance, momentum, volume) from that cache in Python. They
    are FORBIDDEN from calling the API.
  - If today's cache already exists, Agent 03 reuses it and makes zero calls.

## CREATE: CLAUDE.md in the project root

Contents, in order:
  - Purpose, two sentences.
  - The folder rules above, verbatim.
  - The stock basket.
  - The API budget constraint.
  - The state schema table.
  - Agent roster table: number, name, job, reads, writes, activation phrase.
  - How to run: the activation phrases in order.
  - Disclaimer: classroom exercise, not investment advice.

CLAUDE.md is a routing document. Detailed instructions live in the agent
files, not here.

## CREATE: nine files in agents/

  agent-01-basket.md        Basket Manager
  agent-02-state-reader.md  State Reader
  agent-03-fetch.md         Market Data Fetcher
  agent-04a-technical.md    Technical Analysis Agent
  agent-04b-fundamental.md  Fundamental Review Agent
  agent-05-decision.md      Decision Agent
  agent-06-update.md        State Updater
  agent-07-save.md          Save & Archive
  agent-08-dashboard.md     Dashboard Builder

Every agent file uses EXACTLY these headings:

  # Agent <NN> — <Name>
  ## Activation        the exact phrase, e.g. "Activate Agent 03"
  ## Purpose           one paragraph
  ## Inputs            exact file paths this agent reads
  ## Preconditions     what must exist; what to say if it does not
  ## Steps             numbered, concrete, in order
  ## Outputs           exact file paths this agent writes
  ## Guardrails        what this agent must never do
  ## Done when         the observable completion condition

Fill every section with real executable instructions, not placeholders.

## AGENT SPECIFICS

01 Basket Manager
   Owns 01_starter_template/portfolio_state_starter_template.xlsx and its
   schema. Only regenerates it if missing. Uses openpyxl. Change ($) and
   Change (%) are formulas, never hardcoded values.

02 State Reader
   Reads the latest 02_output/portfolio_state_<date>.xlsx if one exists,
   otherwise the starter template. Reports ticker, previous decision,
   reference price, last review date, position status. If a previous-state
   field is blank, says so per ticker and asks the user — never guesses.
   Flags any price change over 20% as a possible split or dividend.

03 Market Data Fetcher
   One TIME_SERIES_DAILY call per ticker. Writes
   02_output/raw_cache_<YYYYMMDD>.json. Reports calls used and budget left.
   Reuses a same-day cache and makes zero calls if present.

04a Technical Analysis Agent
   Reads the cache only. Computes in Python: 20/50-day moving averages and
   price position vs each, RSI(14), MACD(12,26,9), 20-day support and
   resistance, 10-day volume trend, 1-month momentum. Assigns Bullish /
   Neutral / Bearish with the numbers that justify it, and states the rule
   used. Reports "insufficient history" rather than a wrong number when a
   ticker lacks enough data.

04b Fundamental Review Agent
   Assesses revenue growth, earnings, margins, valuation, guidance,
   competitive strength, risks. Assigns Strong / Solid / Weak. Cites the
   source of every figure. Writes "not available" rather than estimating.

05 Decision Agent
   Combines 04a and 04b into Buy / Hold / Sell plus confidence 1-5 and a
   written rationale. Publishes the combination rule as an explicit table so
   the logic is auditable. Flags every ticker where the two views disagree.

06 State Updater
   Carries this run backward into the previous-state columns: Current Date →
   Last Review Date, Current Price → Reference Price, Final Decision →
   Previous Decision, Rationale → Previous Notes. Writes Updated Status and
   Decision Timestamp. This is what makes the next run a review.

07 Save & Archive
   Writes 02_output/portfolio_state_<YYYYMMDD>.xlsx. Moves the superseded
   workbook to 03_archive/ with a timestamp. Recalculates and confirms zero
   formula errors.

08 Dashboard Builder
   Builds a self-contained HTML file at
   04_dashboard/dashboard_<YYYYMMDD>.html from the latest workbook: decision
   counts, a card per ticker with price change, both views, decision and
   confidence, and every ticker whose decision changed since the last run.
   All CSS and JS inline. Archives the previous dashboard.

## OUTPUT

Create the folders, CLAUDE.md, and all nine agent files. Show me a tree of
what you created and the activation phrase list. Do not analyse any stocks.
```

---

## Step 3 — Fill the yellow columns

Open the starter template. Fill three columns by hand for each stock:

| Column | What to enter |
|---|---|
| Position Status | Held / Watching / Exited |
| Previous Decision | Buy / Hold / Sell |
| Previous Notes | Why you hold that view |

`Last Review Date` and `Reference Price` are pre-filled with the 2026-08-04 close. From the second run on, Agent 06 fills all five automatically.

---

## Step 4 — Run the agents

```
Activate Agent 01
Activate Agent 02
Activate Agent 03
Activate Agent 04a
Activate Agent 04b
Activate Agent 05
Activate Agent 06
Activate Agent 07
Activate Agent 08
```

Every run after the first: skip Agent 01, start at Agent 02.

Variants that work:

```
Activate Agent 03 for NVDA and TSLA only
Activate Agent 05 and explain the rule you used for TSLA
Run the full pipeline, Agents 02 through 08
```

---

## Reference — state schema

| Column | Filled by |
|---|---|
| Ticker | Given |
| Company | Given |
| Position Status | **You** → Agent 06 |
| Last Review Date | Given → Agent 06 |
| Reference Price ($) | Given → Agent 06 |
| Previous Decision | **You** → Agent 06 |
| Previous Notes | **You** → Agent 06 |
| Current Date | Agent 03 |
| Current Price ($) | Agent 03 |
| Change ($) | Formula |
| Change (%) | Formula |
| Technical View | Agent 04a |
| Technical Detail | Agent 04a |
| Fundamental View | Agent 04b |
| Fundamental Detail | Agent 04b |
| Final Decision | Agent 05 |
| Confidence (1-5) | Agent 05 |
| Rationale | Agent 05 |
| Updated Status | Agent 06 |
| Decision Timestamp | Agent 06 |

---

## Reference — CLAUDE.md structure

```markdown
# AI Portfolio Analyst

## Purpose
## Folder Rules
## Stock Basket
## API Budget
## State Schema
## Agent Roster
## How to Run
## Disclaimer
```

## Reference — agent file structure

```markdown
# Agent <NN> — <Name>

## Activation
## Purpose
## Inputs
## Preconditions
## Steps
## Outputs
## Guardrails
## Done when
```

---

## Gotchas

- **SPCX** began trading 2026-06-12. Indicators needing 100+ days will not compute.
- **TSM** is the US-listed ADR, not the Taiwan local share.
- Prices are **unadjusted closes**. A split or dividend looks like a price move.
- Re-running Agent 03 in one day should hit the cache. If it doesn't, you'll burn the budget.

---

## Disclaimer

Market data may be delayed or wrong. The analysis is generated by a language model and is not reviewed by any qualified person. Nothing here is investment advice, a recommendation, or a solicitation to trade. Do not risk money on it.
