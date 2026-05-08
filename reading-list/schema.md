---
title: reading-list schema
type: schema
updated: 2026-05-08
status: skeleton
---

# reading-list schema (skeleton)

Domain: general reading, articles, blog posts, books, podcasts, talks. Anything that isn't an ML/AI research artefact (which goes to [[ai-research/schema|ai-research]]) and isn't work-internal (which goes to [[work-notes/schema|work-notes]]).

> **Skeleton.** Basic shape only. On first ingest, propose page types and update this file. Use [[ai-research/schema]] as the reference template.

## Layout

```
reading-list/
├── schema.md
├── raw/                # articles (markdown/html/pdf), book notes, podcast transcripts, symlinks
└── wiki/
    ├── index.md
    ├── log.md
    └── (subdirectories appear as needed)
```

## Suggested page types (placeholder)

- `articles/<slug>.md`, one page per article or blog post.
- `books/<slug>.md`, one page per book.
- `podcasts/<slug>.md`, one page per episode or recurring show.
- `authors/<name-slug>.md`, author/host pages.
- `themes/<slug>.md`, cross-cutting summaries (e.g. "memetics", "city design").

## Routing for this sub-wiki

The catch-all for non-technical, non-work reading. If a piece is *about* AI but written for a general audience, it belongs here, not in `ai-research/`.

## Symlink mappings

| Symlink path | Real path | Created | Notes |
| ------------ | --------- | ------- | ----- |
| _none yet_   |           |         |       |
