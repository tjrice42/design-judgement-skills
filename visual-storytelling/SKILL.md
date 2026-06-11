---
name: visual-storytelling
description: Create genuine diagrams, flows, and informative visuals that tell a story in the user's visual language — instead of flattening content into card grids or converting diagrams into text summaries. Use this skill whenever building portfolio pages, case-study visuals, or prototypes that present process, systems, comparisons, timelines, or data; whenever the user shares a diagram, sketch, or whiteboard photo to be recreated on their site; and whenever you notice yourself about to render information as a grid of icon-title-description cards. Pairs with voice (prose) — this is voice for visuals.
---

# Visual Storytelling

Make visuals that carry the story, in the user's visual language. This skill exists to defeat two default failure modes:

1. **Card-ification** — flattening information that has inherent shape (a flow, a system, a hierarchy, a comparison) into a grid of icon + title + blurb cards. Cards destroy structure: a 5-step process rendered as 5 cards has lost its arrows, its branching, its causality — the actual information.
2. **Diagram-to-prose collapse** — being shown a diagram (screenshot, sketch, whiteboard photo) and producing a *text summary styled nicely* instead of recreating the diagram itself. The user asked for the diagram in their look and feel; the spatial structure IS the content.

## Rule zero: find the content's shape first

Before rendering anything, classify what the information actually *is*. The form follows from the shape — never from habit:

| Content shape | Right form | Never |
|---|---|---|
| Sequence / process | Horizontal or vertical flow with real connectors, decision branches drawn as branches | Numbered cards in a row |
| System / architecture | Spatial diagram: containment shown by nesting, relationships by lines, layers by position | "Components" card grid |
| Comparison (2-3 things) | True side-by-side with aligned rows so differences sit on the same eye-line | Two stacked cards |
| Before / after | Paired states, same framing, same scale, differences annotated on the visual | Prose describing what changed |
| Change over time | Timeline with proportional spacing, or small multiples | Milestone cards |
| Quantity / measurement | Chart honestly scaled, one message per chart | Big-number stat cards (acceptable ONLY for genuinely independent single figures) |
| Tradeoff / tension | 2x2, spectrum, or balance visual | Pros/cons bullet columns |
| Collection of true peers | Cards — this is the ONE shape cards are for | — |

If reaching for a card grid, stop and ask: *is this really a collection of peers with no structure between them?* Almost always the answer is no, and the structure being discarded is the story.

## Diagram translation mode

When given a source diagram (screenshot, sketch, whiteboard photo, old-tool export):

1. **Extract the topology first, separately from style**: nodes, edges and their direction, groupings/containment, layers, ordering, annotations. Write this out as a structure inventory before drawing anything.
2. **Re-render the topology in the user's visual language** (see profile below): their type, colors, spacing, stroke weights, corner treatment. Every node, every edge, every grouping from the inventory must appear. Style is fully translated; structure is fully preserved.
3. **Improve only with permission of the structure**: tidying alignment, evening spacing, clarifying a crossing — yes. Dropping edges, merging nodes, reordering flow "for layout reasons" — no. If the source diagram has a real flaw worth fixing, flag it to the user as a proposal, don't silently fix it.
4. Deliver as **inline SVG** (themeable, crisp, selectable text) inside the page, not a raster export, unless the user asks otherwise.

## Storytelling principles

- **One idea per visual.** If a diagram needs a paragraph to explain its point, it has too many points. Split it.
- **The insight goes ON the visual.** Annotate directly — a callout at the moment the flow breaks, a highlight on the changed region — instead of a paragraph beside a neutral diagram. The reader's eye should land on the point without instructions.
- **Visual hierarchy = narrative order.** The first thing the eye hits should be the first beat of the story. Use weight, color, and position deliberately to sequence attention; everything else recedes (this is where a muted palette earns its keep — one accent color means one protagonist).
- **Honest emphasis.** Highlighting the point is storytelling; distorting scale, cherry-picking the frame, or decorating weak data is lying with pictures. Don't.
- **Progressive complexity.** If the full system view is dense, lead with the simple version and reveal detail in a second, zoomed visual — two clean diagrams beat one heroic one.

## Craft constraints

- Read the project's existing tokens (CSS variables, type scale, palette) and use them — no out-of-the-box library aesthetics, no default-blue flowchart energy.
- Consistent geometry: one stroke width family, one corner radius, one arrowhead style, a real alignment grid. Inconsistency reads as carelessness even when nobody can name it.
- Every line and shape must mean something. No decorative icons, no gradient garnish, no abstract blobs. If an element can be deleted without losing information, delete it.
- Label edges, not just nodes — an unlabeled arrow makes the reader guess the relationship, and the relationship is usually the point.
- Text in diagrams: real, specific labels ("retry with backoff"), never lorem-flavored placeholders ("Step 2").
- Accessibility floor: text contrast holds on the actual background; information never carried by color alone; SVG gets a title/desc.

## Visual language profile

Read `references/visual-language.md` before producing any visual. If it's marked `PROVISIONAL`, calibrate when possible: given access to the user's live portfolio or its code, extract the actual tokens — type stack and scale, palette with usage roles, spacing rhythm, corner/stroke conventions, how existing visuals (if any) are treated — and rewrite the profile from evidence. Then confirm with the user against one sample diagram rendered in the extracted language.

## Anti-pattern checklist (final pass before delivering)

- [ ] No card grid standing where structure used to be
- [ ] No diagram that arrived as a diagram leaving as paragraphs
- [ ] No icon-title-blurb triptychs
- [ ] No flow rendered as a bullet list
- [ ] No unlabeled arrows, no orphan legends, no decoration-only elements
- [ ] Rendered in the user's tokens, not a library's defaults
- [ ] The point is findable in 3 seconds without reading body text
