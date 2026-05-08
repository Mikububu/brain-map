# Brain Map

A personal knowledge base built with the [Karpathy LLM wiki pattern](https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f), opened as a vault in [Obsidian](https://obsidian.md/).

26 pages of philosophical mind-map covering the four-app suite by Michael Wogenburg ([Forbidden Yoga](https://forbidden-yoga.com/)): **1 in a Billion**, **Unhinged**, **Past-Life Contracts**, and **Families-app**. The wiki traces the December 2025 to May 2026 evolution of the prompting architecture, the five astrological narrator archetypes, the per-language LLM dispatch, the uncensored-LLM research thread, and the dialectic between the canonical and transgressive versions of the same engine.

## Start here

Open `prompting-system/wiki/START_HERE.md` for the recommended reading order.

## How to read it

1. Install [Obsidian](https://obsidian.md/) (free)
2. Clone this repo
3. In Obsidian, choose "Open folder as vault" and pick the cloned directory
4. Open `prompting-system/wiki/START_HERE.md`
5. Press `Cmd + G` (or `Ctrl + G` on Windows / Linux) for the graph view

## Layout

```
.
├── CLAUDE.md                       # top-level wiki conventions
├── ai-research/                    # template / starter sub-wiki
├── work-notes/                     # skeleton sub-wiki
├── reading-list/                   # skeleton sub-wiki
└── prompting-system/               # the main mind-map (26 pages)
    ├── schema.md
    └── wiki/
        ├── START_HERE.md
        ├── index.md
        ├── log.md
        ├── voices/                 # 5 narrator archetypes
        ├── apps/                   # 7 apps, including the canonical, the predecessors, and the admin
        └── topics/                 # 14 cross-cutting topic pages
```

## What's NOT in this repo

The `raw/` folders inside each sub-wiki are deliberately empty. Locally, they contain symlinks to the source material (the four app repos). Those source repos are private; this wiki does not redistribute their content. Path references in the `## Sources` section of each page point to those local raw/ symlinks for verification and won't resolve when the repo is cloned. They remain as evidence of where each finding came from.

## Conventions

- Markdown files with YAML frontmatter
- `[[wikilinks]]` between pages, resolved by Obsidian
- Each page begins at a single `# H1` derived from the frontmatter `title`
- Source attribution at the end of every page, with commit hashes where applicable
- No em-dashes (a stylistic preference of the author)

See `CLAUDE.md` (top-level) and `prompting-system/schema.md` (this sub-wiki) for the full conventions.

## Skill

A reusable Claude Code skill at `.claude/skills/voice-evolution-walk/SKILL.md` encodes the discipline used to build the voice pages. Future ingests of additional voice archetypes can invoke it.

## License

Personal knowledge base. No license. Reading, sharing the URL, and cloning for reference are fine. Please do not redistribute the prose or republish without permission.

## Author

[Michael Wogenburg](https://forbidden-yoga.com/), 2026.
