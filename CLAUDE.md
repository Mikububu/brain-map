# Wiki Operations

This is a Karpathy-style LLM wiki ([pattern source](https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f)). Three sub-wikis live here:

- `ai-research/`, fully-scaffolded template
- `work-notes/`, skeleton
- `reading-list/`, skeleton

Each sub-wiki has the same shape:

- `raw/`, source files. The user puts things here (often as symlinks). Never edit anything inside.
- `wiki/`, LLM-generated markdown pages with `[[wikilinks]]`. The user does not edit these; you do.
- `schema.md`, sub-wiki-specific conventions: page types, subdirectories, and the symlink table for `raw/`.

Always read the relevant `schema.md` before doing any operation in a sub-wiki.

---

## The three operations

### 1. Ingest

Triggered by: `Ingest <path>` (or multiple paths, or `Ingest <sub-wiki>/raw/`).

1. Resolve the path. It may live in any sub-wiki's `raw/`. If the user did not specify a sub-wiki, infer it from the source's location; if still ambiguous, route by content (see **Routing rules**).
2. Read the source fully. For PDFs use the Read tool; for very large files read in chunks.
3. Identify entities worth their own page (people, papers, models, organisations, concepts, projects, decisions). Skip entities that only deserve a passing mention, link to existing pages instead of creating thin stubs.
4. For each entity:
   - Create or update the page under the correct subdirectory of `wiki/` per the sub-wiki's `schema.md`.
   - Use `[[wikilinks]]` to connect to other pages. Prefer linking over re-stating.
   - Append the source filename to the page's `## Sources` section.
5. Update `wiki/index.md`, add a one-line summary for any new pages, grouped by type.
6. Append to `wiki/log.md`:
   ```
   ## [YYYY-MM-DD] ingest | <source filename>
   - 2-4 line summary of what was added/changed.
   - List of pages created or updated.
   ```
7. Report back: which pages were created, which updated, any duplicates merged, and any entities you deliberately did not promote to a page.

### 2. Query

Triggered by: `Query: <question>` or `Query <sub-wiki>: <question>`.

1. Search across all sub-wikis (or just the named one) by reading the `wiki/` files. Use grep first to find candidate pages.
2. Synthesize an answer in plain prose.
3. Cite specific pages inline with `[[page-name]]` so the user can click through in Obsidian.
4. If the synthesis is non-trivial and likely to be asked again, offer to file it as a new page (e.g. `wiki/topics/<slug>.md`) so future queries compound. Only file after the user agrees.
5. Note gaps explicitly: things you couldn't answer because no source covers them. This drives what to ingest next.

### 3. Lint

Triggered by: `Lint <sub-wiki>` or `Lint` (all).

1. Walk every page in the target `wiki/` directories.
2. Report:
   - **Broken wikilinks**, `[[target]]` where no matching page exists.
   - **Orphan pages**, no incoming links from other pages.
   - **Stale pages**, `updated:` older than 90 days and no recent log entry.
   - **Duplicates**, multiple pages clearly covering the same entity.
   - **Missing `## Sources`**, page lacks source attribution.
   - **`index.md` drift**, pages that exist on disk but not in the index, or vice versa.
3. Suggest fixes. Do not auto-merge or auto-delete. Auto-fix only obvious typos in wikilink targets, and only after listing them and getting a yes.

---

## Routing rules (which sub-wiki?)

Default by content:

- **AI/ML papers, model cards, researcher profiles, lab pages, technical ML/stats articles** → `ai-research/`
- **Internal meetings, project notes, decisions, OKRs, customer/vendor notes** → `work-notes/`
- **General articles, blog posts, books, podcasts, broad reading** → `reading-list/`

If a source spans two (e.g. a work-related ML paper), prefer the sub-wiki whose `schema.md` has the most specific page type for it. When in doubt, ask the user before ingesting.

---

## File conventions (Obsidian-friendly)

- **Filenames**: `kebab-case.md`. No spaces. No leading dates (except meeting notes, which may use `YYYY-MM-DD-topic.md`).
- **One entity per file**.
- **Wikilinks**: `[[file-name-without-extension]]` or `[[file-name|Display text]]`. Always relative to the vault root, Obsidian resolves them automatically across folders.
- **Frontmatter (YAML)** on every wiki page:
  ```yaml
  ---
  title: Human-readable title
  type: paper | model | concept | person | org | topic | project | decision | meeting | article | book | note
  created: YYYY-MM-DD
  updated: YYYY-MM-DD
  tags: [tag-one, tag-two]
  ---
  ```
- **Headings**: body starts at `##`. The H1 is implied by the YAML `title`.
- **Sources**: every page ends with a `## Sources` section listing the raw files that contributed (filenames only, one per line as `- raw/...`).
- **No em-dashes or en-dashes** in wiki text. Use commas, periods, colons, semicolons, or parentheses instead. Plain hyphens in compound words are fine. (User preference, recorded 2026-05-08.)

---

## Where to look next

For the per-sub-wiki rules (page types, subdirectory layout, and the symlink table that records what's actually in `raw/`), read the relevant `schema.md`:

- [[ai-research/schema]]
- [[work-notes/schema]]
- [[reading-list/schema]]
