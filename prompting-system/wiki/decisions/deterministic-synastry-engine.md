---
title: Deterministic Synastry Engine (Charmaine & Mike)
type: decision
date: 2026-03-10
commit: fa8a327c
created: 2026-05-08
updated: 2026-05-08
tags: [decision, matching, deterministic, math-speaks-first]
---

# Deterministic Synastry Engine

**2026-03-10**, commit `fa8a327c`, *"feat: deterministic Western synastry engine replacing LLM-guessed compatibility scores."* The day math replaced LLM intuition.

## Before

Synastry scores were LLM-guessed. The model was asked to evaluate two charts and output dimensional scores. Results clustered between 60 and 80, regardless of the actual chart. False consensus dressed up as analysis.

## What changed

A 6-category deterministic engine (`synastryEngine.ts`, ~900 lines) replaced the LLM scoring entirely. Scores now feed in from:

- Orb-weighted cross-aspects
- House overlays (especially 4th, 5th, 8th, 7th, 10th)
- Sect (day / night chart distinction)

Six categories: **Sexual Chemistry, Emotional Security, Communication, Growth, Power Dynamics, Long-term Stability**. The LLM no longer scores; the LLM stays within ±15 of the computed value and writes prose around it.

## The validation case

Charmaine & Mike. Old approach: scores clustered 60-80. New approach: full 0-100 spread.

| Category | Old | New |
|---|---|---|
| Communication | ~70 | **32** |
| Growth | ~76 | **46** |
| Overall | ~70 | **56** |

The new scores were not flattering. They were *real*.

## Why

Destroy false consensus. *Math speaks first; the model listens.*

Matching is unforgiving. Wrong advice ruins lives. *32 / 100 is a real answer, not a sales tactic.* The deterministic turn was existential: LLMs are ornamental when they guess; computation is the skeleton.

## What it unblocked

Within 24 hours (March 11), four parallel engines were added: Vedic, Human Design, Gene Keys, Kabbalah. The verdict meta-engine (`verdictSynastryEngine.ts`) blends all five into 16 verdict categories. The whole "code → prompt symbiosis" pattern dates from here: Supabase + workers + LLM-as-narrator-of-computed-truth.

The principle pre-dates this commit: see [[apps/seeking-toxic-relationships]], whose Vedic toxicity engine (Rahu 25%, Saturn 15%, Mars 20%, etc.) introduced deterministic weighting in January 2026, before being abandoned with the Swift codebase.

## Connections

- [[topics/matching-algorithm]]
- [[apps/seeking-toxic-relationships]] (the conceptual ancestor)
- [[apps/admin-panel]] (where dispatch later became configurable)
- [[voices/western]] (the synastry side of Western)

## Sources

- `raw/1-in-a-billion/backend/src/services/synastryEngine.ts`
- `raw/1-in-a-billion/backend/src/scripts/shared/compatibilityScoring.ts`
- Commit `fa8a327c`
