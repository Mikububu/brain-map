---
title: The January Foundation
type: topic
created: 2026-05-08
updated: 2026-05-08
tags: [topic, history, pre-v2, foundation]
---

# The January Foundation

The 6-week period from **2026-01-07** (first commit) to **2026-02-18** (eve of the v2 architectural rewrite). The foundation the v2 voice architecture was built ON, not from scratch.

This was missed by the first pass of the wiki because the early commits live on a non-HEAD branch. `git log --all --reverse` reveals them.

## What was already there at v0

At the very first commit (`f486164f`, Jan 7), the engine had:

- A working **song-generation pipeline** (MiniMax + DeepSeek lyrics)
- All five astrology systems as **TypeScript modules** in `backend/src/prompts/systems/`
- Five **narrator voice samples** (Anabella, Dorothy, Ludwig, Grandpa, Default), anchored to a Henry Miller quote from *Tropic of Cancer*
- Synastry overlays for each system with 10-dimension prompts
- Swiss Ephemeris integration

This was not a skeleton. It was a fully-running app the user then *rewrote on top of itself*.

## What was NOT yet there

- No `prompt-layers/` directory (created Feb 18 with `af0553d2`)
- No five distinct narrator archetypes ("novelist haunted," "Aghori witness," "midnight rabbi," "field biologist," "engineer in love with the machine")
- No Anaïs Nin anchor for [[western]]
- No [[western|Incarnation Zone Contract]]
- No deterministic [[topics/matching-algorithm|matching engine]] (matchEngine.ts was hardcoded mock data: Irena, Haruto, Selene)
- No per-voice [[topics/music-prompts|music prompts]] (single unified lyrics generator)

## The early structure

Pre-v2 prompts lived as **TypeScript modules** in `1-in-a-billion-backend/src/prompts/`:

```
src/prompts/
├── systems/{vedic,western,kabbalah,gene-keys,human-design}.ts
├── styles/production.ts          # single shared style
├── styles/spicy-surreal.ts
├── nuclearPrompts.ts             # master prompt builder, 2000+ word templates
├── structures/, techniques/, spice/
└── builder.ts, index.ts, core/
```

The shared style invoked **David Attenborough** as the only literary reference: *"David Attenborough narrating human souls."* The five system narrators that exist today did not exist yet.

## Pivotal commits in this period

| Date | Move | What changed |
|---|---|---|
| 2026-01-07 | First commit (`f486164f`) | Song pipeline complete, 5 systems live |
| 2026-01-07 | Voice samples (`b6378f8b`) | Henry Miller anchor; Anabella, Dorothy, Ludwig, Grandpa, Default |
| 2026-01-07 | Doc consolidation (`b9cb2b1f`) | 85 MD files → 35; song-per-document routing |
| 2026-01-09 | Vedic writing guide (`418ea42b`) | 411-line "left-handed perspective, fatalistic irony" |
| 2026-01-09 | ID-based matching (`2b79d243`) | Replaced name-based matching, fixed collision bug |
| 2026-02-10 | "Golden Version" backup (`5f9e1ca5`) | Checkpoint before v2 work |
| 2026-02-13 | v2 prompt-layer engine checkpoint (`38586aad`) | Vedic matchmaking spec; preference-scale migration begins |
| 2026-02-14 | Word-count floor (`227fb3de`) | 2500-3000 minimum for long-form; auto-continue |
| 2026-02-16 | v2 backend split (`4cba79c2`) | New `1-in-a-billion-v2/` directory |
| 2026-02-18 | `prompt-layers/` born (`af0553d2`) | Five narrator archetypes locked in; markdown replaces TypeScript |

## What carried INTO v2 (the foundation)

- All five systems (the v2 rewrite refined the **voice**, not the chart logic)
- Five narrators as TTS voice assets (Anabella et al.)
- The Henry Miller quote (lives on in [[apps/unhinged]]'s body anchor)
- Song-generation pipeline
- Swiss Ephemeris

## What v2 REPLACED

- TypeScript modules → markdown `prompt-layers/` (readable, git-friendly, no recompile)
- Single shared narrator → **five distinct archetypes**
- David Attenborough as universal reference → per-system literary anchors
- Generic "dark soul storytelling" → Incarnation model with [[western|Zone Contract]]
- LLM-generated verdicts → preference-scale + soft-ranking spec

## What v2 DROPPED ENTIRELY

- Hardcoded matchEngine mock data (Irena, Haruto, Selene)
- Single unified lyrics prompt (replaced by per-voice [[topics/music-prompts|music prompts]])
- Intensity levels 1-10 (SafeBR / SPICY / EXTREME tiers)
- Generic "consciousness documentary" framing

## The reframe this forces

The v2 rewrite was **not the engine's foundation**. It was a **voice architecture overhaul on an existing engine**. The five astrological systems were already running on Jan 7. The five distinct narrator consciousnesses (the heart of what makes the engine *philosophical*) were the v2 innovation, layered on top.

When the user says *"since December,"* they mean the conceptual work, the December-into-January build of the engine itself. The first GitHub commit landed Jan 7; local development likely predated by a few weeks. The philosophy began forming in January and **crystallised through the v2 rewrite in mid-February**.

The five voice pages on this wiki ([[western]], [[vedic]], [[kabbalah]], [[gene-keys]], [[human-design]]) all date their "Birth" to February 18-19, but that is the birth of the *narrator archetype*, not the birth of the system itself. Everything you read on those pages sits on top of this January foundation.

## Sources

- `raw/1-in-a-billion/` (full git history via `git log --all`)
- Pre-v2 files (now ancestors): `src/prompts/systems/*.ts`, `src/prompts/styles/production.ts`, `src/prompts/nuclearPrompts.ts`, `src/services/matchEngine.ts`, `src/services/lyricsGeneration.ts`, `src/config/voices.ts`

Commits: `f486164f` · `698937c0` · `b9cb2b1f` · `b6378f8b` · `083f4b9d` · `418ea42b` · `2b79d243` · `c2cfd42f` · `5f9e1ca5` · `38586aad` · `227fb3de` · `4cba79c2` · `af0553d2`
