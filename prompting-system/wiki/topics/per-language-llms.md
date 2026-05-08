---
title: Per-Language LLM Selection
type: topic
created: 2026-05-08
updated: 2026-05-08
tags: [topic, llm, language, layer-3, native-generation, admin-panel]
---

# Per-Language LLM Selection

The LLM choice is not one model. It's a **per-language model dispatch**, set in the admin panel and tunable per language and per app.

## The principle

[[topics/layer-3-rewrite|Layer 3]] does not translate. The reading is **generated natively** in the target language. The English text is not a source the model translates from; it's a reference structure the model writes *around* in the user-selected language.

> "The different LLMs correspond to the different languages in the app, because layer 3 is written in the language the user selects. It isn't translated."

This means the LLM that writes the Hindi reading must actually write in Hindi well. The one that writes Japanese must write Japanese well. **Translation-quality models are not the same as native-generation-quality models.** A model that translates fluently can still produce flat, foreign-feeling prose.

## The hardest case: Vedic vocabulary in non-Romance languages

> "The challenge arises with a Vedic reading, which has its own specific vocabulary that applies only to that reading. How do you write this in Japanese or Korean?"

[[vedic]]'s vocabulary is largely Sanskrit-rooted (graha names, nakshatra, dasha, varna, neecha, etc.). In Romance and Germanic languages, the borrowing is usually clean (the words sit comfortably as foreign-but-readable terms). In **Japanese and Korean**, the words must be one of:

- Katakana / Hangul-transliterated (foreign-looking, sometimes meaning-thin)
- Kanji-equivalent-substituted (carries semantic weight but may shift meaning)
- Paraphrased entirely (faithful in spirit, loose in nominal precision)

Each option changes the texture differently. The "right" model for Japanese is the one whose default disposition matches the *texture* the builder wants. This is what drove the deep-research phase.

> "I did deep research on which LLM writes best for Japanese and which for Chinese. This is why we explored different LLMs in depth."

## The current dispatch (as of 2026-05-08)

> "For now, I mostly use Sonnet, but I can change all of this in my admin panel, and I'm open to further refinements."

The [[apps/admin-panel|admin panel]] declares **13 dispatchable models** and **4 control layers**.

### The 13-model palette

`claude` (Sonnet, default), `opus` (Claude Opus), `qwen-plus` (1M context), `deepseek` (V4 Pro), `deepseek-reasoner` (R1), `kimi`, `glm-5-turbo`, `gpt-5.1`, `openai-direct`, `mistral-medium`, `mistral-large`, `qwen-erotic` (self-hosted Qwen3-30B on RunPod), `qwen-72b-erotic` (self-hosted Qwen2.5-72B on RunPod).

The last two are the user's own [[topics/qwen3-research|RunPod-hosted Qwen3 fine-tunes]].

### The 4 control layers (Supabase `api_keys` table)

1. **`active_paid_llm_provider`** , global fallback (default: `claude`)
2. **`advanced_llm_routing`** , per-language matrix keyed by `en, de, es, fr, zh, ja, ko, hi, pt, it, ru`
3. **`final_verdict_llm_provider`** , hard override for verdict generation only
4. **`layer2_llm_provider`** , hard override for digest, trigger, writing layer

Each language inherits the global provider unless explicitly overridden.

The admin panel is the single point of truth for this dispatch. Changes propagate without code edits.

## Why this is one of the most expensive choices

The model selection is one of the architecturally most consequential choices, and one of the most invisible. The user does the research per language, picks the best model, and every reading inherits that choice. A different choice would produce a *measurably* different reading, both texturally and semantically.

The pairing with [[topics/language-anchoring|native voice anchors per language]] (Osho for Hindi, Pelevin for Russian, Yu Hua for Mandarin, etc.) makes the philosophy explicit: **avoid English-bias at every layer**.

A Hindi reading should not feel like an English reading translated. It should feel like Osho writing, in a model that writes Hindi like Hindi, not like English-with-Hindi-words.

## Open

- The exact per-language model assignments (which LLM for Japanese vs. Korean vs. Mandarin vs. Hindi vs. Russian) are not yet enumerated in this wiki. They live in the admin panel database. Worth a future ingest if the user wants the dispatch table mirrored here.
- The user is *"open to further refinements."* This is an active research thread, not a settled allocation.

## Connections

- [[topics/layer-3-rewrite]] (the layer this dispatch operates on)
- [[topics/language-anchoring]] (the literary anchor side; this page is the model side)
- [[topics/uncensored-llms]] (the special case where DeepSeek replaces Sonnet)
- [[vedic]] (the hardest test case for cross-language vocabulary)
- 1-in-a-Billion admin panel (`Mikububu/1-in-a-billion-admin`, the dispatch UI)

## Sources

- User testimony, 2026-05-08
- Backend code (admin panel + per-language model selection in the workers; not enumerated here)
