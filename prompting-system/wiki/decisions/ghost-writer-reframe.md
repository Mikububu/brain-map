---
title: The Ghost-Writer Reframe (Layer 3 as Literature)
type: decision
date: 2026-03-21
commit: cf2e3d3b
created: 2026-05-08
updated: 2026-05-08
tags: [decision, layer-3, literature, ghost-writer]
---

# The Ghost-Writer Reframe

**2026-03-21**, commit `cf2e3d3b`. The day Layer 3 stopped sounding like edited model output and started sounding like literature.

## Before

Layer 3 was a translation / polish step. The prompts asked the model to "write a polished prose version" of the system narrative in the target language. The result was clean, lucid, a little flat. Translated novelist work, not novelist work.

## What changed

Layer 3 was reframed as a **ghost-writer task**: *"Write the masterpiece you never finished."*

Personas explicitly invoked:

- **Michel Houellebecq** (canonical, fatalism)
- **Yukio Mishima** (obsession, discipline as truth)
- **Gabriel García Márquez** (magical realism, family myth)
- **Elfriede Jelinek** (power dynamics without redemption)

The model is no longer "writing the polished version of someone else's draft." It is being addressed as one of these writers, finishing their unfinished masterpiece with the chart as material.

## Why

Stop sounding like AI. Start sounding like a human writer with a project. The reframe gives the model a *psychological frame* (a writer with an unfinished book; this is the chance to finish it) instead of a *task description* (rewrite this prose).

This is the move that turns Layer 3 from craft into art.

## What it unblocked

Every subsequent Layer 3 refinement: the [[decisions/native-script-voice-anchors|native-script anchors]] (Osho for Hindi, Pelevin for Russian, Yu Hua for Mandarin), the [[topics/layer-3-rewrite|fidelity rule]] (system mechanism must survive transformation), the [[apps/families-app|empathy-anchor swap]] (Robinson, Sebald, Ernaux replace Miller and Jelinek for the family register).

It also forces the [[topics/uncensored-llms|uncensored-LLM problem]]: the literary anchors *are* the test cases. Houellebecq, Miller, Jelinek are exactly the writers Sonnet refuses to channel for the most explicit content. The reframe surfaces the censorship problem because it raises the stakes.

## Connections

- [[topics/layer-3-rewrite]]
- [[topics/language-anchoring]]
- [[topics/uncensored-llms]]
- [[decisions/native-script-voice-anchors]] (the next move, one week later)

## Sources

- `raw/1-in-a-billion/backend/prompt-layers/rewrite/narrative-rewrite-en.md`
- Commit `cf2e3d3b`
