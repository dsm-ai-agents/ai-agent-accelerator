# AI Proposal Agent — Orchestrator

This project turns raw discovery/pricing/research documents into a McKinsey-style
consulting proposal deck, in two sequential agent steps.

## Pipeline

```
input/00-05  ──▶  STEP 1 (step1_content.md)  ──▶  content/content.md  ──▶  STEP 2 (step2_proposal.md)  ──▶  output/*.pptx
```

## Folders

- `input/` — source documents (read-only)
  - `00_Workshop_Exercise_Brief.docx` — exercise context, not used as content input
  - `01_Discovery_Meeting.txt` — client discovery transcript (ABC Electronics)
  - `02_Solution_Recommendation.txt` — recommended AI solution & phases
  - `03_Industry_Research.pdf` — supporting market/industry research
  - `04_Pricing_Rate_Card.csv` — line-item pricing
  - `05_Proposal_Deck_Input_Guide.docx` — the blueprint: defines all 12 slides and what goes on each
- `content/` — Step 1 output lands here as `content.md`
- `output/` — Step 2 output lands here as the final `.pptx`

## Design System

`DESIGN.md` (project root) defines the deck's visual identity — palette,
typography, slide templates and component specs, distilled from the
`mckinsey-style` skill. Step 2 reads this file before building any deck, so
every proposal this project produces stays visually consistent regardless
of client or content.

## Steps

1. **step1_content.md** — Content Distillation Agent
   Reads inputs 01, 02, 03, 04 and uses the structure defined in 05 as the target
   slide-by-slide outline. Produces `content/content.md`: a clean, slide-organized
   markdown brief with no design/formatting — just the right content per slide.

2. **step2_proposal.md** — Deck Builder Agent
   Reads `content/content.md` and generates the final proposal deck as a
   `.pptx` file in `output/`, applying a McKinsey/BCG-style corporate design
   (via the `mckinsey-style` skill) — muted red/white palette, serif headings,
   flat KPI cards, print-ready consulting look.

## Execution order

Run Step 1 first and confirm `content/content.md` looks right before running
Step 2 — Step 2 depends entirely on Step 1's output, not on the raw inputs.
