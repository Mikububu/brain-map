---
title: Music Prompts
type: topic
created: 2026-05-08
updated: 2026-05-08
tags: [topic, music, lyrics, modulation]
---

# Music Prompts

The user's example of "many modulations and refinements, sometimes worked, sometimes didn't." A second narrative layer that runs beside every reading.

## Now

Five voice-specific music prompts ([[western]], [[vedic]], [[human-design]], [[gene-keys]], [[kabbalah]]) plus a **Final Verdict** prompt. Each has individual + synastry modes. Each feeds **MiniMax** (external music-generation service) and produces full singable lyrics: 25-35 lines, structured verse / chorus / bridge / outro.

## What they produce

A JSON object: full lyrics, 2-5 word title, short genre label, vocalist descriptor, one emotion word, plus the MiniMax prompt itself.

> "Write full song lyrics. 25-35 lines. Verse, chorus, verse, chorus, bridge, chorus, outro."

## Architecture

- **Individual mode** (5 prompts): one person, one reading excerpt, one ~4-minute composition
- **Synastry mode** (5 overlays): two people; weighting **50% system sonic centre + 25% Person 1 culture + 25% Person 2 culture**
- **Families-app overlays**: same two-person frame, different emotional weight (lineage, family pressure instead of romantic chemistry)
- **Past-Life Contracts**: no music. Vedic-only narrative; audio is TTS of the prose

## Sonic anchors per voice

| Voice | Anchor |
|---|---|
| [[western]] | Sienna Rose indie-pop |
| [[vedic]] | Anoushka Shankar contemporary Indian-classical |
| [[human-design]] | Kamasi Washington jazz |
| [[gene-keys]] | randomly selected eclectic reference |
| [[kabbalah]] | Dead Can Dance darkwave |
| Verdict | Dido / Eminem duet |

## Timeline

| Date | Move | What changed |
|---|---|---|
| 2026-02-02 | Restore per-voice anchors | After flattening; sonic identity rekindled |
| 2026-03-10 | Gene Keys random injection | 10 rotating refs, eclectic; static Stockhausen replaced |
| 2026-03-10 | Brian Eno direction, multilingual | Music enters LLM as cultural DNA, not formula |
| 2026-03-17 | LLM cultural research from birthCity | Birthplace becomes prompt-side texture, never leaks to MiniMax |
| 2026-03-22 | Synastry overhaul | birthCity lookup, no name injection, 25-35 line full lyrics |
| 2026-03-22 | Bowie cut-up simplification | Strip names, birthplaces; surrealist method as universal |
| 2026-03-30 | Universal contract for all 11 prompts | Standardise structure; prevent cascade breaks |
| 2026-03-30 | Western reverted to "Map Not Territory" version | Roll back over-specification; restore proven song |
| 2026-03-30 | Vedic: Tantric terms, female vocalist | Ground in devotion; narrow palette |
| 2026-03-31 | Gene Keys stripped | No artist refs, no system language; artist injection moved into code |

*Want any row expanded? Say "expand <date>".*

## Dialectic across apps

| | Canonical | Unhinged | Families | Past-Life |
|---|---|---|---|---|
| Voices | 5 + Verdict | inherits all | 5 + Verdict + 5 family overlays | none (TTS only) |
| Sonic anchors | Sienna Rose, Anoushka, Kamasi, Dead Can Dance, eclectic | inherits | inherits + relational reframe | n/a |
| Tone | personal scope | darker mood | lineage / family pressure | n/a |

## Dead ends

- Static artist anchoring in [[gene-keys]] (Radiohead, Bon Iver, FKA Twigs, Sigur Rós, Sevdaliza, Thom Yorke), replaced by random selection in code
- Bowie cut-up as mandatory across all voices, replaced for [[vedic]] (devotional path) and Families
- LLM cultural research from raw city names, replaced with static MUSIC_CULTURE_MAP / Supabase lookup (hallucination + inconsistency)
- City names in MiniMax prompts banned (acoustic metadata leak; country-level terms only, e.g. "Austrian alpine folk" not "Villach")
- Hebrew-only [[kabbalah]] lyrics, reverted to 50/50 English-Hebrew split
- `{personName}` injection into lyrics, contradicted the "NEVER use names" rule, removed in `82d44f01`

## Texture

How this builder thinks about music:

- **Sonic anchors over genre descriptors** (Anoushka Shankar, not "Indian-classical")
- **Birthplace as LLM-side texture, never in output**
- **Surrealism as method**: charged-fragment reassembly
- **Cultural weighting as structural rule**: 50% system / 25% / 25% for synastry, no blur
- **4-minute arc as default**

Refused: generic fusion, didactic astrology in lyrics, city names leaking to MiniMax, system jargon as lyric content, static artist lists that can't flex.

The signature paradox: **weighted crossover.** Honour two birthplace traditions at 25% each inside a 50% sonic centre. Each person's music lives in a collision, not a blend.

## Sources

- `raw/1-in-a-billion/backend/prompts/music/western-music-prompt.md` (plus 4 other voices + Verdict)
- `raw/1-in-a-billion/backend/prompts/music/*-overlay-music-prompt.md` (synastry variants)
- `raw/families-app/Families-app-src/backend/prompts/music/*-family-overlay-music-prompt.md`

Commits: `bda08398` · `9440de47` · `465803e7` · `82d44f01` · `391fbeda` · `f353d1ce` · `64574d8d` · `48ff68f2` · `6b4096a8` · `c595f9d9` · `e3d050d1` · `43af4f68`
