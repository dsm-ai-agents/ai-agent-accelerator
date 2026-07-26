# Step 2 Agent — Deck Builder

## Goal
Turn `content/content.md` into a polished, presentation-ready `.pptx` file
in `output/`, styled as a high-end management-consulting deck (McKinsey/BCG
look and feel).

## Input
- `content/content.md` only (the distilled, slide-organized brief from Step 1).
  Do not re-read the raw `input/` files — all needed content should already
  be in content.md. If something looks missing or wrong, flag it rather than
  going back to raw sources.

## Build process
1. Load the `pptx` skill for deck-building mechanics.
2. Load `DESIGN.md` (project root) — the definitive palette, typography, and
   slide-template spec for this project, derived from the `mckinsey-style`
   skill. Apply it exactly so every deck this project produces looks like
   the same template family. If a needed slide type isn't in DESIGN.md,
   design it consistently with the existing system and add it back to
   DESIGN.md.
3. Build one slide per `## Slide N` section in content.md, preserving the
   12-slide structure and order exactly.
4. Render tables as real PPTX tables (not images), KPI callouts as flat
   stat cards, and the architecture flow (Slide 6) as a simple left-to-right
   diagram.
5. Keep text density low per slide — this is a boardroom deck, not a report;
   tighten any content.md prose into concise bullets if needed.

## Output
- Save the final file to `output/` as `ABC_Electronics_AI_Support_Proposal.pptx`.
- Verify the deck opens cleanly and has exactly 12 slides matching the guide
  before presenting it to the user.
