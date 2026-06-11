---
name: prompt-retro
description: Analyze how the user has been prompting Claude — from build journals, session transcripts, or pasted prompts — and run a retrospective showing which prompts worked, which cost extra iterations, why, and how to prompt better next time, with rewritten examples of the user's actual prompts. Use this skill whenever the user asks how their prompting is going, wants prompting feedback or insights, says "how could I have prompted that better," wants to improve their AI workflow, or at the natural end of a build session as a closing retro. Maintains a cumulative personal prompting playbook across sessions.
---

# Prompt Retro

A retrospective on how the user prompts, grounded entirely in their **actual prompts and what actually happened next** — never a generic prompt-engineering lecture. The output compounds: every retro updates a personal playbook (`references/prompting-playbook.md`) so lessons accumulate instead of evaporating.

## Inputs

In priority order:
1. **Build journals** (`journal/` from the `build-journal` skill) — PROMPT entries plus the attempt/fail/adjustment trail around them are pre-paired prompt→outcome data.
2. **The current or a pasted session transcript.**
3. **Prompts the user pastes directly** — ask what happened after each one; a prompt without its outcome can't be evaluated.

## Method

### 1. Pair every prompt with its outcome
For each significant prompt, record what happened next, scored by **cost to acceptable result**:
- 🟢 **Landed** — result acceptable first try or with trivial touch-up
- 🟡 **Iterated** — got there, but took N follow-up corrections (record N and what each correction had to add)
- 🔴 **Sideswiped** — output went somewhere unintended; required restart or major redirect

The follow-up corrections are the diagnostic gold: **whatever the user had to say in turn 2 is usually what was missing from turn 1.** "No, keep the existing layout" in turn 2 means turn 1 needed a constraint. "More like the second one" means turn 1 needed an example.

### 2. Find patterns, not incidents
Look across the pairs for recurring causes. Common pattern families to check (extend freely):
- **Missing constraints** — what to preserve, what not to touch, scope boundaries
- **Underspecified taste** — "make it better/cleaner" without a reference, example, or named quality
- **Overloaded asks** — three changes in one prompt, where the model satisficed on two
- **Missing context the user had in their head** — assumed knowledge of the project the model didn't have
- **Over-specification** — prescribing implementation when describing the outcome would've let the model find a better path (this pattern matters: senior users often over-steer)
- **Iterating vs. restarting** — long correction chains on a poisoned direction where a fresh, fuller prompt would have been cheaper
- **What the 🟢 prompts share** — the user's existing strengths, stated as explicitly as the weaknesses

### 3. Rewrite real examples
For each major pattern, take one of the user's **actual** prompts and show:
- Original (verbatim) → what it cost (the actual follow-ups it required)
- Rewritten version → why this version would likely have landed, mapped to the specific corrections it pre-empts
Rewrites stay in the user's voice and style — terse if they're terse. The point is a better version of *their* prompt, not a template.

### 4. Update the playbook
Append to / revise `references/prompting-playbook.md`:
- **Keep doing** — strengths with an example each
- **Watch for** — the user's personal recurring patterns, each with the tell ("if your prompt contains 'better' with no reference, stop")
- **Personal heuristics** — accumulated rules in the user's own terms, dated, with the session that taught them
The playbook is the product. Keep it under a page — when it grows past that, merge and prune; a playbook nobody re-reads is dead weight.

## Output

A short retro document (`prompt-retro-YYYY-MM-DD.md`):
1. **Scoreboard** — counts of 🟢/🟡/🔴 and total correction turns spent (the honest cost metric)
2. **Top 2-3 patterns** this session, each with the real example → rewrite
3. **One strength to lean on harder**
4. **Playbook diff** — what got added or changed
Keep it tight enough to read in two minutes. One insight applied beats ten admired.

## Rules
- **Every claim cites a real prompt from the material.** No invented examples, no generic tips that could appear in a listicle.
- **Score by cost, not elegance.** A scrappy prompt that landed first try is a good prompt. Do not recommend ceremony (roles, elaborate structure) unless the evidence shows its absence caused failures.
- **Respect intent over compliance**: if the model technically did what was asked but the user was unsatisfied, that's still a prompt-outcome gap worth diagnosing — what did the prompt fail to carry about what they actually wanted?
- **No blame inversion.** Sometimes the tool just failed; pattern-matching every failure to a user mistake teaches superstition. Mark genuine tool misses as such.
