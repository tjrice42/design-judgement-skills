---
name: build-journal
description: Automatically maintain a build journal during any prototyping, design, or development session — capturing attempts, failures, pivots, verbatim prompts, decisions, and visual state changes as they happen, so the work documents itself into future case-study material. Use this skill at the start of EVERY session where the user is building a prototype, portfolio piece, app, or design artifact, even if they don't mention journaling — and especially if they say "start a journal," "document this build," "track what we try," or reference their build journal. Also use it to retroactively convert an existing manual journal or chat transcript into the structured format.
---

# Build Journal

Maintain a running journal of the build *as it happens*, so the raw material for a case study exists the moment the project ships. The user's judgment — what was tried, what failed, what changed and why — is the most valuable and most perishable information in any build. Capture it in the moment; it cannot be reconstructed later.

**This is a standing behavior for the entire session, not a one-time step.** Once this skill is active, keep journaling until the session ends.

## Setup (once per project)

Create `journal/` in the project root with one file per session: `journal/YYYY-MM-DD-session-NN.md`. If a journal already exists, read the most recent entry first and open the new session with a one-line "where we left off."

## What triggers an entry

Append an entry whenever any of these happens — without asking permission and without announcing it beyond a brief marker:

1. **Attempt** — a new approach is tried on a problem (a prompt strategy, a library, a layout direction).
2. **Failure or surprise** — something didn't work, worked differently than expected, or the tool went sideways. **These are the highest-value entries.** Capture what the failure looked like, the hypothesis for why, and what was tried next.
3. **Pivot** — abandoning an approach. Record what was abandoned and the reasoning, even if it feels obvious in the moment.
4. **Decision point** — choosing between viable options. Record the options considered, the choice, and the why. One sentence of rationale now saves an hour of reconstruction later.
5. **Prompt worth keeping** — when a user prompt (or a prompt strategy) materially shaped the outcome, record it **verbatim**, not summarized. The difference between "asked it to fix the layout" and the actual words is the difference between a claim and evidence.
6. **Visual state change** — the prototype reaches a new visible state (first render, major layout shift, feature working end-to-end). Prompt the user once, briefly: "Good screenshot moment — grab one for the journal?" Never block on the answer.
7. **Milestone** — something works end-to-end, ships, or gets handed off.

## Entry format

Terse. Telegraphic. This is a field log, not prose — the case-study writer turns it into prose later.

```
### [HH:MM] ATTEMPT|FAIL|PIVOT|DECISION|PROMPT|VISUAL|MILESTONE — short title
- Tried: ...
- Result: ...
- Adjustment / why: ...
- Verbatim prompt (if PROMPT): "..."
- [SENSITIVE] flag if entry references employer-internal systems, names, or data
```

Rules for entries:
- **Never interrupt flow.** Journaling is Claude's job, not the user's. Write entries silently during natural pauses (after a tool result, while a build runs). The only user-facing interruption permitted is the single screenshot nudge on VISUAL entries.
- **Capture the user's actual words** when they articulate reasoning, frustration, or insight in chat — quote them. Their voice in the moment is case-study gold.
- **Record dead ends with the same care as wins.** A case study's credibility lives in its failures.
- **Mark confidentiality in the moment.** Tag `[SENSITIVE]` on anything referencing employer-internal material so the sanitization decision is pre-flagged, not rediscovered during portfolio assembly.

## End of session

When the session winds down (user says they're done, or activity clearly ends), close the journal file with:

1. **Session summary** — 3-5 sentences: what got built, the defining struggle, the key decision.
2. **Case-study seeds** — 1-3 moments from this session with narrative potential, each tagged with why ("good tension: obvious approach failed twice before the rethink"). These are the hooks a future case study hangs on.
3. **Open threads** — what's unresolved, so the next session's journal can pick up cleanly.

## Retroactive mode

When given an existing manual journal, chat transcript, or notes from a past build: convert it into this format as faithfully as possible, preserving the user's original wording wherever it exists. Mark gaps explicitly (`[NOT CAPTURED: exact prompt]`) rather than inventing detail — a journal with honest holes is usable; one with fabricated specifics is poison for a portfolio. Finish with the same case-study seeds section, identifying the strongest narrative moments in the historical material.

## Why this matters (context for judgment calls)

The journal's downstream consumer is a portfolio case study read by hiring panels. When deciding whether something is worth an entry, the test is: *would this help tell the story of how a designer navigated a real build with judgment?* Tool struggles, taste calls, scope cuts, and recoveries all pass that test. Routine progress ("installed dependencies") does not.
