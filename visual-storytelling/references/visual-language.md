# Visual Language Profile — Tori Rice's Portfolio

> **STATUS: CALIBRATED** (2026-06-11) — from editorial.css + expressive.css skin files and the live site's content layer.
> Gaps remaining from base Classic stylesheet: exact type scale (--fs-* values), spacing rhythm, base corner radii. Marked TO CONFIRM below; everything else is evidence-based.

## Architecture: build on variables, never hex

The portfolio runs a **multi-skin system** — Classic (base), Expressive, Editorial — each with light and dark themes, switched via `data-skin` / `data-theme` attributes. Therefore the cardinal technical rule:

**Every diagram must be built on the site's CSS custom properties** (`--accent-1..4`, `--surface-0..3`, `--text-primary/secondary/tertiary`, `--border-subtle/medium`, `--serif`), never hard-coded hex. A diagram done right re-themes itself across all six skin/theme combinations for free. A hard-coded one breaks the system's whole premise.

## Palette (Expressive/Editorial evidence)

- **Foundation**: deep plum/aubergine inks — `#190734` page, `#28104A` cards, `#241046` text ink; cream paper surfaces in light (`#F6F1E5` editorial, `#F7F4EE` expressive).
- **Signature accent**: periwinkle `#6D7CFF` (`--accent-1`) — in her words, "the brand focal color," used as "a FOCAL color, not a wash." In any diagram, periwinkle marks the protagonist. One protagonist per visual.
- **Supporting cast**: cornflower `#6495ED` (cool companion), coral `#FF7A6E`, peach `#FFC49B`, gold `#F2C94C`, sage `#A6C36F`, indigo `#5B4BBF` — "sparing editorial landmarks and emphasis, never backgrounds."
- **Semantic color language** (use it — it's load-bearing): the site assigns meaning-colors per case study: cornflower = trust/identity/systems, sage = discovery/search, coral = human-AI collaboration, periwinkle = reliability/systems, gold = creation. Diagrams about a given domain should inherit its meaning-color as the local accent.
- **Stated philosophy, verbatim from her CSS**: "Color is concentrated in a few editorial moments, never spread as glows." / "Color belongs in the work, not behind it." Diagrams obey the same law: structure in neutrals (text + border tokens), color only at the moments of meaning. No gradient washes, no ambient glows behind diagram content (she sets decorative gradients to opacity 0.05 on purpose).

## Typography

- **Body/sans**: DM Sans (system fallback stack).
- **Display/serif**: Fraunces, weight 500–600, tight letter-spacing (-0.015 to -0.025em), italics used for the conceptual turn — in headlines, the *emphasized* word is italic and periwinkle.
- **Labels/eyebrows**: uppercase, letter-spacing 0.2em, weight 600, accent-colored, often preceded by a small accent dot.
- Diagram mapping: node labels in DM Sans; a diagram's headline (if it has one) may take Fraunces in editorial contexts; edge labels smaller, `--text-secondary`. Magazine numerals (decimal-leading-zero `01 02 03`, big serif, low opacity) are an established motif for sequenced content — use for numbered flows.
- TO CONFIRM: exact `--fs-*` scale values from base stylesheet.

## Geometry & texture

- **Organic, not mechanical**: portrait frame uses asymmetric radii (`18px 24px 20px 26px`); pills are full-round (999px). Diagram nodes should lean softly rounded, allowed slight asymmetry for hero diagrams; never sharp-cornered boxes.
- **Hand-made accents exist in the system**: brush-stroke SVG underlines and painted textures (editorial skin). A hand-drawn-feel annotation (brush underline under the key insight) is ON-language for editorial moments — use sparingly, one per diagram max.
- **Shadows**: soft, large-radius, low-opacity, often tinted with the accent (`rgba(109,124,255,0.34)` glows on hover). Diagrams: flat or near-flat; reserve glow for the single interactive/highlighted element.
- TO CONFIRM: base border-radius and spacing tokens from Classic stylesheet.

## Editorial conventions (from the live content layer)

- Headlines are complete sentences with periods ("I don't just design AI. I build with it.") — callouts on diagrams follow suit: full declarative thoughts, not noun labels.
- Every project pairs with ONE sharp proof point ("12→1 logins unified," "2.9M users") — every diagram earns one stat or declarative payoff, placed on the visual.
- Pull-quote treatment: oversized serif quotation mark in accent at 50% opacity — available motif for quoted user/stakeholder voice inside a visual.
- Sanitization register: internal work is shown abstracted ("Internal · walkthrough on request") — diagrams of internal systems show topology and concepts, never recreated internal UI.

## Diagram conventions (stable)

- Flow direction: left→right processes, top→down hierarchies; one direction per visual.
- Structure drawn in `--border-medium` / `--text-secondary`; meaning marked in the local semantic accent; the protagonist in `--accent-1` (or the case study's meaning-color).
- Groupings: background tint (accent at 8–12% alpha, matching her icon-chip treatment) OR thin border — never both.
- Callouts: accent-colored, anchored to the exact element, written as the insight in sentence form.
- Dark/light: verify every diagram in both themes before delivering — the system demands it.
