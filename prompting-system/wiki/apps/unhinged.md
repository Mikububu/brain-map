---
title: Unhinged
type: app
created: 2026-05-08
updated: 2026-05-08
tags: [app, fork, noir, dialectic]
---

# Unhinged

The dialectical opposite of [[apps/1-in-a-billion|1 in a Billion]]. Same engine. Opposite voice temperature.

## What it is

The same five-system reader, but the rewrite layer is rewritten as **diagnostic noir / chaos-chic**. Sexually explicit, shadow-forward (~40%), Jung × Lynch. The system prompts are imported wholesale from the canonical app; what diverges is the *how-to-write*.

## Tonal posture

**"Exquisite disaster connoisseur."** Provocation wins over reverence when they clash. The reader should feel SEEN, *exposed, and sometimes grimly amused by the human comedy of it.* Henry Miller as body anchor: *"Raw, unfiltered, ecstatic. The body as the primary instrument of knowing. Beauty found inside filth, philosophy inside fucking."*

## Voices in use

Same five voices as [[apps/1-in-a-billion]], but with the noir override layered on the rewrite layer:

| Voice | Notable divergence |
|---|---|
| [[western]] | Tenderness replaced with provocation |
| [[vedic]] | Full Sanskrit graha names; goddess voice escalated (Rahu as decapitated woman, etc.) |
| [[kabbalah]] | **No divergence**. The noir register has nothing to add to a candle-lit room |
| [[gene-keys]] | Dangerous-organism emphasis amplified |
| [[human-design]] | Engine pushed to redline |

## Architecture

- Same three-layer composition as canonical
- Same Swiss Ephemeris compute, same DeepSeek
- Same eleven languages
- Diverges only in `prompt-layers/rewrite/` and parts of `prompt-layers/style/` (especially the `spicy-surreal` style guides)
- Bundle ID: `app.unhinged.toxic`
- Codebase folder: `Unhinged/toxic-app/`

## Origin

- Initial import from canonical: **2026-04-08** (commit `6b4363e`, "chore: initial import of toxic-app workspace")
- Most files byte-identical to canonical at import time
- Backend infrastructure differs in: bundle prefix (`unhinged_toxic_v1_`), Pricing-resume step missing, sequential audio (vs parallelised in canonical)
- GitHub repo: `Mikububu/unhinged-toxic` (created 2026-04-08)

## The predecessor: Seeking Toxic Relationships

Unhinged is the **second incarnation** of the toxic-relationship-app idea. The first was [[apps/seeking-toxic-relationships]], a pure Swift / SwiftUI iOS app created on **2026-01-19** (`Mikububu/seeking-toxic-relationships`). The user explored Vedic-as-matching-system there for ~2.5 months before abandoning the Swift codebase entirely and rebuilding the same concept inside [[apps/1-in-a-billion]]'s engine on April 8. What survived: the *concept* (Vedic astrology + dark / toxic relationship patterns). What was thrown away: the entire codebase.

## What it adds to canonical

- `writing-style-guide-spicy-surreal-v2.md`: Jung × Lynch, RED ROOM imagery, 40% shadow emphasis, raw verbs (devour, penetrate, dissolve)
- `styles/production.ts` chaos-comedy override: *"Primary tone is dark comedy: sarcastic, provocative, exaggerated, and funny... campy claymation energy, not nihilistic."*
- Henry Miller body anchor across rewrite layer

## What's particular

- The engine is the canonical engine; the philosophy is its inverse
- This app proves the engine is voice-shape-agnostic: same chart, same data, opposite reading
- The dialectic with [[apps/1-in-a-billion]] is the architectural feature, not a bug
- **The premise depends on uncensored LLM output.** Henry Miller as body anchor requires a model that will actually write Henry Miller. See [[topics/uncensored-llms]] for the open infrastructure problem.
- **The rebrand was not just cosmetic.** Apple required the surface ("Toxic" → "Unhinged") to change. On `3e7eb2a` (2026-04-15), the system prompt also shifted from *"fairytale for adults"* to *"diagnostic noir for adults."* The shadow content stayed at full strength; the framing went from mythic to clinical. See [[topics/toxic-to-unhinged-rebrand]].

## Sources

- `raw/unhinged/toxic-app/backend/prompt-layers/rewrite/narrative-rewrite-en.md`
- `raw/unhinged/toxic-app/backend/prompt-layers/style/writing-style-guide-spicy-surreal-v2.md`
- `raw/unhinged/toxic-app/backend/src/prompts/styles/production.ts`
- `raw/unhinged/toxic-app/backend/prompt-layers/style/writing-style-guide-incarnation-v1.md`
