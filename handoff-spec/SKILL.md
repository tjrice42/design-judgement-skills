---
name: handoff-spec
description: Generate a complete dev-handoff spec with an exhaustive edge-case and state matrix for any prototype, design, or feature. Use this skill whenever the user finishes or shares a prototype, mentions handing off to dev/engineering, asks about edge cases, states, error states, empty states, loading states, "what am I missing", design QA, or wants a spec written. Also trigger proactively at the end of any prototype-building session — a prototype is not done until its spec exists. Even if the user only says "wrap this up" or "get this ready for the team," use this skill.
---

# Handoff Spec Generator

Turn a prototype (code, Figma description, or written feature concept) into a complete handoff spec: a state-by-state edge-case matrix plus design decisions for every state the prototype doesn't show. Prototypes show the happy path; this skill documents everything else so engineering never has to guess and design debt gets caught before it ships.

## Workflow

### Step 1 — Inventory the surfaces
Read the prototype (code files, screenshots, or the user's description) and list every **surface**: each screen, panel, modal, list, form, card, or component that either renders data or accepts input. Note for each:
- What data it displays and where that data comes from
- What actions it offers
- Relevant code locations (file + line) if working from code

Don't skip secondary surfaces: toasts, tooltips, dropdowns, confirmation dialogs.

### Step 2 — Run the state taxonomy against every surface
For each surface, walk the full taxonomy below. For each state, classify it as one of:

- **Designed** — the prototype shows it. Note where.
- **Undesigned** — the state can occur but the prototype doesn't handle it. These are the spec's payload.
- **N/A** — genuinely cannot occur. Always include a one-line justification ("list is system-generated, can never be empty"). Be honest: "unlikely" is not N/A.

### Step 3 — Propose defaults for every undesigned state
An undesigned state without a recommendation just moves the guessing from dev to a Slack thread later. For each undesigned state, write a concrete proposed behavior (copy, layout, interaction) that the designer can approve or override. Match the prototype's existing patterns and voice. If two reasonable options exist, state both and recommend one.

### Step 4 — Assemble the spec
Use the structure in `assets/template.md`. The spec has:
1. **Summary matrix** — surfaces × state categories, each cell marked ✅ Designed / ⚠️ Undesigned / ➖ N/A. This is the one-glance view.
2. **Undesigned states detail** — one entry per ⚠️, with severity, proposed default, and open questions. Sort by severity.
3. **Questions for design** — only items genuinely requiring a design decision (tradeoffs, brand voice, product policy). Keep this list short; everything answerable by convention goes in proposed defaults instead.
4. **Out of scope / N/A log** — the justifications, so reviewers can challenge them.

Severity tags:
- **Blocker** — user hits a dead end, loses data, or sees broken UI (unhandled error, data loss on conflict)
- **Should fix** — degraded but survivable (awkward truncation, missing loading state on slow networks)
- **Polish** — noticeable to careful users only

### Step 5 — Save and deliver
Write the spec as a markdown file named `{feature-name}-handoff-spec.md` alongside the prototype (or to outputs if no repo). Offer a one-paragraph summary of the highest-severity findings in chat.

## The State Taxonomy

Walk ALL of these for every surface. Categories overlap on purpose — redundancy catches gaps.

### Data volume states
- **Empty — first use**: user has never created anything. (Onboarding opportunity, not just "No items.")
- **Empty — cleared**: user had data and deleted it all. Different emotional context than first use.
- **Empty — filtered to zero**: data exists but the current filter/search matches nothing. Must offer a way out ("Clear filters").
- **Single item**: do layouts built for grids/lists hold up with one item? Pluralization ("1 items")?
- **Typical**: the happy path (usually the only designed state).
- **Maximum / overflow**: 10,000 rows, 50 tags, 200-person picker. Pagination? Virtualization? "Show more"? What's the actual cap and what happens at it?
- **Partial / degraded**: some data loaded, some failed. Render what arrived or fail the whole view?

### Loading states
- **Initial load**: skeleton, spinner, or blank? What's the layout-shift story?
- **Refresh / refetch**: does existing content stay visible (stale-while-revalidate) or flash away?
- **Pagination / infinite scroll load**: indicator placement, scroll position preservation.
- **Optimistic updates**: does the UI commit before the server confirms? What happens on rejection?
- **Slow network**: what does the user see at 3 seconds? At 10? Is there a timeout, and what does it say?
- **Action in flight**: are buttons disabled during submit? Double-click/double-submit protection?

### Error states
- **Field validation**: when does it fire (blur, submit, keystroke)? Where does the message render? Can the user tell which field?
- **Form-level / submit failure**: is user input preserved? (Losing a long form to an error is a Blocker, always.)
- **Network failure**: offline or flaky connection. Retry affordance? Queued action?
- **Server error (5xx)**: what's the copy? Generic "Something went wrong" needs a recovery path.
- **Partial failure**: bulk action where 3 of 10 items failed. How is that communicated per-item?
- **Destructive-action failure**: delete fails — does the item reappear? Is the user told?
- **Stale-permission failure**: action was visible but the user's rights changed mid-session.

### Permission & entitlement states (critical for enterprise)
- **Read-only user**: which controls hide vs. disable? Disabled controls need tooltips explaining why.
- **No access**: route-level — redirect, 404, or request-access screen?
- **Feature flag off / not in plan tier**: hidden, or visible-but-gated upsell?
- **Admin vs. end-user views**: which surfaces diverge?
- **Revoked mid-session**: user is on the page when access is removed.

### Content stress states
- **Truncation**: long titles, names, emails. Where's the ellipsis — middle (preserves file extensions) or end? Tooltip on hover?
- **No-whitespace strings**: `aaaaaaaaaaaaaaaa@example.com` and unbroken URLs break layouts that long sentences don't.
- **Localization expansion**: German runs ~35% longer; do buttons and tabs survive? Any text baked into images?
- **RTL and emoji**: does the layout mirror? Do emoji in user content break truncation math?
- **Number extremes**: 0, negative, 7-figure values, long decimals. Currency and thousands separators by locale.
- **Missing media**: no avatar, broken image, missing thumbnail. Fallback initials? Placeholder?
- **Date/time edge cases**: timezones, "just now" vs. absolute, year boundaries, relative dates older than a year.

### Temporal & concurrency states
- **Stale data**: tab open for 2 days — does anything refresh? Is staleness even detectable?
- **Concurrent edit conflict**: two people edit the same record. Last-write-wins (silent data loss!) or conflict UI?
- **Deleted-from-under-you**: viewing an item someone else deletes.
- **Session expiry mid-task**: especially mid-form. Is work preserved through re-auth?

### Input & interaction states
- **Paste and autofill**: do masked/formatted inputs handle pasted values? Browser autofill styling?
- **Keyboard-only**: full task completable without a mouse? Visible focus states? Logical tab order? Modal focus traps?
- **Screen reader**: are loading/error state changes announced (aria-live)? Do icon-only buttons have labels?
- **Undo / interruption**: can destructive or bulk actions be undone? Toast-with-undo vs. confirm dialog?

## Rules

- **Never invent designed states.** If the prototype doesn't show it, it's Undesigned even if it's "obvious."
- **Cite evidence.** When working from code, reference file and line for both designed states and gaps.
- **N/A requires a reason.** No silent N/As.
- **Proposed defaults must be concrete** — actual copy strings, actual layout behavior, not "show an appropriate message."
- **Don't pad.** A tight spec devs actually read beats an exhaustive one they skim. The matrix is exhaustive; the detail section covers only ⚠️ states.
- **Match the product's voice** in proposed copy. Pull tone from existing strings in the prototype.
