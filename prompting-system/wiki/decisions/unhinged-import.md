---
title: The Unhinged Import (The Dialectical Fork is Born)
type: decision
date: 2026-04-08
commit: 6b4363e
created: 2026-05-08
updated: 2026-05-08
tags: [decision, unhinged, dialectic, fork]
---

# The Unhinged Import

**2026-04-08**, commit `6b4363e`, *"chore: initial import of toxic-app workspace."* The day the dialectical fork of the engine was created.

## The lineage at this moment

This is the second incarnation of the toxic-relationships idea. The first was [[apps/seeking-toxic-relationships]], a Swift / SwiftUI iOS app that ran from 2026-01-19 to 2026-02-12 before being abandoned. **56 days later**, the same concept was rebuilt on a completely different stack (Expo React Native + Hono backend), borrowing [[apps/1-in-a-billion]]'s engine wholesale.

## What changed

The `Unhinged/toxic-app/` workspace appeared. Most prompt files were *byte-identical* to the canonical 1-in-a-Billion at this moment. The divergence had not yet happened; the tonal differentiation came later in this same week (`9e6efbd` *"toxic-chic rewrite"*) and again on April 15 (the [[decisions/toxic-to-diagnostic-noir|fairytale-to-diagnostic-noir shift]]).

App.json already declared the rebrand: `name: "UNHINGED"`, `bundleIdentifier: "app.unhinged.toxic"`. The codebase folder kept the old name (`toxic-app/`); the App-Store-facing product was UNHINGED from day one. See [[topics/toxic-to-unhinged-rebrand]] for the full naming politics.

## Why

Build the dialectical opposite of the canonical engine using the *same* engine. The contrast (canonical = tenderness over reverence; Unhinged = provocation over reverence) proves the engine is **voice-shape-agnostic**. Same chart, same data, opposite reading.

This is not contradicting canonical. It's showing canonical is real (rather than an accident of voice).

## What it unblocked

The whole [[topics/the-dialectic|architectural dialectic]] becomes a feature, not a bug. The [[topics/four-app-constellation|four-app constellation]] becomes possible: canonical and Unhinged as the two tonal poles, [[apps/past-life-contracts]] and [[apps/families-app]] as the two scope-narrowings.

The April 15 prompt-tone shift (*"fairytale → diagnostic noir"*) and the April 18 launch readiness audit both happen downstream of this commit.

## Connections

- [[apps/unhinged]]
- [[apps/seeking-toxic-relationships]] (the abandoned predecessor)
- [[topics/the-dialectic]]
- [[topics/toxic-to-unhinged-rebrand]]
- [[topics/four-app-constellation]]

## Sources

- `raw/unhinged/toxic-app/app.json`
- `raw/unhinged/toxic-app/backend/prompt-layers/`
- Commit `6b4363e`
