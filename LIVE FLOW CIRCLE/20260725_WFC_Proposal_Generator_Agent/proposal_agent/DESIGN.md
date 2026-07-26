# DESIGN.md — Proposal Deck Design System

This is the single source of truth for the visual style of every deck this
project produces. Step 2 (`step2_proposal.md`) must read this file and apply
it exactly, so decks stay consistent run over run regardless of client or
content. Based on the `mckinsey-style` skill, adapted for PowerPoint.

## Canvas
- Widescreen: `LAYOUT_WIDE` — 13.33" x 7.5"
- Margins: 0.6" left/right, 0.35"–0.5" top, 0.4" bottom (footer zone)

## Color Palette

| Role | Hex | Usage |
|---|---|---|
| Primary Red | `9E1B32` | Section kickers, header accents, table headers, primary CTAs, key highlight cards |
| Secondary Red | `C0394B` | Title-slide kicker text, secondary accents on dark slides |
| Tint Red | `F5E6E8` | Zebra-striped table rows, light highlight/risk cards |
| Neutral Dark | `1A1A1A` | Body text, dark-slide backgrounds (title/closing) |
| Neutral Gray | `6B6B6B` | Secondary text, captions, footer text, labels |
| Border/Divider Gray | `E0E0E0` | Card borders, table borders, dividers |
| Background | `FFFFFF` | All content-slide backgrounds |
| Dark Card | `262626` | Cards/boxes on dark slides (title, next steps) |
| Dark Card Border | `3A3A3A` | Borders for cards on dark slides |
| Positive | `2E7D32` | Positive deltas only (rare) |
| Negative | `B00020` | Negative deltas only (rare) |

Never introduce other hues (blue, green, orange, purple) into charts or
accents — red + neutrals only.

## Typography
- Headings: **Cambria** (serif) — bold, 28–44pt
- Body / labels / tables / data: **Calibri** (sans) — 10.5–15pt
- Section kicker (small caps-style label above title): Calibri, 12pt, bold, `charSpacing: 1`, color Primary Red (or Secondary Red on dark slides)
- Slide title: Cambria, 28pt bold, Neutral Dark (or white on dark slides)
- Title-slide headline: Cambria, 44pt bold, white
- Body text: Calibri, 12.5–13.5pt, `lineSpacingMultiple: 1.25–1.3`
- KPI big number: Calibri, 26pt bold, Neutral Dark
- KPI label: Calibri, 11pt, Neutral Gray
- Table header: Calibri, 12pt bold, white on Primary Red fill
- Table body: Calibri, 12pt, Neutral Dark
- Footer: Calibri, 9pt, Neutral Gray

## Layout Pattern (per content slide)
1. **Section kicker** at x=0.6, y=0.35 — small bold red uppercase label naming the slide topic.
2. **Slide title** at x=0.6, y=0.62 — serif, bold, states the takeaway (not just the section name).
3. **Body content** starts around y=1.75–2.0.
4. **Footer** at y=PH-0.4 — left: `"{Client} | {Project} | Confidential"`, right: page number.

## Slide Type Templates
- **Title slide (dark)**: full dark background, thin red rule (0.04" bar) near bottom third, kicker + huge serif headline + italic subhead, three-column prepared-by/date/client block below the rule.
- **Closing / Next Steps slide (dark)**: same dark background, numbered step cards in a row (`262626` fill, `3A3A3A` border, red numeral), contact card below.
- **Content slides (white)**: kicker + title, then one of:
  - **KPI card row** — white fill, `E0E0E0` border, 0.06" red top accent bar, big number + label. Use for executive summary / ROI callouts.
  - **Styled table** — red header row, white/tint-red zebra striping, `E0E0E0` borders. Use for any Metric/Value, Before/After, or line-item data straight from the guide.
  - **Process/flow row** — equal-width boxes connected by gray right-arrows, one box (the "hero" step) filled solid red. Use for architecture flow and roadmap phases.
  - **Numbered module cards (grid)** — 3-column grid, white cards with 0.06" left red accent bar, large serif numeral, bold title, gray description. Use for solution/module breakdowns.
  - **Two-column risk/assumption cards** — left column tint-red cards (risks), right column white bordered cards (assumptions).

## Component Specs
- **Card border radius**: none — flat rectangles only, no rounded corners, no drop shadows.
- **Accent bars**: only as a left-edge or top-edge 0.06"–0.08" solid bar on cards — never a full-width banner, never a stripe under the title (no title underlines).
- **Arrows** (flow diagrams): `rightArrow` shape, gray fill, ~0.18" tall, no outline.
- **Table row height**: 0.42"–0.75" depending on content density.

## What to Avoid
- No accent line/underline beneath titles
- No color bars or edge stripes purely for decoration
- No rounded corners or heavy shadows
- No rainbow chart palettes — red + gray only
- No cream/beige backgrounds — pure white or the dark (`1A1A1A`) bookend only
- No centered body text — left-align everything except title-slide headline block

## Reuse Instructions for Step 2
When generating a new deck:
1. Load this file before writing the pptxgenjs script.
2. Reuse the color constants, font names, `sectionHeader()`, `footer()`, `kpiCard()`, and `tableStyled()` patterns described above so every deck this project produces looks like the same template family, just with new content.
3. If a new slide type is needed that isn't covered here, design it within this palette/typography system and add its pattern back into this file so it's captured for next time.
