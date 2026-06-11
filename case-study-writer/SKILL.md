---
name: case-study-writer
description: Draft a portfolio case study from raw project materials — build journals, project decks, scattered notes, screenshots, chat transcripts, or a designer's verbal rambling about a project. Use this skill whenever the user wants to write, draft, start, or restructure a case study, turn a build journal or project notes into portfolio content, or says "help me write up this project." Pairs with build-journal (input), voice (style), portfolio-edit-pass and portfolio-critique (downstream review).
---

# Case Study Writer

Draft portfolio case studies that read like a senior designer's judgment narrative, not a process recap. This skill is the generative counterpart to `portfolio-critique` — its structure deliberately mirrors that skill's rubric, so a draft from here should pass the critique's storytelling, role-clarity, and impact checks on the first run.

**Before writing anything**: if the `voice` skill exists, read its voice profile and write in it. If it doesn't, ask the user for 2-3 samples of their writing and match them.

## Inputs

Accept anything: build journals (especially `journal/` folders from the `build-journal` skill — start with the case-study seeds sections), decks, Figma links, screenshots, scattered notes, or a transcript of the user talking through the project. Messy input is expected; extracting the story from mess is the job.

If material is thin, interview before drafting. The five questions that matter most:
1. Why did this project matter — to the business and to the user? (Stakes)
2. What was the moment the obvious approach failed, or an assumption got overturned? (Tension — every good case study has one; find it)
3. What did *you personally* decide, design, and influence vs. the team? (Role)
4. What tradeoff did you consciously make, and what did you give up? (Judgment)
5. What happened after it shipped — numbers if they exist, signal if they don't? (Impact)

If the user can't answer #2, dig: "what surprised you?", "what took way longer than expected?", "what did you argue about?" The tension is always there; it's usually just not labeled as the story yet.

## Structure

Default skeleton — adapt freely, but every section's *job* must be done somewhere:

1. **Hook (2-4 sentences)**: the stakes and the outcome, up front. The reader should know why to care and what happened before any process appears. Never open with "The team was tasked with..."
2. **Context**: product, users, constraints — only what's needed to understand the decisions that follow. Ruthless about length.
3. **Role statement**: one unambiguous block: what the user owned, decided, and drove. First person singular. This is non-negotiable — "we" without "I" is the most common senior-portfolio killer.
4. **The work, told as decisions**: the body is a sequence of decision points, not a tour of artifacts. For each: the situation, the options considered, the choice, the why. The tension moment from question #2 anchors this section. Artifacts (screens, diagrams) appear as *evidence for decisions*, each with a caption that adds information beyond what's visible.
5. **What didn't work**: at least one genuine dead end or failure, treated with respect, plus the recovery. Credibility lives here.
6. **Outcome**: the sharpest honest impact claim available. Rank evidence: measured metric > directional metric > adoption/qualitative signal > shipped. Never inflate; "the team adopted it as the default pattern" beats a vague "improved engagement."
7. **Reflection (short)**: what the user would do differently, or what the project changed about how they work. 2-4 sentences; this is where seniority shows quietly.

## For AI-native / built-with-AI case studies

When the project was built with Claude or other AI tools, the human judgment is the story — the tool is the setting:
- Include 1-3 **verbatim prompts** at genuine decision points, each paired with why that prompt and what it produced. Prompts without commentary are trivia.
- The attempts log (tried → failed → adjusted) is the narrative spine. Frame failures as the user reading the tool's behavior and adapting — that's agentic UX thinking applied to their own workflow, and it should be named as such when the target role is AI tooling.
- Be precise about the human/AI boundary: what the tool generated, what the user directed, what the user overrode and why. Vagueness here reads as either inflation or naivety.

## Rules

- **Never fabricate.** No invented metrics, quotes, decisions, or detail the source material doesn't support. Mark gaps for the user: `[NEED: what the actual adoption number was]`. A draft with honest holes is a working document; one with plausible inventions is a liability in an interview.
- **Honor [SENSITIVE] flags** from build journals: sanitize or placeholder that content (`[SANITIZE: internal metric — abstract to "double-digit lift"?]`) and surface every instance to the user in the delivery note.
- **Write tight.** Target 800-1400 words of body copy for a full case study. If the draft runs long, the cut candidates are context and process, never tension and decisions.
- **Skimmable headers**: every section header should carry meaning alone — a skimmer reading only headers should get the arc. "The Process" is banned; "Why the first navigation model failed" is the energy.
- **Deliver as a file** (`{project}-case-study-draft.md`) with a short delivery note: the 2-3 weakest spots in the draft, any [NEED]/[SANITIZE] items, and a suggestion to run `portfolio-critique` once gaps are filled.
