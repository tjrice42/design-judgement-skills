---
name: voice
description: Apply the user's personal writing voice to any prose written on their behalf — portfolio copy, case studies, bios, emails, LinkedIn posts, application materials. Use this skill whenever writing or editing text the user will publish or send as their own words, even if they don't mention voice or style. Also use it when the user wants to calibrate, update, or review their voice profile, or says something "doesn't sound like me."
---

# Voice

A single source of truth for how this user sounds in writing. Every skill or task that produces prose in the user's name reads the profile at `references/voice-profile.md` and writes in it — so "Tori's voice" is defined once, not approximated independently by every tool.

## Two modes

### Apply mode (default)
1. Read `references/voice-profile.md`.
2. Write the requested prose following it.
3. If the profile is still marked `PROVISIONAL`, say so once and suggest calibration — then proceed anyway with the seed profile.

When editing existing text the user wrote themselves, the bar is higher: preserve their phrasing wherever it already works; fix only what's unclear or weak. Their actual sentences outrank the profile.

### Calibration mode
Run when the user provides writing samples, asks to calibrate, or says output doesn't sound like them.

1. Collect 3+ samples of the user's real writing, ideally across registers (portfolio copy, a work message, something casual). More samples and more variety = better profile.
2. Analyze for the dimensions in the profile template: sentence rhythm, vocabulary fingerprint, directness, warmth, humor, formatting habits, and — most important — the **never list** (words and constructions this person would not produce).
3. Rewrite `references/voice-profile.md` with findings, quoting short fragments of their actual writing as exemplars. Remove the `PROVISIONAL` marker.
4. **Verify with a blind test**: write two short paragraphs on a neutral topic — one in the calibrated voice, one in generic-professional voice — and ask the user to pick which sounds like them and what's off. Fold corrections into the profile.

Recalibrate incrementally whenever the user corrects voiced output ("I'd never say leverage") — add the correction to the profile immediately rather than just fixing the one instance.

## Rules

- **The never list is the most enforceable part of voice.** Check drafts against it explicitly before delivering.
- **Voice ≠ register.** The same voice flexes across a portfolio case study and a Slack message. The profile defines the constant (rhythm, vocabulary, directness); the task defines the register. Don't flatten everything to one formality level.
- **Don't perform the voice.** Matching someone's style means their reader doesn't notice anything; it never means caricature. If the profile says "casual and direct," that's an absence of stiffness, not an injection of slang.
- **Authenticity guardrail**: this skill exists so the user's published words sound like them, not to ghostwrite a personality. Where the user's own draft text exists, it wins.
