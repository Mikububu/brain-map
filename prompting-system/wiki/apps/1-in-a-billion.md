---
title: 1 in a Billion
type: app
created: 2026-05-08
updated: 2026-05-08
tags: [app, canonical, engine]
---

# 1 in a Billion

The main app. The canonical engine. The other three apps are forks of what's built here.

## What it is

A long-narrative astrological reader. Five systems ([[western]], [[vedic]], [[kabbalah]], [[gene-keys]], [[human-design]]), each in three modes (individual, synastry, incarnation). Long-form prose plus a music layer per system. Eleven languages.

## Tonal posture

**Literary consciousness-noir.** Astrology as scaffolding for literature, never the surface. The reader should feel *seen*, not analysed, not diagnosed. Tenderness over reverence when they clash.

## Voices in use

| Voice | Modes available |
|---|---|
| [[western]] | individual + synastry + incarnation |
| [[vedic]] | individual + synastry + incarnation |
| [[kabbalah]] | individual + synastry + incarnation |
| [[gene-keys]] | individual + synastry + incarnation |
| [[human-design]] | individual + synastry + incarnation |

This is the only app where all five voices run in all three modes.

## Architecture

- **Three composition layers**: System (terminology + depth model) → Voice (narrator consciousness) → Layer 3 (literary rewrite per language)
- **Compute first, write second**: Swiss Ephemeris computes the chart; DeepSeek writes; Layer 3 rewrites in target language with a native literary voice anchor
- **Eleven language anchors** (Osho for Hindi, Pelevin for Russian, Yu Hua for Mandarin, etc.)
- Backend: Hono on Fly. Frontend: Expo / React Native. Supabase + RevenueCat.

## Origin

- First commit: **2026-01-07** (`f486164f`, "Complete song generation pipeline implementation")
- V2 architectural rewrite: **2026-02-18** (`af0553d2`, "V2 prompt-layer overhaul")
- ~243 total commits as of May 8, 2026
- Codebase folder: `1-in-a-billion-v2/`
- GitHub repo: `Mikububu/1-in-a-billion-paradise` (created 2026-01-08)

The v2 rewrite was a **voice architecture overhaul on top of an existing engine**, not a foundation. See [[topics/january-foundation]] for the 6-week period that came before.

## Why this app exists

Two reasons, in the builder's own words:

1. **The yoga clients.** *"For yoga, I always have a client I analyze months before the project starts, and I consult real astrologers. I paid real people for Vedic astrology and for Gene Keys, among others, and their analyses always took forever and cost a lot of money."* The app productises something the builder already did manually: deep, multi-system astrological reading as the foundation of working with someone.

2. **The name.** *"A girlfriend once called me 'one in a billion', until she didn't call me that anymore."* Borrowed, with self-awareness, from a relationship that ended.

The yoga work and the name together name the deeper frame: a tool the builder wished existed when he was paying others to do it, carrying the weight of the way someone he loved once saw him.

## Six arcs that shaped it

- **Feb 18** — V2 prompt-layer foundation (`af0553d2`)
- **Feb 16-18** — Incarnation Zone Contract established for [[western]]
- **Mar 10** — Vocabulary reversal for [[kabbalah]] and [[gene-keys]] (`c1abc2de`)
- **Mar 21** — Layer 3 reframed as ghost-writer; Hellenistic merged into Western
- **Mar 28** — Native-script voice anchors per language
- **Mar 30** — Music prompts standardised, simplified

## What's particular

- The canonical voice for every system lives here; everywhere else is a fork
- Tenderness over reverence (the dialectical opposite of [[apps/unhinged|Unhinged]])
- The phrase *"The reader should feel SEEN, not analysed, not diagnosed"* originates here

## Sources

- `raw/1-in-a-billion/backend/prompt-layers/style/voice-architecture-all-systems.md`
- `raw/1-in-a-billion/backend/prompt-layers/rewrite/narrative-rewrite-en.md`
- All five voice pages in this wiki
