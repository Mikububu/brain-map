---
title: Fairytale to Diagnostic Noir (The Apple-Driven Tone Shift)
type: decision
date: 2026-04-15
commit: 3e7eb2a
created: 2026-05-08
updated: 2026-05-08
tags: [decision, unhinged, apple, rebrand, tone]
---

# Fairytale to Diagnostic Noir

**2026-04-15**, commit `3e7eb2a`, *"clean remaining toxic prompt tone."* The day [[apps/unhinged|Unhinged]]'s framing changed from mythic to forensic. The deeper layer of the [[topics/toxic-to-unhinged-rebrand|Apple-driven rebrand]].

## Before (`9e6efbd`, *"toxic-chic rewrite"*, 2026-04-08)

System prompt: *"You are telling the story of a soul. Not analyzing a chart. This is a fairytale for adults. A mystery theater of longing and obsession."*

Tone: *"Dreamy and mythic, like a fairytale for adults... Honest about shadows, compassionate about wounds."*

Opening instruction: *"Begin like a fairytale for adults, an invocation that makes the listener pause."*

Override name: `toxicComedyOverride`. Phrase: *"SEEKING TOXIC ARRANGEMENTS."*

## After (`3e7eb2a`, 2026-04-15)

System prompt: *"You are telling the story of a person who already knows they are the problem. Not analyzing a chart. This is **diagnostic noir for adults**. A sharp theater of longing, obsession, defense, and cost. Write as a storyteller who sees the invisible architecture of a pattern and refuses to rescue it."*

Tone: *"Darkly funny and precise, like a forensic narrator with perfume on the evidence bag... Honest about shadows, clear about wounds, **allergic to rescue language**."*

Opening instruction: *"Begin in the middle of a diagnosis already happening, not with an invocation. Start mid-scene, mid-observation, as if the reader walked in on something."*

Override name: changed to `chaosComedyOverride`. Phrase: *"DECODE YOUR ROMANTIC CHAOS."*

## Why

Apple App Store review pressure required the surface to soften. *"Toxic"* in the marketing was not going to pass.

But the rebrand could not just be cosmetic; the prompts themselves had to reflect the new framing or the readings would clash with the marketing. So the user did both: changed the App Store metadata *and* shifted the tone of the system prompt from mythic-poetic to clinical-forensic.

The shift is consistent: *fairytale → diagnostic noir*; *compassionate → allergic to rescue language*; *invocation → mid-scene observation*. Same shadow content, different genre.

## What stayed strong

The [[apps/unhinged|spicy-surreal style]] (where the actual transgressive voice lives) was **not softened**:

- 40% shadow emphasis (unchanged)
- Raw verbs: *devour, penetrate, consume, shatter, burn, dissolve, possess* (unchanged)
- *"Include ACTUAL DANGER: addiction, emotional violence, manipulation patterns, betrayal trajectories"* (unchanged)
- *"Sex as doorway or destruction"* section (unchanged)

Apple cares about the app *name*, the *subtitle*, the *description*. Apple does not run grep on the source code. The substance survived; the surface translated.

## What it unblocked

Unhinged passing App Store review and shipping. The "diagnostic noir" tone that defines the current Unhinged voice. The [[topics/toxic-to-unhinged-rebrand|rebrand topic]] makes the full politics legible.

## Connections

- [[apps/unhinged]]
- [[topics/toxic-to-unhinged-rebrand]]
- [[topics/the-dialectic]] (Unhinged's side of the dialectic in its current form)
- [[decisions/unhinged-import]] (the import a week earlier, before this tonal shift)

## Sources

- `raw/unhinged/toxic-app/backend/src/prompts/styles/production.ts` (the file changed by this commit)
- `raw/unhinged/toxic-app/backend/src/prompts/styles/spicy-surreal.ts` (the file *not* changed)
- Commit `3e7eb2a`
