---
title: Native-Script Voice Anchors (Hindi → Osho)
type: decision
date: 2026-03-28
commit: a6065909
created: 2026-05-08
updated: 2026-05-08
tags: [decision, language, anchors, osho, pelevin, yu-hua]
---

# Native-Script Voice Anchors

**2026-03-28**, commits `a6065909` (*"rewrite samples: switch ru/hi to native-script source texts"*) and `026b8247` (*"rewrite: switch Hindi sample to Osho voice anchor"*). The day English literary bias was explicitly rejected for non-English readings.

## Before

Layer 3 sample anchors were English-translated source texts. A Hindi reading anchored implicitly to whatever great writer the model defaulted to (often someone like García Márquez), filtered through translation. The result: Hindi prose that sounded like translated magical realism.

## What changed

Sample texts in `prompt-layers/rewrite/samples/` switched from English-translated to **native-script source texts**. New voice-anchor pairings:

| Language | Anchor |
|---|---|
| Hindi | **Osho** |
| Russian | **Viktor Pelevin** |
| Mandarin | **Yu Hua** |

Each language now reads with its own native literary voice as the implicit narrator.

## Why

Avoid English literary bias at every layer. A Hindi reading anchored to García Márquez sounds like translated magical realism. A Hindi reading anchored to Osho sounds like Osho.

The reader's literary recognition should not be borrowed; it should be native. The work is to make the reading feel like *that writer writing in that language*, not like an English-language reading translated.

## The Vedic-vocabulary problem

This decision is paired with [[topics/per-language-llms|per-language LLM dispatch]]. Sanskrit-rooted Vedic vocabulary (graha, nakshatra, dasha, neecha) sits cleanly in Romance and Germanic languages but requires katakana / Hangul transliteration, kanji-equivalent substitution, or paraphrase in Japanese / Korean. The right anchor and the right LLM together make the Vedic register translate without flattening.

## What it unblocked

[[topics/language-anchoring|The language-anchoring thesis]]. Treats each of the 11 languages as its own register, not a translation target. Sets up the per-language LLM choice as a meaningful axis: which model writes Hindi like Hindi, not English-with-Hindi-words.

## Connections

- [[topics/language-anchoring]]
- [[topics/per-language-llms]]
- [[topics/layer-3-rewrite]]
- [[decisions/ghost-writer-reframe]] (the prior move, one week earlier, that made this move sensible)

## Sources

- `raw/1-in-a-billion/backend/prompt-layers/rewrite/samples/` (the literary anchors)
- `raw/1-in-a-billion/backend/prompt-layers/rewrite/narrative-rewrite-hi.md`
- `raw/1-in-a-billion/backend/prompt-layers/rewrite/narrative-rewrite-ru.md`
- Commits `a6065909` · `026b8247`
