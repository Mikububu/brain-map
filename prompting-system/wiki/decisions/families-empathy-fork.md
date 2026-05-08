---
title: The Families Empathy Fork (Sexual Block Disabled)
type: decision
date: 2026-04-12
commit: de30f75
created: 2026-05-08
updated: 2026-05-08
tags: [decision, families, empathy, anchors, scope-narrowing]
---

# The Families Empathy Fork

**2026-04-12**, commit `de30f75`, *"Total tone rewrite: empathetic family philosophy across all layers."* The day [[apps/families-app|Families-app]] became its own thing.

## Before

Families-app had been forked from canonical [[apps/1-in-a-billion]] two days earlier (`9f067e7`, 2026-04-10). At that moment, it inherited the canonical voice wholesale: Henry Miller and Jelinek as Layer 3 anchors, the sexual-mechanism block enabled, the consciousness-noir register intact.

That voice doesn't fit family-myth scope.

## What changed

A tonal rewrite across all layers:

- **Anchor swap**: Henry Miller and Elfriede Jelinek removed. Replaced with **Marilynne Robinson, W.G. Sebald, Annie Ernaux**. The literary register shifts from libertine / power-dynamics to grief / inheritance / attachment.
- **`buildSexualMechanismBlock()` disabled**. The block that injects sexual mechanism analysis into individual readings is *off* in Families. Not censored, structurally disabled.
- **Klipoth reframe** (in [[voices/kabbalah|Kabbalah]] specifically): from *"protective shell that outlived its purpose"* to *"shell that became the self"*. Tikkun reframed from generic recurring-loop to *"repetition signature in the body, in the reflexes"*.

## Why

A family is not a couple. A family is not an individual. The transgenerational scope demands tenderness directed at attachment, lineage, role pressure, and inherited grief, not erotic obsession. Different scope, different voice register.

This is also partly a way to *avoid* the [[topics/uncensored-llms|uncensored-LLM problem]]: family-myth tone runs on Sonnet without provider conflict. The empathy-anchor swap and the sexual-block disable together let Families-app live at the soft end of the voice spectrum without the friction Unhinged generates.

## What it unblocked

[[apps/families-app|Families-app]]'s distinct identity in the four-app constellation. The "third position" beyond the canonical-vs-Unhinged dialectic: not a tonal fork, but a **scope narrowing** (1 to 4 people as one organism rather than the individual or the dyad).

The unique structural commitments that distinguish Families-app from canonical, *no section headers*, *all members named throughout*, the *ghost field* for deceased members, the *word-count scaling formula* (8000 base + 1200 per member + 600 per pair), all consolidate after this commit (especially in `0ec0017` two days later: *"Rewrite reading pipeline: 1 job = 1 system = 1 family document"*).

## Connections

- [[apps/families-app]]
- [[topics/four-app-constellation]] (the family-myth position)
- [[voices/kabbalah]] (where the Klipoth-as-self reframe lives)

## Sources

- `raw/families-app/Families-app-src/backend/prompt-layers/style/`
- `raw/families-app/Families-app-src/backend/src/prompts/structures/family.ts`
- Commit `de30f75`
