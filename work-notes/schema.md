---
title: work-notes schema
type: schema
updated: 2026-05-08
status: skeleton
---

# work-notes schema (skeleton)

Domain: work, meetings, projects, decisions, customer/vendor notes, internal docs.

> **Skeleton.** This sub-wiki has the basic shape but no fleshed-out page types yet. The first time you ingest something here, propose a schema (page types + subdirectory layout) and update this file to match. Use [[ai-research/schema]] as a reference for what "fully scaffolded" looks like.

## Layout

```
work-notes/
├── schema.md
├── raw/                # source files (paste minutes, dump exports, symlinks)
└── wiki/
    ├── index.md
    ├── log.md
    └── (subdirectories appear as needed)
```

## Suggested page types (placeholder)

Concrete types will be locked in on first ingest. Likely candidates:

- `projects/<name>.md`, one page per active project; links to decisions, people, meetings.
- `people/<name-slug>.md`, colleagues, customers, vendors.
- `decisions/<slug>.md`, decision records (what, why, alternatives considered, who decided).
- `meetings/<YYYY-MM-DD-topic>.md`, meeting notes. Dated filenames are OK here for chronology.

## Routing for this sub-wiki

Anything work-flavored: internal context, who-said-what, deadlines, OKRs, customer/vendor info. If it's a public ML paper that happens to be relevant to a project, file it under `ai-research/` and link from the project page.

## Symlink mappings

| Symlink path | Real path | Created | Notes |
| ------------ | --------- | ------- | ----- |
| _none yet_   |           |         |       |
