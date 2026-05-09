---
title: "Vedic Archive"
type: archive-hub
created: 2026-05-08
updated: 2026-05-08
tags: [vedic, archive, raw-source, no-interpretation]
---

# Vedic Archive

**The raw source material.** No interpretation. No summary. The actual file content and diffs, verbatim from git.

This is the research archive. Use these pages as primary sources when writing long documents about how Vedic developed.

For the chronological commit log with my annotations, see [[decisions/vedic-daily-ledger]]. For the synthesised mind-map, see [[voices/vedic]]. **This archive is the raw material those pages sit on top of.**

## Birth state (Jan 7 to Feb 18, 2026)

The earliest existence of Vedic in the codebase.

- [[vedic-archive/00-pre-v2-vedic-ts|00. Pre-v2 vedic.ts (Jan 7)]] — the v0 TypeScript module, 196 lines, the first appearance of any Vedic logic in the codebase. *"Adventures in Inner Space, Mahavidya wisdom, Aghori-tantra texture."*
- [[vedic-archive/01-vedic-individual-feb-16|01. vedic-individual.md (Feb 16)]] — the first markdown-prompt version of Vedic individual reading.
- [[vedic-archive/02-vedic-synastry-feb-16|02. vedic-synastry.md (Feb 16)]] — the first markdown synastry prompt.
- [[vedic-archive/03-vedic-incarnation-feb-18|03. vedic-individual-incarnation.md (Feb 18)]] — the Aghori-witness incarnation voice at birth, 213 lines.
- [[vedic-archive/04-vedic-voice-style-feb-18|04. style-guide-insert-vedic-voice.md (Feb 18)]] — the 388-line voice insert at first commit.
- [[vedic-archive/05-vedic-chart-digest-feb-18|05. vedic-chart-digest-v1.md (Feb 18)]] — the Layer 0 digest at first commit.

## Pivotal transformations (Mar 12 to Mar 22)

Full diffs at the most consequential commits.

- [[vedic-archive/06-mar-12-vamachara|06. Mar 12, `cd2e6f95` — Vamachara left-hand tradition interpretation]]
- [[vedic-archive/07-mar-15-pipeline-audit|07. Mar 15, `b20fba9e` — Vedic pipeline audit (spice, prompt, terminology)]]
- [[vedic-archive/08-mar-17-dharmic-archetype|08. Mar 17, `50be6c07` — Qualitative scores + dharmic archetype system]]
- [[vedic-archive/09-mar-18-layer-0|09. Mar 18, `623ba8e8` — Layer 0 digest wired into reading pipeline]]
- [[vedic-archive/10-mar-21-happiness-index|10. Mar 21, `2aef2407` — Ashtakuta tables fix + the Happiness Index]]
- [[vedic-archive/11-mar-22-gatekeeper|11. Mar 22, `4208c3ca` — Five-layer Vedic gatekeeper]]

## Current state (May 8, 2026)

Verbatim contents of the key Vedic files as they exist today.

- [[vedic-archive/12-current-vedic-individual|12. Current vedic-individual.md]]
- [[vedic-archive/13-current-vedic-incarnation|13. Current vedic-individual-incarnation.md]]
- [[vedic-archive/14-current-vedic-voice-style|14. Current style-guide-insert-vedic-voice.md]]
- [[vedic-archive/15-current-vedic-chart-digest|15. Current vedic-chart-digest-v1.md]]
- [[vedic-archive/16-current-vedic-music|16. Current vedic-music-prompt.md]]
- [[vedic-archive/17-current-vedic-overlay-music|17. Current vedic-overlay-music-prompt.md]]
- [[vedic-archive/18-current-vedic-synastry|18. Current vedic-synastry.md]]

## How to use this archive

The "long documents later" use case. To write about a specific transformation:

1. Read the *birth state* page for that file (00 to 05).
2. Read the relevant *pivotal transformation* diff (06 to 11).
3. Read the *current state* (12 to 18).
4. Compare. The story is in the delta, not in my prose.

The user has everything they need to write essays / a PhD / talk material about the Vedic evolution from these 18 raw source pages, without depending on my interpretation.

## What this archive is missing

- Commits with `Auto-deploy updates from desktop` messages are not given individual archive pages (no philosophical content). The [[decisions/vedic-daily-ledger]] lists them all chronologically, but the diffs are usually small / cosmetic.
- The Unhinged and Families-app variants of these files (where they exist) are not in this archive. They could be added if useful.
- TypeScript-side code changes (`vedicSynastryEngine.ts`, `vedicTrigger.ts`, etc.) are partially captured in the pivotal-commit diffs above when those commits touched them. Full per-file source archive of those files could be a future expansion.
