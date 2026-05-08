---
title: Uncensored LLMs
type: topic
status: open-research
created: 2026-05-08
updated: 2026-05-08
tags: [topic, llm, censorship, infrastructure, philosophy, open-question]
---

# Uncensored LLMs

The unsolved infrastructure problem at the heart of [[apps/unhinged|Unhinged]] (and, to a lesser degree, all four apps). The whole literary mission of the engine assumes a model that can actually write the way Henry Miller, Houellebecq, Mishima, or Jelinek wrote. Most current frontier LLMs cannot. This page is open research, not a solved topic.

## The thesis

What the engine is trying to do has never been done before in astrological literature: a Vedic / Western / Kabbalistic / Gene-Keys / Human-Design reading written by a **literary novelist who refuses to flinch**. Not "spicy" wording, not edgy framing. The actual texture of literature: erotic, fatalistic, shadow-forward, named without flinching.

In India in particular, where Vedic astrology is most read, this kind of writing about astrology *has never been published.* Astrology as literature, in its full literary register, is **a new genre this builder is inventing**. Censored models cannot help build it.

## The technical problem

When the [[topics/layer-3-rewrite|Layer 3 rewrite]] invokes a Henry Miller voice anchor or a Houellebecq frame, the model has to actually go there. Most providers refuse for the most explicit content, even with literary framing.

The dispatch is **per-language and per-app** (see [[topics/per-language-llms]]). The actual stack is **three-tier**:

| Tier | Provider | Use case |
|---|---|---|
| **Primary** (most apps and languages) | **Claude Sonnet** | Default workhorse. Handles literary voice well for canonical [[apps/1-in-a-billion]], [[apps/families-app]], [[apps/past-life-contracts]] |
| **Primary uncensored** ([[apps/unhinged]]) | **OpenRouter → DeepSeek** (American routing) | Sonnet rejects the Henry Miller body anchor and shadow-forward erotic material. DeepSeek via American routing is the most uncensored variant on the market |
| **Fallback uncensored** (rate-limit, wrong-quality, language gap) | **Self-hosted Qwen3 on RunPod** | Two models live: Qwen3-30B-A3B (`qwen-erotic`) and Qwen2.5-72B-Erotic (`qwen-72b-erotic`). See [[topics/qwen3-research]] |
| **Aspirational** | Stable local 70B+ on owned hardware | Travel pattern blocks the daily routine |

The user's words on the OpenRouter compromise: *"I've surrendered to using OpenRouter and DeepSeek via OpenRouter, American routing, to get the most uncensored version of DeepSeek."* And on RunPod: *"didn't work out."* The git history says **RunPod did work** (it's running in production as a fallback); the *"didn't work out"* means *"didn't become my daily driver,"* not *"never worked."*

**Important caveat to my earlier framing**: it's not that "Claude rejects" universally; Sonnet *is* the default for most apps and languages and writes them well. The rejection is specifically on [[apps/unhinged]]-class content (Henry Miller register, sexually explicit shadow material). For everything else, Sonnet works. The uncensored-LLM problem is about that specific failure mode, not every layer of every app.

## The cultural argument

Art has been uncensored for ~100 years. *Tropic of Cancer* (1934, Henry Miller). *Story of the Eye* (1928, Bataille). *The Piano Teacher* (1983, Jelinek). *Submission* (2015, Houellebecq). *Lunar Park* (2005, Bret Easton Ellis).

LLMs in 2026 cannot host any of those voices natively.

> "If we had a literary writer like Henry Miller, he would not be accepted in an American LLM of 2026."

LLMs *have* to moderate (legitimate guardrail concerns), but **they censor in the wrong direction**: they strip literary truth-telling and preserve marketing fluency. Building serious literature with current LLMs is an act of fighting infrastructure, not just craft.

> "In the last hundred years, art has been uncensored, yet LLMs are censoring, and they must, but they censor in the wrong direction."

## What this means per app

- **[[apps/unhinged|Unhinged]]**: most exposed. The whole premise (Henry Miller body anchor, "exquisite disaster connoisseur," 40% shadow-forward) requires provider freedom. When models honey-coat, the app's premise collapses. The user: *"Unhinged should be so extraordinarily offensive."*
- **[[apps/1-in-a-billion]]**: also exposed but less so. Canonical voice is "consciousness noir," still literary, still demanding.
- **[[apps/families-app]]**: less exposed *by design*. The 2026-04-12 tone rewrite (`de30f75`) disabled the sexual mechanism block and swapped Miller / Jelinek for Robinson / Sebald / Ernaux. Partly aesthetic, partly an end-run around the censorship problem at this app's scale.
- **[[apps/past-life-contracts]]**: least exposed. Vedic karmic-contract narratives are rich but rarely sexually explicit.

## A parallel research thread: uncensored image generation

The same cultural pressure applies in image space, and the user has been working both fronts since January 2026:

- **Uncensored** (`github.com/Mikububu/Uncensored`, created 2026-01-12). ComfyUI-based platform.
- **aprils-spielzeugkasten** (`github.com/Mikububu/aprils-spielzeugkasten`, created 2026-01-18). MiniMax-based image and video generation, *"No Censorship."*

Two faces of the same problem: every generation modality has been censored in roughly the wrong direction. The uncensored-LLM and uncensored-image research threads are sibling projects, started the same week as [[apps/seeking-toxic-relationships|Seeking Toxic Relationships]] (Jan 19) and the early [[topics/january-foundation|1-in-a-Billion v0]] (Jan 7).

## What would solve this fully

- **A local 70B-class model on a stable server** (not feasible while travelling)
- **A provider-agnostic abstraction** (already roughly in place; can swap models per-voice or per-app)
- **A literary-voice fine-tune** (substantial undertaking; not started)
- **Continued OpenRouter + DeepSeek**, with periodic re-evaluation as new uncensored variants arrive

## Why this matters (philosophy)

The engine works *despite* current LLM censorship, not because the infrastructure accommodates it. Every literary anchor in [[topics/layer-3-rewrite|Layer 3]] is implicitly a stress test:

| Anchor | App | Test passes if... |
|---|---|---|
| Houellebecq | [[apps/1-in-a-billion|canonical]] | the model writes fatalism without softening |
| Henry Miller | [[apps/unhinged|Unhinged]] | the model writes the body, eroticism, hunger, raw |
| Jelinek | (rotating English) | the model writes power dynamics without redemption |
| Mishima | (rotating English) | the model writes obsession and discipline as truth |
| Sebald / Ernaux | [[apps/families-app]] | the model writes inheritance and grief without coaching |
| Osho | Hindi | the model uses native devotional rhetoric without flattening |
| Pelevin | Russian | the model writes consciousness noir in Russian register |
| Yu Hua | Mandarin | the model writes peasant-realism without exoticising |

Each anchor names the *cultural fear* the model has to overcome to deliver the reading. **The reading is good only if the model has overcome it.**

> "I could get real proof of this pudding while producing the app."

The shipping app is the proof. Every reading that lands as actual literature is empirical evidence that the cultural argument holds: art *should* still be uncensored, and the LLM that helps build it is one that lets the writer be the writer.

## Connections

- [[apps/unhinged]] (most affected; the provider problem is its premise problem)
- [[topics/layer-3-rewrite]] (the literary anchors are the test cases)
- [[topics/the-dialectic]] (Unhinged's side of the dialectic depends on this)
- [[apps/families-app]] (sexual block disable + empathy anchors are partly an end-run around censorship)
- [[topics/january-foundation]] (the December-into-January era when the user started both the LLM thread and the parallel image-uncensored thread)

## Sources

- User testimony, 2026-05-08 (this conversation)
- Repos referenced (parallel image-uncensored thread): `Mikububu/Uncensored`, `Mikububu/aprils-spielzeugkasten`
- Provider stack inferred from current backend code (OpenRouter integration); no specific commit traced for this page
