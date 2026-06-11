# design-judgement-skills

A suite of Claude skills I built to run my own design practice as a system.

Execution got cheap. Judgment didn't. These skills encode the judgment-heavy half of how I work: capturing a build as it happens, writing it up in my voice, trimming and critiquing it, and QA-ing the site before it ships, so my standards travel with the tools.

I built them while building my portfolio. In a real sense, these are the tools that built it.

## The skills

| Skill | What it does |
| --- | --- |
| **build-journal** | Maintains a running journal of a build as it happens (attempts, failures, pivots, decisions) so case-study material exists the moment you ship. |
| **case-study-writer** | Drafts a portfolio case study from raw materials: build journals, notes, screenshots, transcripts. |
| **voice** | Applies my personal writing voice to any prose written on my behalf. |
| **portfolio-edit-pass** | A screen-by-screen editorial pass that flags what to cut or merge before review. |
| **portfolio-critique** | A structured, multi-lens critique: storytelling, confidentiality risk, hiring-manager appeal, design depth, readiness. |
| **site-preflight** | Mechanical pre-flight QA before sharing a site: broken links, mobile, meta/OG, favicon, accessibility. |
| **prompt-retro** | A retrospective on how I prompt, grounded in my actual prompts and what happened next, with a cumulative playbook. |

## How they fit together

```
build-journal ─▶ case-study-writer ─▶ portfolio-edit-pass ─▶ portfolio-critique ─▶ site-preflight
                     (+ voice)
```

`prompt-retro` runs across all of it, making the prompting better over time.

## A note on borrowing these

These encode my judgment and my voice. Take the structure; swap in your own standards.
