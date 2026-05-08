---
title: Admin Panel
type: app
status: control-surface
created: 2026-05-08
updated: 2026-05-08
tags: [app, control-surface, dispatch, infrastructure]
---

# Admin Panel

A Next.js dashboard that controls all four apps ([[apps/1-in-a-billion]], [[apps/unhinged]], [[apps/past-life-contracts]], [[apps/families-app]]) from one interface. The single point of truth for the [[topics/per-language-llms|LLM dispatch]] and a lot more.

## What it controls

- **LLM dispatch** (the most important): per-language model routing across 11 languages, plus three independent override layers
- **Prompt layers**: rewrite (Layer 3), system (Layer 2), style guides, digests, verdict synthesis, image generation, code-level prompts (trigger seeds, forbidden phrases)
- **Users**: browse, view job history, delete, track language preferences
- **Job pipeline**: monitor reading-generation jobs in real time; provider assignment per job; fallback reasons; completion times
- **Subscriptions and pricing**: dynamic API cost formulas; in-app purchase metadata (11 languages); tier configuration
- **Offers and coupons**: promotional codes, usage limits, checkout link generation
- **Push notifications**: broadcast to all or subscribed users; device counts by platform
- **Store publishing**: App Store and Google Play metadata (descriptions, screenshots, localised content) for all four apps

## The 13-model palette

The LLM Switcher UI declares these models, all dispatchable per-language:

| Model | Label |
|---|---|
| `claude` | Claude 4.6 Sonnet (default workhorse) |
| `opus` | Claude 4.6 Opus |
| `qwen-plus` | Qwen 3.5 Plus (1M context) |
| `deepseek` | DeepSeek V4 Pro |
| `deepseek-reasoner` | DeepSeek R1 |
| `kimi` | Kimi K2.5 |
| `glm-5-turbo` | GLM 5 Turbo |
| `gpt-5.1` | GPT-5.1 |
| `openai-direct` | OpenAI Direct |
| `mistral-medium` | Mistral Medium 3.1 |
| `mistral-large` | Mistral Large 3 |
| **`qwen-erotic`** | **Qwen3 30B Erotic (RunPod L40S), self-hosted uncensored** |
| **`qwen-72b-erotic`** | **Qwen2.5 72B Erotic (RunPod A100), self-hosted uncensored** |

The last two are the builder's own RunPod-hosted Qwen3 fine-tunes from [[topics/qwen3-research]]. Together with OpenRouter + DeepSeek, they form a three-tier uncensored stack.

## Four control layers (Supabase `api_keys` table)

1. **`active_paid_llm_provider`** , global fallback (default: `claude`)
2. **`advanced_llm_routing`** , per-language matrix (JSON keyed by `en`, `de`, `es`, `fr`, `zh`, `ja`, `ko`, `hi`, `pt`, `it`, `ru`)
3. **`final_verdict_llm_provider`** , hard override for verdict generation only
4. **`layer2_llm_provider`** , hard override for digest, trigger, writing layer

Each language inherits the global provider unless explicitly overridden in the matrix. Layer 2 and final-verdict overrides operate independently of the per-language matrix.

## Origin

- First commit: **2026-02-24** (`1449189`, *"Admin dashboard: studio control room UI with Supabase integration"*)
- GitHub: `Mikububu/1-in-a-billion-admin` (created 2026-01-14)
- Local: `~/Desktop/my Iphone apps/Admin-Panel/`
- Stack: Next.js + Supabase

## Pivotal commits

| Date | Move | What changed |
|---|---|---|
| 2026-03-15 | LLM switcher UI added | First model-selection page in admin sidebar |
| 2026-03-15 | DeepSeek-reasoner option | Reasoning variant available in dispatch |
| 2026-03-16 | Per-language matrix introduced | 1217-LOC change adds the dispatch table |
| 2026-03-16 | UI rewrite to language-based schema | Refactored from app-based to language-based |
| 2026-03-26 | Final-verdict override | Independent dropdown for verdict synthesis |
| 2026-04-01 | Qwen 72B Erotic added | 72B uncensored fine-tune on A100 |
| 2026-04-05 | Layer 2 override | Independent dropdown for digest / trigger / writing |
| 2026-04-12 | Multi-app DB switching | Unified all four app backends under one panel |

## Connections

- [[topics/per-language-llms]] (the dispatch this panel writes to Supabase)
- [[topics/uncensored-llms]] (the qwen-erotic entries are the self-hosted layer)
- [[topics/qwen3-research]] (the RunPod work backing the qwen-erotic options)
- [[apps/1-in-a-billion]], [[apps/unhinged]], [[apps/past-life-contracts]], [[apps/families-app]] (all four backends route through this panel)

## Sources

- `~/Desktop/my Iphone apps/Admin-Panel/app/llm-switcher/page.tsx` (430 lines, the main dispatch UI)
- `~/Desktop/my Iphone apps/Admin-Panel/app/api/admin/settings/llm/route.ts` (180 lines, Supabase upsert API)
- `~/Desktop/my Iphone apps/Admin-Panel/lib/projects.ts` (4-app project config)
- `~/Desktop/my Iphone apps/Admin-Panel/app/ai-settings/page.tsx` (8 prompt categories)

Commits: `1449189` · `a117c5d` · `550086e` · `1f95d4d` · `0a00286` · `7e48d67` · `ebb1ea2` · `8ac021c` · `4db46dd`
