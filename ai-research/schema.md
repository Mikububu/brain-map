---
title: ai-research schema
type: schema
updated: 2026-05-08
---

# ai-research schema

Domain: AI/ML research, papers, models, methods, researchers, labs, cross-cutting topics.

This sub-wiki is the **fully-scaffolded template**. Use it as a model when promoting `work-notes/` or `reading-list/` from skeleton to full schema.

## Layout

```
ai-research/
├── schema.md            # this file
├── raw/                 # source materials (PDFs, exported markdown, html dumps, symlinks)
└── wiki/
    ├── index.md         # catalog of all pages, grouped by type
    ├── log.md           # append-only ingest/query/lint log
    ├── papers/          # one page per paper
    ├── models/          # one page per model or architecture
    ├── concepts/        # techniques, ideas, methods, definitions
    ├── people/          # researchers, authors
    ├── organizations/   # labs, companies, universities
    └── topics/          # cross-cutting summaries (e.g. "scaling-laws")
```

## Page types

### `papers/<arxiv-id-or-slug>.md`
Frontmatter: `title`, `type: paper`, `authors: [...]`, `venue`, `year`, `arxiv` (id or url), `created`, `updated`, `tags`.
Body sections (in order):
- `## TL;DR`, your 2-3 sentence summary in plain English. Not the abstract.
- `## Key ideas`, bulleted list of contributions.
- `## Method`, short walk-through. Math optional but welcome.
- `## Results`, what worked, on which benchmarks.
- `## Connections`, `[[wikilinks]]` to related papers, concepts, models, people.
- `## Sources`

### `models/<model-slug>.md`
Frontmatter: `title`, `type: model`, `org`, `released: YYYY-MM`, `parameters` (e.g. `7B`), `tags`.
Body: `## Architecture`, `## Training`, `## Capabilities`, `## Notes`, `## Sources`.

### `concepts/<concept-slug>.md`
Frontmatter: `title`, `type: concept`, `tags`.
Body: `## Definition`, `## Why it matters`, `## Examples` (linking to papers/models that use it), `## Related` (`[[wikilinks]]`), `## Sources`.

### `people/<name-slug>.md`
Frontmatter: `title`, `type: person`, `affiliation`, `tags`.
Body: `## Bio` (1-3 sentences), `## Notable work` (linking to papers/models), `## Sources`.

### `organizations/<org-slug>.md`
Frontmatter: `title`, `type: org`, `kind: lab | company | university`, `tags`.
Body: `## What they do`, `## Notable work`, `## People` (`[[wikilinks]]`), `## Sources`.

### `topics/<topic-slug>.md`
Frontmatter: `title`, `type: topic`, `tags`.
Body: `## Summary`, `## Key papers`, `## Key concepts`, `## Open questions`, `## Sources`.
Topics are written by hand or filed from queries. They are the highest-leverage pages for compounding.

## Routing for this sub-wiki

Anything ML/AI/statistics/research-flavored belongs here. Borderline cases:

- An *introductory* article about LLMs for a general audience → `reading-list/`.
- A paper that touches both AI and your work → here, with a `[[wikilinks]]` to the relevant `work-notes/projects/<x>` page.

## Symlink mappings

A table of what's symlinked into `raw/`. Update on every Step-3-style symlink.

| Symlink path                         | Real path                       | Created    | Notes |
| ------------------------------------ | ------------------------------- | ---------- | ----- |
| _none yet_                           |                                 |            |       |

To add a mapping:
```
ln -s <absolute-real-path> raw/<symlink-name>
```
then record it in the table above so future sessions know where things point.
