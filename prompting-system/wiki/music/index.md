---
title: Music
type: hub
created: 2026-05-08
updated: 2026-05-08
tags: [music, hub]
---

# Music

The music architecture of the four-app suite. Five voices, three modes (individual, synastry, family-overlay), one verdict, and an external generation engine (MiniMax). The user has called this *"worth a PhD in itself."* This section captures every layer.

## The four-layer pipeline

1. **Individual music prompts** — one per voice. Read a single person's reading; produce a song's lyrics + a MiniMax brief
2. **Synastry / overlay prompts** — one per voice. Read a two-person collision; apply the **50/25/25 weighted-crossover rule**
3. **Family-overlay prompts** — one per voice in [[apps/families-app|Families-app]]. Reframe the voice for relational scope (no romance, lineage instead)
4. **Final Verdict music prompt** — the meta-layer synthesis. Dido + Eminem stadium duet. The five systems agreeing in song

The output of any of these flows to **MiniMax** (external music-generation API), which produces the actual audio file (3:30-4:15 typical).

## Per-voice pages

| Voice | Sonic anchor | Page |
|---|---|---|
| Western | Sienna Rose, indie-pop introspection | [[music/western]] |
| Vedic | Anoushka Shankar 2026, contemporary Indian-classical | [[music/vedic]] |
| Kabbalah | Dead Can Dance 2026, sacred darkwave | [[music/kabbalah]] |
| Gene Keys | Random eclectic (Bon Iver, FKA Twigs, Sigur Rós, James Blake, Sevdaliza, Thom Yorke) | [[music/gene-keys]] |
| Human Design | Kamasi Washington meets Esperanza Spalding, late-night jazz duet | [[music/human-design]] |

Plus:

- [[music/philosophy]] — the cross-cutting principles, dead ends, the "weighted crossover" paradox
- [[music/final-verdict]] — the meta-layer Dido + Eminem stadium verdict

## The cultural-pairing rule

Synastry / overlay prompts apply a strict 50/25/25 weighting:

- **50%** = the voice's sonic centre (Sienna Rose / Anoushka / Dead Can Dance / random / Kamasi)
- **25%** = Person 1's birthplace cultural memory
- **25%** = Person 2's birthplace cultural memory

Birthplace flows in via Supabase's `library_people` table (`birthCity` field), feeds the LLM as research material, and **never leaks to MiniMax**. City names are banned from the audio brief; only country-level traditional / folk references make it through.

## What changed when

- **Feb 16** (`4cba79c2`) — all 5 voice music prompts created
- **Mar 17** — restored after a fallback era; synastry overlays added
- **Mar 22** (`82d44f01`, `f353d1ce`, `391fbeda`, `a5194d04`) — the master simplification day. Bowie cut-up framing removed, 50/25/25 locked in, name-stripping hardened, instruments-list ban introduced
- **Mar 30-31** — 27+ commits in 23 minutes (00:14 to 00:37 UTC on March 31). The "thousands of modifications" crucible. Most volatile: [[music/gene-keys]]. Most important: the [[music/final-verdict]] paring-down
- **Apr 15** (`7f21ce4f`) — `lyricsGeneration.ts` test suite added. System stabilises

## What's not music

[[apps/past-life-contracts|Past-Life Contracts]] has no music. It uses **`audioNarrationPass.ts`** instead, a TTS-optimised narrative-prose adaptation (5-7 paragraphs, ~500-700 words) of the karmic-contract story, intended for spoken delivery via Qwen3 TTS. See [[topics/qwen3-research]] for the TTS substrate.

## Connections

- [[topics/music-prompts]] — the original, lighter overview (now a satellite of this hub)
- [[topics/app-soundtrack]] — the *other* music: in-app theme tracks distinct from the per-reading music here
- [[topics/per-language-llms]] — the same dispatch-per-language logic applies to lyric language choice
