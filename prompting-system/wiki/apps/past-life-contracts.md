---
title: Past-Life Contracts
type: app
created: 2026-05-08
updated: 2026-05-08
tags: [app, fork, vedic-only, contracts]
---

# Past-Life Contracts

The narrowest fork. One system, two people, one unfinished contract.

## What it is

A Vedic-only mystical storytelling app. Generates a narrative reconstruction of a karmic contract between two souls: a broken vow, an unequal exchange, a rescue that turned into possession, an unfinished union. The output is a **literary short story** (800-1200 words), not a horoscope.

## Tonal posture

**Recovered memory novella.** Period-appropriate, sensory-rich, literary. Strictly forbidden: Western astrology vocabulary, fabricated technical certainty, generic divination framing. The story is recovered memory, not utility advice.

## Voices in use

| Voice | Modes |
|---|---|
| [[vedic]] | the only voice; pair-specific |

This app *deliberately narrows* the canonical engine: one system, one pair, one contract. No synastry overlays from other systems. No Western terminology. No multi-system blending.

## Architecture

- **Three layers like canonical**, but Vedic-only:
  - Layer 1 (`layer1-domain.ts`): Jyotish-only worldview, contract types, location logic
  - Layer 2 (`layer2-mandate.ts`): writing mandate, language-aware (11 languages), JSON output structure
  - Layer 3 (`layer3-polish.ts`): optional second-pass prose polish
  - Plus an audio narration pass (`audioNarrationPass.ts`): TTS adaptation, 500-700 words, stripped of astrology terminology
- **Compute → constrain**: Swiss Ephemeris (Lahiri sidereal, whole-sign houses, Vimshottari Dasha, D60) computes the chart, then *overwrites* the LLM's metadata with the deterministic computed nodal axis. No room for hallucination.
- Backend: Hono on Fly. Bundle ID: `app.past-life-contracts` (or similar).

## Origin

- First backend commit: **2026-04-17** (`dd0d34d`, "Initial backend + security audit fixes")
- Auth integrated 2026-04-19 (`a2e5119`)
- Build-bump cycle 2026-05-01 to 05-03 (mobile store submission)

## What makes it specific

- **One system only**. The most ruthless tonal narrowing across the four apps.
- **Story over utility.** Framed as recovered memory, not divination.
- **Computed metadata constrains the LLM**, never decorates the narrative. The chart is upstream of the prose, not parallel to it.
- **Pair, not individual**. Two people, one contract. No solo readings.
- **Output is structured JSON** (title, era, location, relationship, body paragraphs, computed metadata) before being polished into prose.

## Connection back to engine

Inherits from [[apps/1-in-a-billion]]:
- Three-layer architecture (domain → mandate → polish)
- Multi-language Layer-3 rewrite pipeline
- Vedic depth (Lahiri, Vimshottari, D9, D60)
- Long-form narrative as primary output

Diverges:
- One voice ([[vedic]]) instead of five
- One scope (two-person karmic contract) instead of three modes
- Computed-data-as-truth instead of model-as-author

## Sources

- `raw/past-life-contracts/backend/src/prompts/layer1-domain.ts`
- `raw/past-life-contracts/backend/src/prompts/layer2-mandate.ts`
- `raw/past-life-contracts/backend/src/prompts/layer3-polish.ts`
- `raw/past-life-contracts/backend/src/prompts/audioNarrationPass.ts`
- See also: [[vedic]] voice page
