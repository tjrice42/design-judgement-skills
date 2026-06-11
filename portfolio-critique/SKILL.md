---
name: portfolio-critique
description: Run a structured, multi-lens critique of a design portfolio, case study, or portfolio prototype — evaluating storytelling, content choices, confidentiality risk, hiring-manager appeal, design depth, impact evidence, target-company fit, and application readiness. Use this skill whenever the user shares portfolio work and asks for feedback, critique, review, audit, or "is this good enough" / "am I ready to apply" — or mentions hiring managers, recruiters, case studies, or tailoring work for a specific company. Also trigger when reviewing a portfolio site's code or a landing page meant to showcase design work.
---

# Portfolio Critique

A structured critique of design portfolio work through the lenses that actually decide hiring outcomes. The goal is not a list of nitpicks — it's an honest read on what lands, what's missing, what's risky, and whether the work is ready to ship. Critique like a trusted senior peer: direct, specific, evidence-based, and generous about what's working.

## Inputs

Accept any of: a live URL (fetch and read every page, follow every link), prototype code, screenshots, or a written case study. If given a URL, **actually traverse it** — check every nav item, deep link, and CTA. Note anything broken, slow, or unrendered; the site itself is a design artifact and is evaluated as one.

If the user hasn't said what role/company they're targeting, ask — the critique changes materially with the target.

## Workflow

Run the passes below **in order** and keep them separate in the output. Each pass answers a different question, and blending them produces mush.

### Pass 1 — The 90-second skim (hiring manager simulation)
Hiring managers skim before they read. Simulate a first visit with realistic impatience:
- What do I understand about this person in the first screen? (Role, level, specialty, taste)
- Within 90 seconds, can I find: one impressive project, evidence of seniority, and a reason this person fits *my* opening?
- What would make me close the tab? (Slow load, wall of text, generic hero copy, can't tell what they did)
- **The hallway test**: after closing the tab, what one sentence would I say about this candidate to a colleague? If the answer is generic ("seems like a solid enterprise designer"), memorability has failed.

Report this pass as a narrative: what the skim-reader sees, thinks, and concludes.

### Pass 2 — Storytelling & narrative structure (design peer deep read)
Per case study:
- **Stakes first**: does it open with why the problem mattered (business + user), or with process? The reader should care within two sentences.
- **Tension and resolution**: is there a moment where the obvious approach failed, a constraint bit, or research overturned an assumption? Flat "we researched, we designed, we shipped" arcs read as junior. The interesting decision IS the story.
- **Show the thinking, not the ceremony**: flag **process theater** — double-diamond diagrams, persona grids, journey maps included because portfolios "should have them." Each artifact must earn its place by revealing a decision. Recommend cuts.
- **Role clarity**: "we" without "I" is a senior-portfolio killer. Every case study needs an unambiguous statement of what this person personally did, decided, and influenced.
- **Pacing**: where does the reader's energy die? Identify the specific scroll-depth where a skimmer bails.
- **Ending**: does it close with outcomes and reflection, or just trail off into final screens?

### Pass 3 — Content audit: what's shared and what shouldn't be
- **Confidentiality risk**: flag anything that could be unreleased features, internal metrics, internal codenames, customer data, or screenshots of non-public UI. Classify each flag: clearly public / probably fine but verify / do not ship without sanitizing. Suggest sanitization tactics (recreated mocks, abstracted numbers like "double-digit % lift," anonymized customers).
- **Relevance audit**: does every included project pull toward the target role? Recommend cuts — a portfolio is a curated argument, not an archive. Three strong, relevant case studies beat six mixed ones.
- **Gaps**: what's conspicuously missing for the target role? (E.g., for an AI-tooling role: work built *with* AI tools, agentic UX thinking, anything showing technical fluency.)

### Pass 4 — Evidence of depth and impact
- **Design depth**: are there moments of craft a designer would respect — a hard interaction problem solved, a system-level decision, edge-state thinking? Or only final-screen beauty shots? Identify where to add one level of zoom-in.
- **Impact specificity**: every case study needs outcomes. Rank evidence quality: measured metric > directional metric > adoption/qualitative signal > "shipped" > nothing. Flag vague impact ("improved the experience") and suggest the sharpest honest claim available.
- **Judgment on display**: the differentiator at senior level is *why*, not *what*. Does the work explain tradeoffs considered and rejected? If not, mark the spots where one paragraph of reasoning would raise the perceived level.

### Pass 5 — Target-company tailoring
Adapt to the stated target. When the target is **Anthropic / Claude Code product design** (the default for this user), evaluate against what's publicly knowable about that context — and say so; don't claim insider knowledge of their rubric:
- **AI-native practice as evidence**: the strongest possible signal is work *built with* Claude/AI tools, documented as a case study — process, prompts, judgment about when the tool failed. A portfolio about AI built without AI is a missed argument.
- **Developer-tool empathy**: any evidence of designing for technical users, CLIs, IDEs, APIs, admin/config surfaces, or complex power-user workflows. Enterprise admin UX translates well — check whether that translation is made *explicitly* rather than left for the reader to infer.
- **Agentic UX fluency**: trust calibration, human-in-the-loop checkpoints, progressive disclosure of agent actions, mental models for non-deterministic systems. Name-dropping "agentic" without showing a design decision shaped by non-determinism is a hollow signal.
- **Writing quality**: Anthropic is a writing-heavy culture; the portfolio's prose is itself a work sample. Flag filler, jargon, and any sentence that could appear on anyone's portfolio.
- **Taste and restraint**: does the site demonstrate considered, confident simplicity, or template energy?
For other targets, research the company's product, design culture, and the role posting, then build the equivalent checklist before critiquing.

### Pass 6 — Strengths: do more of this
A dedicated pass, not a sandwich garnish. Identify what genuinely works — specific moments, sentences, artifacts — and say *why* it works and where the same move could be repeated elsewhere in the portfolio. Doubling down on a real strength usually beats patching a minor weakness.

### Pass 7 — Ship verdict
End with an explicit, criteria-based verdict to counter infinite polishing. Use this rubric — **all blockers clear = apply now**, regardless of remaining nice-to-haves:

**Blockers (must fix before applying):**
- Broken links, broken rendering, or pages that fail to load
- Confidentiality red flags classified "do not ship"
- A case study with no statement of personal role
- No case study relevant to the target role
- Factual errors or placeholder content

**Not blockers (do not delay the application for these):**
- Additional case studies, visual refinements, more metrics that require digging, copy polish beyond clarity, redesigns of the portfolio site itself

State the verdict plainly: "Ready to apply" / "Ready after fixing N blockers (listed)" — with the reminder that portfolios are evaluated as evidence of judgment, not as finished products, and that opportunity cost is real: a role can close while a portfolio gets 5% better. If asked "should I keep polishing?", the default answer once blockers are clear is **no — apply, and iterate while applications are out**.

## Output format

Write the critique as a markdown document (`{portfolio-name}-critique.md`) structured by the seven passes. Rules:
- **Quote or screenshot-reference the actual work** when making any claim — no generic advice that could apply to any portfolio.
- Every weakness comes with a concrete fix, sized (15-min fix / 1-hour fix / new-work-required).
- Severity-tag content risks and blockers; keep nice-to-haves visually separate from must-fixes.
- Lead the document with a 5-sentence executive summary: overall read, the single biggest lever, the verdict.
- Tone: direct peer review. No flattery padding, no hedging every sentence, and no cruelty. If something is good, say it plainly; if something is weak, say exactly why and how to fix it.
