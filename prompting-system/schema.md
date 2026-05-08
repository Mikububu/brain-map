---
title: prompting-system schema
type: schema
updated: 2026-05-08
---

# prompting-system schema

Domain: the philosophical journey of building the four-app suite, **1 in a Billion** (the canonical engine), **Unhinged** (its dialectical opposite), **Past-Life Contracts** (Vedic-only contract narratives), **Families-app** (family-myth scope).

> Naming note: "1 in a Billion" is the app. `1-in-a-billion-v2/` is the v2 codebase folder name (a v2 architectural rewrite). Use the app name "1 in a Billion" in prose; use the folder path only inside `Sources` lists or file references. This sub-wiki is a **mind-map**, not a reference manual. Its purpose is to make the philosophy of what was built visible, including the dead ends, the dialectics, the gap between intent and execution.

## Layout

```
prompting-system/
├── schema.md                   # this file
├── raw/                        # symlinks to the four app repos (read-only)
│   ├── 1-in-a-billion       →  ~/Desktop/my Iphone apps/1-in-a-billion/1-in-a-billion-v2
│   ├── unhinged             →  ~/Desktop/my Iphone apps/Unhinged
│   ├── past-life-contracts  →  ~/Desktop/my Iphone apps/Past-life-contracts
│   └── families-app         →  ~/Desktop/my Iphone apps/Families-app
└── wiki/
    ├── index.md
    ├── log.md
    ├── voices/                 # one per astrological system
    ├── apps/                   # one per tonal fork
    ├── topics/                 # cross-cutting themes
    ├── decisions/              # pivotal commits / philosophical moves
    └── experiments/            # things tried that didn't work
```

## Page types

- **`voices/<system>.md`**, Western, Vedic, Kabbalah, Gene Keys, Human Design. The narrator. The metaphor world. The journey from first commit to current state. Order of construction: Western → Vedic → Kabbalah → Gene Keys → Human Design (the methodological order).
- **`apps/<app>.md`**, 1 in a Billion, Unhinged, Past-Life Contracts, Families-app. Each as a tonal fork of the same engine.
- **`topics/<slug>.md`**, cross-cutting themes: the engine itself, layer-3 rewrite, the Unhinged↔1-in-a-billion dialectic, music prompts, language anchoring, the matching algorithm.
- **`decisions/<slug>.md`**, pivotal moments in the build. Each carries a commit hash + date as evidence.
- **`experiments/<slug>.md`**, things tried that didn't work, were abandoned, or hit the gap between intent and what the AI could execute.

## Method (read-only)

Source-of-truth for evolution is **git history** of the four app repos. Walk diffs, not just commit messages. Quote prompt text where it makes the philosophical move visible. Treat dead ends as first-class material, they are part of the journey, not noise.

No file in `raw/` is ever modified. `git log`, `git show`, `git diff` only.

## Routing for this sub-wiki

Anything related to the prompting / voice / system architecture of the four-app suite, including its philosophy and history. The four backend repos and their git history are the corpus. Other sub-wikis exist for unrelated material (`ai-research/`, `work-notes/`, `reading-list/`).
