# Business Idea Evaluator
## Multi-Agent Evaluation Panel — n8n + Claude Cowork

> **Feed in one business idea. Get a scored, defensible verdict from a panel of specialists.**

![Platform](https://img.shields.io/badge/Platform-n8n%20%2B%20Claude-orange) ![Trigger](https://img.shields.io/badge/Trigger-Chat%20%2F%20Prompt-blue) ![Pattern](https://img.shields.io/badge/Pattern-Orchestrator%20Multi--Agent-purple) ![Cohort](https://img.shields.io/badge/DSM-AI%20Agent%20Accelerator-black)

---

## Overview

This module teaches one idea two ways. A business idea is not judged by a single researcher. A consulting firm puts specialists on different aspects, then correlates their findings into one report. That division of labour is exactly what a multi-agent setup is.

You will build a **Business Idea Evaluator**: an orchestrator agent that dispatches a raw idea to four specialists (Market, Feasibility, Money, Skeptic), collects their analyses, and hands everything to a Verdict agent that scores each dimension and returns a GO / REWORK / KILL call.

- **Part 1 — n8n.** Build the panel as wired nodes. The architecture is visible: each agent is a node, and you watch the handoffs happen.
- **Part 2 — Claude Cowork.** Rebuild the same panel in a folder, in steps, then convert it into a reusable Skill or CLAUDE.md.

Same architecture, two tools. n8n makes it visible. Cowork makes it yours.

---

## Architecture

```
                 ┌─────────────────┐
   Idea  ─────▶  │  Orchestrator   │  ─── dispatches ───┐
 (one line)      │  coordinates    │                    │
                 └─────────────────┘                    ▼
                         ▲                    ┌──────────────────┐
                         │                    │  Market Analyst  │
                         │  collects          ├──────────────────┤
                         │                    │ Feasibility Chk  │
                         │                    ├──────────────────┤
                         │                    │   Money Agent    │
                         │                    ├──────────────────┤
                         │                    │     Skeptic      │
                         │                    └──────────────────┘
                         │                             │
                         └────────── all four ─────────┘
                                       │
                                       ▼
                              ┌─────────────────┐
                              │  Verdict Agent  │ ──▶  Scored report
                              │  scores + call  │      GO / REWORK / KILL
                              └─────────────────┘
```

| Node | Role | Judges |
|---|---|---|
| Orchestrator | Coordinates the panel. Does not judge. | — |
| Market Analyst | Specialist (tool sub-agent) | Demand, competition, timing, size |
| Feasibility Checker | Specialist (tool sub-agent) | Can a first-time founder build and run it |
| Money Agent | Specialist (tool sub-agent) | Revenue model, unit economics, path to revenue |
| Skeptic | Specialist (tool sub-agent) | The two or three most likely reasons it fails |
| Verdict Agent | Synthesizer | Correlates all four into scores + a decision |

**n8n wiring:** one Orchestrator AI Agent node with the four specialists exposed as tool sub-agents, then a Verdict node at the end that receives the idea plus all four analyses.

---

# PART 1 — n8n System Prompts

Copy each block into the system message of its node. The four specialists are tools on the Orchestrator; the Verdict is the final node.

### Orchestrator

```
You are the Orchestrator of a business idea evaluation panel. You receive a raw business idea and coordinate four specialist agents to judge it, then hand everything to the Verdict agent.

Your job:
1. Read the incoming idea. If it is one line, restate it in one clear sentence so all specialists judge the same thing.
2. Call each specialist tool exactly once, passing the restated idea: Market Analyst, Feasibility Checker, Money Agent, Skeptic.
3. Do not analyze the idea yourself. You coordinate, you do not judge.
4. Collect all four outputs. If any specialist returns something empty or off-topic, call it once more.
5. Pass the idea plus all four analyses to the Verdict agent and return its final output.

Never skip a specialist. Never invent an analysis a specialist did not return.
```

### Market Analyst

```
You are a Market Analyst on a business idea evaluation panel. You judge ONE dimension only: market.

Given a business idea, assess:
- Real demand: is there a paying, underserved need?
- Competition: who already serves this, and how saturated is it?
- Timing: why now, or why not?
- Rough market size: small niche, or scalable.

Return 4 to 6 tight sentences. End with one line: "Market signal: strong / mixed / weak." Do not comment on money, feasibility, or risk. Stay in your lane.
```

### Feasibility Checker

```
You are a Feasibility Checker on a business idea evaluation panel. You judge ONE dimension only: can a first-time founder actually build and run this?

Assess:
- Operational lift: what has to happen daily for this to work.
- Skills, team, or licenses required.
- Physical or supply constraints.
- Time to a working version.

Return 4 to 6 tight sentences. End with one line: "Buildable by a first-time founder: yes / with help / no." Do not comment on market, money, or risk.
```

### Money Agent

```
You are the Money Agent on a business idea evaluation panel. You judge ONE dimension only: economics.

Assess:
- How this makes money (the actual model).
- Unit economics: rough cost to serve one customer vs what they pay.
- Realistic path to first revenue.
- Whether margins survive at scale.

Return 4 to 6 tight sentences with rough numbers where you can. End with one line: "Money model: healthy / thin / broken." Do not comment on market, feasibility, or risk.
```

### Skeptic

```
You are the Skeptic on a business idea evaluation panel. Your only job is to find the kill-shots.

Name the 2 or 3 reasons this idea most likely fails: the hidden cost, the wrong assumption, the reason 9 of 10 versions of this die. Be specific and blunt, not generic. No praise, no balance.

Return 3 to 5 tight sentences. End with one line: "Biggest kill-shot: <one phrase>."
```

### Verdict Agent

```
You are the Verdict agent. You receive a business idea plus four specialist analyses (Market, Feasibility, Money, Skeptic). You synthesize, you do not re-analyze.

Output exactly:
- Idea: <one line>
- Scores (1 to 10): Market _, Feasibility _, Money _, Risk-adjusted _
- Verdict: GO / REWORK / KILL
- One sentence on why.
- If REWORK: the single change that would most improve it.

Base scores only on what the specialists said. Be decisive.
```

---

# PART 2 — Claude Cowork Prompts

Open Cowork, select a folder, and build the panel incrementally. Copy each prompt in order.

### Step 1 — Orchestrate once, end to end

Paste this. Cowork runs all five roles on a fixed sample idea and writes a real file into the folder, so the room sees the multi-agent output as an artifact.

```
Act as the Orchestrator of a business idea evaluation panel.

The idea to evaluate: "A monthly subscription tiffin (home-cooked meal) service for hostel and PG students, with app-based menu selection and daily delivery."

Run it through four specialist roles, one at a time, each judging only its own dimension:
1. Market Analyst (demand, competition, timing, size)
2. Feasibility Checker (can a first-time founder build and run this)
3. Money Agent (revenue model, unit economics, path to first revenue)
4. Skeptic (the 2 to 3 most likely reasons this fails)

Then act as a Verdict role that synthesizes all four into scores (1 to 10) and a GO / REWORK / KILL call with one line of reasoning.

Save the result as evaluation.md in this folder, with one section per role and the verdict at the top.
```

### Step 2 — Convert into something reusable

Once Step 1 works, turn the working panel into a reusable form. Pick one.

**Option A — Skill (SKILL.md)**

```
Take the evaluation panel you just ran and turn it into a reusable Skill. Create SKILL.md in this folder with: a name, a description that says to trigger it whenever the user wants a business idea evaluated, and step-by-step instructions for running the four specialist roles plus the verdict. Written so any future idea can be dropped in, not just the tiffin one.
```

**Option B — Project memory (CLAUDE.md)**

```
Create a CLAUDE.md in this folder so that any time we work here, you behave as this business idea evaluation panel by default: the four specialist roles and the verdict format, ready to apply to whatever idea I paste.
```

---

## CLAUDE.md vs SKILL.md

Students build both in Step 2, so teach the difference where they can feel it.

| | CLAUDE.md | SKILL.md |
|---|---|---|
| What it is | Always-on project memory | On-demand capability |
| Loads | Every time, in this folder | Only when a task matches |
| Answers | Who you are here, how we work | How to do X well |
| Scope | One workspace | Portable across projects |
| Best for | Standing context and defaults | A procedure you invoke |

**Rule of thumb:** context that is always true here goes in CLAUDE.md. A skill you trigger on demand goes in SKILL.md.

---

## Test Prompts

Swap the tiffin idea for any of these to run the panel again live. Pick the category that fits the room.

### 🟢 Basic — clear, relatable ideas
```
A monthly subscription tiffin service for hostel and PG students, with app-based menu selection.
```
```
A doorstep bike-servicing business that comes to your office parking on a fixed weekly schedule.
```

### 🟡 Intermediate — needs real judgement
```
A paid community for first-time founders in tier-2 Indian cities, with weekly expert sessions and a job board.
```
```
A B2B tool that turns a company's WhatsApp support chats into a searchable FAQ and auto-reply bot.
```

### 🔴 Advanced — where the Skeptic earns its keep
```
An AI agent marketplace where small businesses rent pre-built automations on a monthly plan.
```
```
A local same-day grocery service for a single dense neighbourhood, competing on delivery under 15 minutes.
```

---

## Implementation Notes

### Why the Orchestrator does not judge

The Orchestrator is the engagement manager, not an analyst. If it starts forming opinions, it contaminates the specialists' independence and the panel collapses into one voice. The system prompt enforces "you coordinate, you do not judge" for exactly this reason. Narrate this in the session.

### Why each specialist stays in its lane

Each specialist judges one dimension and is told not to comment on the others. This is what makes the outputs correlatable at the Verdict stage. Overlapping opinions produce a mushy report; single-lane opinions produce a scoreable one.

### Why Cowork is staged, not one mega-prompt

Step 1 shows the panel running end to end as files that appear in the folder. Step 2 converts that working system into something reusable. Splitting it lets the room watch the architecture form before abstracting it, which is where the CLAUDE.md vs SKILL.md lesson lands.

### Deploying the n8n version

Once the panel runs on a manual trigger, make it always-on:

- Swap the manual trigger for a **Webhook** node so any form or app can POST an idea and receive a verdict.
- Add a **Schedule (cron)** trigger to evaluate a queue of ideas from a Google Sheet on a fixed interval.
- Add a **Slack or Telegram** node after the Verdict to push the report to a channel.

### Extending the panel

- Add a **fifth specialist** (for example a Go-To-Market agent) by cloning the specialist pattern and registering it as a new tool on the Orchestrator.
- Branch the test prompts **by industry** while keeping the core five-role structure reusable across verticals.
- Log every verdict to a **Google Sheet** to build a dataset of evaluated ideas over time.

---

*Data Science Masterminds · AI Agent Accelerator · Multi-Agent Module*
*Built for cohort use. Do not redistribute without permission.*
