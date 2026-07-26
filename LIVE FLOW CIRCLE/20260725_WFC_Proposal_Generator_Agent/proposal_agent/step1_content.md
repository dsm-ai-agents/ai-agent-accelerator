# Step 1 Agent — Content Distillation

## Goal
Read the four raw source documents and distill them into a slide-by-slide
content brief, saved as `content/content.md`. This step is about **content
only** — no slide design, no layout, no visuals. Just get the right facts on
the right slide, in clean prose/bullets/tables.

## Inputs (read all four)
- `input/01_Discovery_Meeting.txt` — client's current process, pain points, goals
- `input/02_Solution_Recommendation.txt` — recommended AI modules, phases, success metrics
- `input/03_Industry_Research.pdf` — supporting market/industry context and stats
- `input/04_Pricing_Rate_Card.csv` — line-item pricing (service, category, qty, unit price, line total)

## Structure to follow
Use `input/05_Proposal_Deck_Input_Guide.docx` as the blueprint. It defines
12 slides — follow its section headers and table shapes exactly. Do not add
or remove slides. Do not invent facts not present in the four inputs; if a
guide field has no source data, mark it `[TBD — confirm with client]` rather
than fabricating a number.

## Output
Write `content/content.md` with one `## Slide N — Title` section per slide
(1 through 12), matching the guide's structure:

1. Title — project title, client name, prepared by, date, one-line value prop
2. Executive Summary
3. Client Business Overview (+ metrics table)
4. Current Challenges (+ challenge/impact table)
5. Proposed AI Solution (module-by-module)
6. Solution Architecture (flow description)
7. Scope & Deliverables (table)
8. Implementation Roadmap (phase/duration table)
9. Investment (costs summarized from the pricing CSV — group into Software,
   Implementation, Training, Support, and Total)
10. Business Benefits & ROI (before/after table + estimated savings/ROI)
11. Risks & Assumptions
12. Next Steps

For each slide, write the exact bullets/table rows/short paragraphs that
should appear on the slide — this file is what Step 2 will render directly
into the deck, so keep it tight (slide-ready, not essay-length).

## Notes
- Client is ABC Electronics (online consumer electronics retailer).
- Pull hard numbers (300 tickets/day, 8 agents, 4–6 hr response time, etc.)
  directly from the discovery transcript and pricing CSV — don't round or
  approximate where an exact source number exists.
- Investment slide: sum the CSV line totals into the guide's four categories
  plus a Total Project Investment figure.
