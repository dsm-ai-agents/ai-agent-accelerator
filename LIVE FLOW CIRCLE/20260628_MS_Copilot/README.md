# Copilot Frontier — Prompt Pack

---

## Module 1 — Researcher

Give it a research task. Get a cited briefing back. Reads the web **plus** your emails, meetings, and files.

**Demo — competitive briefing:**

```
Prepare a competitive briefing on [COMPETITOR]. Combine recent public news
with what our account teams have said about them in emails and meeting notes
from the last quarter. Structure it as: what changed, why it matters to us,
and three questions we should be asking. Cite every source.
```

**Rep — your turn:**

```
Prepare a briefing on [TOPIC YOU'D ASSIGN TO A JUNIOR]. Use public sources
plus our internal emails, meetings, and files. Cite everything. I need:
summary, what it means for us, and open questions.
```

---

## Module 2 — Analyst

Hand it a spreadsheet and a question. It writes and runs Python on your data — the code is visible, so you can audit it. It computes; it doesn't guess.

**Demo — sales data analysis** (attach `demo-sales-data.xlsx`):

```
Analyze this data — show growth by region, flag anomalies, and chart the overall trend.
```

> Expected catches: a unit/revenue spike (West / Beacon, Nov 2025) and a negative-revenue row (Central / Drift, Feb 2026). If it finds both, that's the trust moment.

**30-second trust habit:** ask for row counts and totals first, check them against the sheet, *then* trust the analysis.

**Rep — your turn:**

```
Here is [YOUR DATA FILE]. Answer this: [THE QUESTION YOU ARE CURRENTLY
WAITING ON SOMEONE ELSE FOR]. Show your reasoning step by step.
```

---

## Module 3 — Agents in Excel, Word, PowerPoint

Same data as Module 2, deliberately — Module 2 *answered a question*, Module 3 *builds the artifact*. Run each prompt inside its app.

**Excel Agent** (on `demo-sales-data.xlsx`):

```
Analyze this data — add a summary sheet with growth by region, flag anomalies,
and build a chart showing the trend.
```

**Word Agent:**

```
Draft a one-page client memo summarizing the regional sales analysis: what grew,
what we flagged, and the recommended next step. Formal tone, with a header and a
summary table.
```

**PowerPoint Agent:**

```
Turn this memo into a 5-slide executive deck: situation, growth by region,
anomalies, trend, recommendation.
```

> **Data flows by manual handoff — you are the connector.** Excel writes the analysis into the file → you attach that file in Word → you attach the Word doc in PowerPoint. Between each step you review: did the analysis catch the anomaly before it travels into the deck?

---

## Module 4 — Create

Brand visuals — images, posters, banners, infographics — without a designer and without leaving Copilot. Open **Create** from the app launcher.

**Demo — all-hands poster:**

```
Create a poster announcing our quarterly all-hands: clean corporate style,
our brand colors, headline 'Q3 Town Hall', date and Teams link placeholder.
```

**Demo — edit, don't regenerate** (refining beats starting over):

```
Change the headline color to match our brand teal and make the date larger.
```

**Exercises — your turn:**

```
Create an announcement visual for [YOUR NEXT TEAM EVENT]: [STYLE],
headline '[TITLE]', date placeholder.
```

```
Create an infographic explaining [THE PROCESS YOUR TEAM EXPLAINS REPEATEDLY]
in [N] simple steps.
```

> Then set up a brand kit (**Manage brand kits → Brand kits**), re-run the first prompt, and compare. Brand kits keep every output on-brand — set once, reuse everywhere.

---

## Module 5 — Build Your Own Agent

Instructions + your documents = a teammate. No code.

**Agent instructions — Proposal Reviewer** (paste as the agent's instructions in *New agent*; attach `proposal-standards.docx` as its knowledge):

```
You review draft proposals against our standards document. Flag missing sections,
pricing errors, and claims we cannot support. Reply as a checklist: PASS or FLAG
for each standard, with a one-line reason. Be strict. If a section is missing
entirely, say so first.
```

**Demo test** (attach `sample-proposal.docx` — it has planted violations):

```
Review the attached draft proposal.
```

**Rep — spec template:**

```
Agent name: [NAME]. Who it serves: [TEAM]. What it knows: [THE 1-3 DOCUMENTS
IT SHOULD FOLLOW]. What it does: [THE REPEATED TASK]. How it answers:
[FORMAT — checklist, draft, summary].
```

---

## Module 6 — Workflows

Describe a routine once. Copilot runs it every day. Type into **Workflows (Frontier)** from the Agents sidebar.

**Demo — morning brief:**

```
Every weekday at 8:30 AM, send me a Teams message with my meetings for today
and a summary of important unread emails from yesterday.
```

**Demo — conversational edit** (edit the workflow by talking to it):

```
Also include my top 3 priorities from Planner in the same message.
```

**Rep — your turn:**

```
Every weekday at [TIME], send me a Teams message with [THE THING YOU CHECK
MANUALLY EVERY MORNING].
```

---
## Files in this repo

| File | Use |
|------|-----|
| `copilot-frontier-course-v2.pptx` | The course deck (8 modules, Workflows last) |
| `demo-sales-data.xlsx` | Dataset for Modules 2 and 3 (planted anomalies) |
| `proposal-standards.docx` | Knowledge doc for the Module 5 agent |
| `sample-proposal.docx` | Flawed proposal to test the Module 5 agent |
