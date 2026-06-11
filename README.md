# Design Judgment, Installed

Ten Claude skills that encode the judgment-heavy parts of my design practice. Critique, curation, voice, storytelling, self-review: the tools I build with hold the same bar I do.

## Why this exists

AI tools lowered the execution floor. Anyone can ship a clean, functional site now. What didn't get cheaper: knowing what to cut, what story to tell, when something is done, and what good looks like for the situation in front of you.

So instead of using Claude to execute faster, I encoded the judgment half. Each skill in this repo is a piece of how I actually work. My critique standards, my editing instincts, my writing voice, my definition of ready to ship, written down precisely enough that an agent can apply them. The skills are opinionated on purpose. That's the point.

I'm a product designer ([portfolio](https://tori-rice.vercel.app)), and I built these while building my portfolio with Claude Code. I didn't plan a skill suite; I kept noticing pieces of my practice that could be encoded, and ten skills later it runs as a system. The repo is both the tooling and the case study.

## The skills

| Skill | The judgment it encodes |
|---|---|
| [build-journal](./build-journal) | What's worth remembering about a build. Captures attempts, failures, pivots, and verbatim prompts as they happen, because judgment in the moment can't be reconstructed later. |
| [prompt-retro](./prompt-retro) | How to get better at working with the tool. Pairs my actual prompts with their outcomes, finds my recurring patterns, and maintains a one-page personal playbook. |
| [case-study-writer](./case-study-writer) | What makes project work read as a story. Stakes first, decisions over artifacts, failures treated with respect, impact claims ranked by evidence quality. |
| [voice](./voice) | How I sound. One calibrated profile that every other skill writes in, including the words I'd never use. |
| [writing-guardrails](./writing-guardrails) | What machine writing smells like, and how to never produce it. The one skill here with nothing personal in it; take it as-is. |
| [visual-storytelling](./visual-storytelling) | What shape information has. Renders flows as flows and systems as systems instead of flattening everything into card grids, in my visual language. |
| [portfolio-edit-pass](./portfolio-edit-pass) | What to cut. A screen-by-screen editor with a deliberate bias toward cutting, because you can't see the bloat from inside your own work. |
| [portfolio-critique](./portfolio-critique) | What a reviewer actually sees. A seven-pass critic with a 90-second hiring-manager skim, a confidentiality audit, and a rubric-based ship verdict. |
| [site-preflight](./site-preflight) | What ready to share means mechanically. Every link, the Slack unfurl preview, image weights, placeholder text. Function only, no opinions. |
| [handoff-spec](./handoff-spec) | What prototypes hide. Enumerates the states the happy path skips (empty, error, permission, truncation, concurrency) and proposes a default for each. |

## How they chain

```
while building:      build-journal ──► prompt-retro
                          │
to publish:               ▼
          case-study-writer ──► portfolio-edit-pass ──► portfolio-critique ──► site-preflight
                          ▲
under all prose:        voice + writing-guardrails
under all visuals:      visual-storytelling
```

The journal captures raw material during builds. The writer turns it into a draft, the editor cuts, the critic grades and renders a ship verdict, and preflight makes sure nothing embarrassing happens when the link gets shared. Voice and the guardrails sit under everything that produces prose; visual storytelling sits under everything that produces diagrams. Handoff-spec runs when a prototype goes to engineering, enumerating the states the happy path skips.

The two skills that matter most are the ones that compound. The journal means every project documents itself into future case-study material. The retro means every session makes the next one better.

## Install

**Claude Code:** clone and symlink into your skills directory.

```bash
git clone https://github.com/tjrice42/design-judgement-skills.git
cd design-judgement-skills
mkdir -p ~/.claude/skills
for d in */; do ln -s "$(pwd)/$d" ~/.claude/skills/"${d%/}"; done
```

Start a new session and the skills load automatically when relevant.

**claude.ai / Claude Desktop:** zip any skill folder, rename it to `.skill`, and upload it under Customize → Skills.

## A note on borrowing these

The mechanics will work for anyone, but the opinions inside are mine: the cut threshold, the blocker list, the never-say words. If you fork this, replace my judgment with yours. That's the actual exercise. The exception is writing-guardrails, which carries no personal opinions and works as-is for anybody.

## Built with

Claude Code, and these skills themselves. The build journal was running while the later skills were written, and the journals from this build are becoming a case study on [my portfolio](https://tori-rice.vercel.app). I'd welcome feedback, and I'm happy to walk through how any of it works if there's interest.
