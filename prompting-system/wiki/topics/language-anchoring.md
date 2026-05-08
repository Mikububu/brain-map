---
title: Language Anchoring
type: topic
created: 2026-05-08
updated: 2026-05-08
tags: [topic, languages, voice-anchors, native-script]
---

# Language Anchoring

The eleven-language [[topics/layer-3-rewrite|Layer 3 rewrite]] would default to English literary taste applied to other tongues. The explicit refusal of that bias is one of the most consequential moves in the engine's history.

## The eleven languages

en (English), de (German), es (Spanish), fr (French), hi (Hindi), it (Italian), ja (Japanese), ko (Korean), pt (Portuguese), ru (Russian), zh (Mandarin).

## The native voice anchors

Each language pairs with a culturally native literary voice. The reading sounds like *that writer* writing in *that language*, not like an English-language reading translated.

| Language | Confirmed voice anchor |
|---|---|
| Hindi | **Osho** |
| Russian | **Viktor Pelevin** |
| Mandarin | **Yu Hua** |
| English | Houllebecq, Mishima, García Márquez, Jelinek (rotating) |
| Other languages | (anchors set in `prompt-layers/rewrite/samples/`, not yet enumerated in this wiki) |

## The pivotal move

**2026-03-28** (`a6065909`, "rewrite samples: switch ru/hi to native-script source texts").
**2026-03-28** (`026b8247`, "rewrite: switch Hindi sample to Osho voice anchor").

The user explicitly rejected English literary bias in non-English readings. Hindi got Osho. Russian got Pelevin. Mandarin got Yu Hua. The rewrite samples switched from English-translated sources to native-script source texts.

## Why it matters

A Hindi reading anchored to (say) García Márquez would sound like translated magical realism. A Hindi reading anchored to Osho sounds like Osho. The reader's literary recognition is not borrowed; it's native.

## How the apps differ

- [[apps/1-in-a-billion]]: full eleven-language native-anchor implementation
- [[apps/unhinged]]: same languages, plus Henry Miller as additional body anchor in the rewrite layer
- [[apps/past-life-contracts]]: same eleven; simpler Layer 3 (the chart is upstream of the prose)
- [[apps/families-app]]: English anchors swapped to empathy writers (Robinson, Sebald, Ernaux); non-English anchors unchanged

## What's not yet captured

The non-English voice anchors beyond Hindi / Russian / Mandarin (German, Italian, Japanese, Korean, Spanish, Portuguese, French). They exist in `prompt-layers/rewrite/samples/` but haven't been enumerated in this wiki yet. Worth a future ingest.

## Sources

- `raw/1-in-a-billion/backend/prompt-layers/rewrite/` (all 11 narrative-rewrite-XX.md files)
- `raw/1-in-a-billion/backend/prompt-layers/rewrite/samples/` (literary anchors)

Commits: `a6065909` · `026b8247`
