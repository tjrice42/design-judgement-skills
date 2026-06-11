---
name: portfolio-edit-pass
description: A screen-by-screen editorial pass over a design portfolio, case study, or portfolio prototype that flags unneeded screens and sections, recommends cuts and merges, and proposes specific visual, layout, and copy improvements. Use this skill whenever the user wants to trim, tighten, curate, declutter, or improve their portfolio before review — or asks "what should I cut," "is this screen needed," "how can this look better," or wants an edit pass before running a critique. Run this BEFORE portfolio-critique when both are in play.
---

# Portfolio Edit Pass

A screen-by-screen editorial pass that turns a complete-but-bloated portfolio into a tight, intentional one. This skill is an **editor, not a critic**: it does not grade the portfolio, simulate hiring managers, or render a ship verdict (that's `portfolio-critique`, which runs after edits are applied). Its only job is concrete, per-screen change proposals: cut this, merge these, replace that image, rewrite this line.

Editorial stance: **a portfolio is a curated argument, not an archive.** Every screen must earn its scroll. When in doubt, recommend the cut — the user can always veto, but they can't see the bloat from inside it.

## Inputs

A live URL (traverse every page and section in order, top to bottom), prototype code, screenshots, or written case studies. Before starting, confirm the target role if not already known — relevance judgments depend on it.

## Workflow

### Step 1 — Inventory every screen and section
Walk the portfolio in reading order and build a numbered inventory: every page, and within each page, every distinct section/screen/artifact (hero, bio, each case-study block, each image, each diagram). This numbering is the spine of the whole edit plan — every recommendation references it.

### Step 2 — Assign each item a verdict
One of five, each with a one-sentence reason:

- **KEEP** — earns its place as-is. Say what job it's doing.
- **CUT** — doesn't advance the argument for hiring this person for this role. Common cut candidates: redundant final-screen galleries, process artifacts that repeat what prose already said, projects irrelevant to the target, decorative diagrams, anything the user included because portfolios "should" have it.
- **MERGE** — two or more items doing the same job; specify which survives and what gets absorbed.
- **REWORK** — right content, wrong execution. Must be paired with a Step 3 proposal.
- **MOVE** — right content, wrong position. Specify exactly where it goes and why the new order reads better.

The test for every item: *if a reviewer skipped this, would the argument weaken?* If no → CUT.

### Step 3 — Concrete improvement proposals (for KEEP and REWORK items)
For each surviving item, propose specific upgrades where warranted. Categories to check:

**Visual & layout**
- Hierarchy: is the most important element actually the most prominent? Flag walls of same-weight text and competing focal points.
- Image quality: blurry exports, tiny unreadable UI screenshots, inconsistent device frames, mismatched corner radii/shadows across mockups. Propose the fix (re-export at 2x, crop to the relevant region, consistent frame treatment).
- Screenshot framing: full-app screenshots where a cropped detail would communicate more. Specify the crop.
- Density and breathing room: sections where spacing is doing none of the storytelling work.
- Consistency: type scale, color usage, caption styles drifting across pages — list each drift specifically.
- Redundant visuals: three screenshots showing the same state from slightly different angles → pick the one that works hardest.

**Copy**
- Tighten: quote the actual sentence, provide the rewritten version. Never say "make this more concise" without doing it.
- Captions: every image needs a caption that adds information beyond what's visible. Flag missing or decorative captions and draft replacements.
- Headers: do section headers carry meaning when skimmed alone? Propose rewrites for generic ones ("The Process" → something that states the actual insight).

**Structure**
- Reading order within each case study: does the sequence build, or jump around? Propose the reorder.
- Above-the-fold check per page: what a visitor sees before scrolling — is it the strongest available material?

### Step 4 — Deliver the edit plan
Write `{portfolio-name}-edit-plan.md`:

1. **Summary**: counts (X keep / X cut / X merge / X rework / X move), estimated total reduction (e.g., "this removes ~30% of scroll length and loses nothing"), and the three highest-leverage edits.
2. **The plan**: the numbered inventory with verdicts, reasons, and proposals — in portfolio reading order so the user can walk through with the site open and execute top to bottom.
3. **Effort sizing** on every proposal: 5-min / 30-min / needs-new-asset.
4. **Quick-win list**: everything sized 5-min, gathered at the end, so a single short session yields visible improvement.

## Rules

- **Be specific or be silent.** Every proposal names the exact item (by inventory number), quotes the exact copy, or describes the exact image. Generic advice ("improve visual hierarchy") is banned.
- **Do the rewrite.** Copy suggestions include the replacement text, in the user's existing voice.
- **Bias to cut.** Reviewers reward tightness; the user's attachment to their own work is the headwind this skill exists to counter. If genuinely torn, mark it CUT (soft) and let the user veto.
- **No grading, no verdicts.** Do not assess whether the portfolio is good, ready, or competitive — that's the critique skill's job and doing it here softens the edits.
- **Respect the voice.** Proposals upgrade execution; they don't replace the user's style with a generic one.
