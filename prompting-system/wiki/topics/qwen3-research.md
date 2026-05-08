---
title: Qwen3 Research (Self-Hosted Uncensored)
type: topic
created: 2026-05-08
updated: 2026-05-08
tags: [topic, llm, qwen3, runpod, self-hosted, uncensored, infrastructure]
---

# Qwen3 Research

Two repos. One thesis: **self-host uncensored inference on owned infrastructure** so the engine doesn't depend on what frontier providers will or won't write.

## What Qwen3 is and why these repos exist

Qwen3 is Alibaba's open-weight model family. Unlike Claude or GPT, the weights are downloadable; the user can deploy quantized variants on owned GPUs. The HuggingFace ecosystem hosts uncensored fine-tunes ("abliterated-erotic" variants) that no API provider will host. The user maintains his own variants under `forbiddenmichael/*` on HuggingFace.

These two repos package those variants for production use:

| Repo | Purpose | Status |
|---|---|---|
| `qwen3-tts-service` | Qwen3-TTS-12Hz-0.6B for text-to-speech | Functional, low usage |
| `qwen3-llm-serverless` | Qwen3-30B-A3B (and 72B) AWQ-Int4 LLM completions | **Functional, integrated as fallback** |

## qwen3-llm-serverless

A RunPod serverless handler running **Qwen3-30B-A3B AWQ-Int4** quantized inference. Uses **vLLM 0.10.2 with the V0 engine forced** (`VLLM_USE_V1=0`), because vLLM 0.11.0+ removed the V0 engine and the V1 EngineCore subprocess hits `/dev/shm` limits on RunPod.

**Critical insight from the diffs**: there was a multi-day debugging battle (March 30 to April 1) figuring out the vLLM V0/V1 engine architecture. The "nuclear" commit `53b8ba5` (*"VLLM_USE_V1=0, fall back to V0 engine, no EngineCore at all"*) is the moment the problem was solved.

The handler is OpenAI-message-compatible. From [[apps/1-in-a-billion]]'s backend, this Qwen3 service is called as `qwen-erotic` (30B) or `qwen-72b-erotic` (72B), both selectable in the [[apps/admin-panel|admin panel]].

## qwen3-tts-service

Smaller scope. Wraps **Qwen3-TTS-12Hz-0.6B-CustomVoice** (a 600 MB TTS model) as a RunPod serverless handler. Input: text + language + speaker + optional instruction prompt. Output: WAV as base64.

Used as a **non-English TTS fallback** when MiniMax is unavailable. Documented in the app's `CAPACITY_AND_PROVIDER_ROUTING.md`.

## What worked

- **Lazy model loading** (`a340efb`, March 31). Defer model init until first request, fires the RunPod heartbeat in time, prevents 60-second worker-kill timeout.
- **vLLM 0.10.2 + V0 engine pin**. The only stable combination for the AWQ-Int4 quantized 30B-A3B model on RunPod's hardware.
- **Pre-loaded model in Dockerfile** (TTS service). Avoids download-during-cold-start delays.
- **OpenAI-compatible interface**. Drops in to 1-in-a-billion-v2's existing provider abstraction with no code changes.
- **`MODEL_ID` env var** (`a5f54d6`). One handler, multiple models. Run any HuggingFace model by changing the env.
- **Custom HuggingFace variants** (`forbiddenmichael/*`). Self-hosted abliterated-erotic Qwen3 variants. No rate-limiting, no censorship.

## What didn't (or what's incomplete)

- **vLLM version brittleness**. 0.10.2 works; 0.11.0+ broke things (V0 engine removed). Pinning is a dead end when other features need newer vLLM.
- **TTS service: low active usage**. Functional but rarely routed (only when language is non-English AND MiniMax is unavailable). Built for resilience, not daily traffic.
- **Repetition penalty tuning** (`605b39e`). Output quality issues in some sampling configurations; ongoing tuning.
- **Cost and cold starts**. RunPod is GPU-backed and pay-per-second. Cold starts on a 30B model are slow. This is why OpenRouter + DeepSeek remains the **primary** uncensored path; Qwen3 is the **fallback**.

## Reconciliation with the user's stated experience

The user's earlier testimony: *"When I tried to use a RunPod server, it didn't work out, so for now I've surrendered to using OpenRouter and DeepSeek."*

The git history says something more nuanced: **the RunPod work succeeded and is live in production**, but as a fallback rather than the primary day-to-day. The phrase *"didn't work out"* probably means *"didn't become my daily driver,"* not *"never worked."*

The actual three-tier uncensored stack:

1. **Primary**: OpenRouter + DeepSeek (American routing). Cheap, fast, predictable.
2. **Fallback**: Self-hosted Qwen3-30B and Qwen2.5-72B-Erotic on RunPod (this work). Used when DeepSeek is rate-limited or wrong-quality for the language.
3. **Aspirational**: A stable owned-infrastructure local node. Blocked by the user's travel pattern.

## Pivotal commits

| Date | Repo | Move |
|---|---|---|
| 2026-03-17 | `qwen3-tts-service` | Initial RunPod handler with Fly.io deployment, model pre-loaded |
| 2026-03-30 | `qwen3-llm-serverless` | Baseline LLM handler (Qwen3-30B-A3B AWQ-Int4) |
| 2026-03-31 | `qwen3-llm-serverless` | **Lazy model loading** to fire heartbeat before init |
| 2026-04-01 07:50 | `qwen3-llm-serverless` | **`VLLM_USE_V1=0` "nuclear" V0-engine fallback** |
| 2026-04-01 14:57 | `qwen3-llm-serverless` | vLLM 0.10.2 pinned + sync LLM class |
| 2026-04-01 19:40 | `qwen3-llm-serverless` | `<think>` block stripping + thinking-mode toggle |
| 2026-04-01 20:08 | `qwen3-llm-serverless` | `MODEL_ID` env var (model-agnostic handler) |

## Connections

- [[topics/uncensored-llms]] (the broader research thread; this is its self-hosted limb)
- [[topics/per-language-llms]] (qwen-erotic and qwen-72b-erotic appear in the dispatch palette)
- [[apps/admin-panel]] (where these models are switched in)
- [[apps/1-in-a-billion]] (where the integration lives, 126 references in the codebase)

## Sources

- `~/Desktop/my Iphone apps/1-in-a-billion/qwen3-tts-service/{handler.py, Dockerfile, fly.toml}`
- `~/Desktop/my Iphone apps/1-in-a-billion/qwen3-llm-serverless/{handler.py, Dockerfile, entrypoint.sh}`
- HuggingFace: `forbiddenmichael/*` (the user's abliterated-erotic Qwen3 variants)

Commits: `37c9ef1` · `ff5924c` · `a340efb` · `53b8ba5` · `1cbf569` · `adbd5e0` · `a5f54d6` · `67e5a07` · `605b39e` · `1f732a7`
