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

## Two codebase incarnations of one app

Unhinged is **one app** with two codebase incarnations. *"Seeking Toxic Relationships"* was the original tagline / subheadline, used as the GitHub repo name in the early Swift era; it was never a separate app.

### Early Swift codebase (2026-01-19 to 2026-02-12)

The first incarnation was a pure Swift / SwiftUI iOS app at `Mikububu/seeking-toxic-relationships` (GitHub repo created 2026-01-18). Tinder-style swipe interface, neobrutalist aesthetic (#000000 black, #FF453A iOS red, "visual aggression 0.7"), local `MockMatchService`. The design doc was explicit that the app *"must read and consume all relevant Markdown files from the One in a Billion folder as read-only input"* and *"must not contain its own competing doctrine"*; from day one, this was conceived as a toxicity-amplifying lens on [[apps/1-in-a-billion]]'s engine.

The unbuilt `new-arch/` monorepo (committed at launch but never deployed) coded the **earliest deterministic synastry weighting** in the user's body of work:

| Factor | Weight |
|---|---|
| Rahu Influence | 25% |
| Saturn Endurance | 15% |
| Mars Aggression | 20% |
| 8th House Intensity | 20% |
| 12th House Loss | 10% |
| Shared Nakshatras | 5% |
| Lunar Compatibility | 5% |

This logic predates the canonical engine's Mar-10 deterministic-synastry pivot by a month. See [[topics/matching-algorithm]].

Last Swift commit: **2026-02-12** (`43d2564`, *"ci(v2): add single GitHub Actions workflow for V2"*). 56-day silence followed.

### React Native codebase (2026-04-08 onward)

On 2026-04-08 the app was rebuilt on a different stack (Expo React Native + Hono backend), borrowing [[apps/1-in-a-billion]]'s engine wholesale. New GitHub repo: `Mikububu/unhinged-toxic`. Most prompt files byte-identical to canonical at import time. The current Unhinged.

### What carried across the rewrite

- The Vedic-as-toxic-matching philosophy
- The neobrutalist design language
- The "toxicity scoring" terminology
- The narrative-driven *fit cards* / *watchouts* framework
- The "first move" suggestions framing

### What was abandoned

- The Swift / SwiftUI iOS codebase entirely
- The local `MockMatchService` and in-app chart calculation
- The `new-arch/` monorepo structure (unused; never deployed)
- Free-swipe-limit subscription model (replaced by reading-based subscription)
- Multi-screen onboarding (compacted)

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
