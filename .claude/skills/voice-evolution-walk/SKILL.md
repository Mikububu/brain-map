---
name: voice-evolution-walk
description: Walk the philosophical journey of one astrological voice/system across the four-app suite (1 in a Billion, Unhinged, Past-Life Contracts, Families-app) by reading git diffs day-by-day from December 2025 onward, then write a mind-map page to `prompting-system/wiki/voices/`. Use when starting work on the next voice, Vedic, Kabbalah, Gene Keys, or Human Design, or revising an existing one (Western already done). Operates read-only on git history. The output is a philosophical artifact in the user's own texture, not a data extraction.
---

# Voice Evolution Walk

## What this skill does

Reconstructs the philosophical journey of one astrological voice/system across the four-app suite by reading git diffs day-by-day from each repo's first commit (around December 2025) to today. Writes a mind-map page in the user's texture to `prompting-system/wiki/voices/<system>.md`.

This is **not** a data extraction or a snapshot. The output is a philosophical artifact: the user, a non-technical builder, reads it to recognise their own thinking. **Dead ends and dialectics are first-class material**, they are part of the journey.

## Inputs

A voice/system name, one of: `western`, `vedic`, `kabbalah`, `gene-keys`, `human-design`.

If the user says "do the next voice" or similar, infer from `prompting-system/wiki/index.md` which voices are already done and which is methodologically next. Order of construction: **Western → Vedic → Kabbalah → Gene Keys → Human Design**.

## The four apps

- **1 in a Billion**, main app, canonical engine. Codebase folder is `1-in-a-billion-v2/` (a v2 architectural rewrite); the app is called "1 in a Billion". Use the app name in prose; use the folder path only inside `Sources` lists.
- **Unhinged**, diagnostic-noir / chaos-chic / "exquisite disaster connoisseur" tonal fork. Same engine, opposite voice temperature.
- **Past-Life Contracts**, Vedic-only, two-person karmic-contract narratives.
- **Families-app**, relational / family-myth scope (1-4 people).

Symlinks already in place at `prompting-system/raw/`:
- `1-in-a-billion` → `~/Desktop/my Iphone apps/1-in-a-billion/1-in-a-billion-v2`
- `unhinged` → `~/Desktop/my Iphone apps/Unhinged`
- `past-life-contracts` → `~/Desktop/my Iphone apps/Past-life-contracts`
- `families-app` → `~/Desktop/my Iphone apps/Families-app`

## Read-only discipline (non-negotiable)

Source files in `prompting-system/raw/` are symlinks to **live app repos**. They MUST NOT be modified. Use only:
- `git log --follow --diff-filter=AM --pretty=format:'%h %ai %s' -- <file>`
- `git show <hash> -- <file>`
- `git diff <hashA> <hashB> -- <file>`
- `git log --all --oneline -- <file>` for full coverage including renames
- File reads via the `Read` tool

NEVER: edit, write to, sed, awk, redirect-into, rm, or otherwise mutate any file under `raw/`. NEVER create commits or branches in any of the four app repos. If you find a bug or smell something wrong in the source, note it in the output page; do not fix it.

## Where to look for each voice

For each voice, the relevant files across both repos (1 in a Billion + Unhinged) typically include:

- `backend/prompt-layers/systems/<voice>-individual.md`
- `backend/prompt-layers/systems/<voice>-synastry.md` (may not exist for all voices)
- `backend/prompt-layers/systems/<voice>-individual-incarnation.md`
- `backend/prompt-layers/style/style-guide-insert-<voice>-voice.md`
- `backend/prompt-layers/rewrite/narrative-rewrite-en.md` (and the 10 other languages, sample 2-3, including the native-script ones: hi, ru, zh)
- `backend/prompt-layers/digests/<voice>-chart-digest-*.md` (may exist for Vedic)
- `backend/prompts/music/<voice>-music-prompt.md`
- `backend/src/prompts/systems/<voice>.ts` (if exists)
- `backend/src/prompts/styles/<voice>*.ts` or `*<voice>*.ts` (if exists)
- references in `backend/prompt-layers/style/voice-architecture-all-systems.md`

Slug normalisation: `gene-keys` and `human-design` are kebab-case. The folder structure usually follows the same convention; double-check via `find` if a path is missing.

For Past-Life Contracts: only Vedic is relevant; skip if walking another voice. For Families-app: all five voices but with different scope, relational / family-myth tone, often tonally softer than the canonical engine.

## Method

1. **Map the territory.** In each relevant repo, find every file related to the voice via grep / find. List paths.
2. **Walk each file's history.** Run `git log --follow` for each. Note creation date, commit count, file size growth.
3. **Pick 8-15 pivotal commits** across all files. Look for: large diffs, telling commit messages, deletions of substantial blocks, file renames, file deletions.
4. **Read the diffs.** For each pivotal commit, `git show <hash>` and read the actual diff. Note what was added / removed / replaced.
5. **Compare current vs. first.** Diff the current state of each file against its first substantive version. What survived? What was rewritten? What was deleted entirely?
6. **Find dead ends.** Phrases or sections that were added then later removed mark experiments that didn't pan out. These belong in the page.
7. **Identify the dialectic.** How does this voice differ between 1 in a Billion and Unhinged? Find the exact contrast, same concept, two voice temperatures.
8. **Read intent docs.** Any `voice-architecture-all-systems.md`, READMEs, or audit docs that explain the design intent at the time.

If the work is large, delegate the deep walk to an `Explore` subagent (read-only). Pass it the same instructions. Synthesize its report into the Obsidian page yourself, texture lands better when one mind shapes the prose.

## Output: the mind-map page

Write to `prompting-system/wiki/voices/<system>.md`. Filename is kebab-case (`gene-keys.md`, `human-design.md`).

### Frontmatter

```yaml
---
title: <Voice Name>
type: voice
system: <slug>
narrator: <one-line narrator description, e.g. "Aghori witness at the cremation ground">
created: YYYY-MM-DD
updated: YYYY-MM-DD
tags: [voice, <slug>, ...domain tags]
---
```

### Sections, in order

The voice page is a **mind-map**, scannable in 90 seconds. Target ~300 words total. Mostly tables and short bullets. No prose paragraphs longer than 3 lines. Deep-dive content goes into separate `decisions/<slug>.md` pages, only created on user request.

1. `# <Voice Name>`, top heading. One short tagline orienting the voice in relation to the other four (one sentence).

2. `## Now`, the voice today. One blockquote of 1-3 short sentences quoting/paraphrasing current prompt language. Then one or two sentences on the operational rule (e.g. for Western: the two-zone contract).

3. `## Timeline`, a markdown table with columns: `Date | Move | What changed`. 6-10 rows covering the most pivotal commits in chronological order. After the table, one italic line: *"Want any row expanded into its own page? Say 'expand <date>' and I'll write a `decisions/<slug>` page."*

4. `## Dialectic with <opposite app>`, a small comparison table (typically 2-3 rows) showing how the voice differs in the dialectical fork (Unhinged for Western, etc.). For voices without a strong fork, skip this section.

5. `## Dead ends`, bulleted list, 4-8 entries. Each: short phrase naming what was tried then abandoned, in parentheses why.

6. `## Texture`, bulleted. How this builder thinks: 5-8 short phrases (metaphors, syntactic tics, things they reach for). Then one short list of what's refused. End with one paradox sentence (e.g. for Western: "literature that is forensically true").

7. `## Sources`, bulleted list of `raw/...` paths. Then one line of commit hashes separated by `·`.

**Do not** include "Birth", "The journey" (full prose), or deep-dive sections like "The Hellenistic merge" on the voice page itself. Those go into `decisions/<slug>.md` pages on request.

## Texture rules (the user's voice)

The Obsidian page must read in the builder's voice, not academic prose. Match these patterns:

- **Architectural / sensory metaphors**, rooms, corridors, locked floors, weather, doors, vessels, fires, rivers (depends on which voice, match the voice's own metaphor world).
- **Judicial vocabulary**, mandate, contract, non-negotiable, hard rules, forbidden lexicon. The user builds systems that *enforce*, not guidelines that *suggest*.
- **"X is not Y. X is Z."** sentence shape, direct naming over soft framing.
- **"The reader should feel SEEN."** This phrase recurs across the corpus; quote when relevant.
- **No moralization, no rescue language, no Instagram-coach positivity.**
- **Quote prompt text directly**, wherever the user's actual words make a move visible. Use blockquote (`> "..."`) for impact.
- **Cite commit hashes and dates**, verifiable evidence. The user can `git show <hash>` to confirm.
- **Dead ends as first-class material**, the journey includes failures.
- **Dialectical mode**, always note where the voice contrasts with another, especially Unhinged.
- **Never use em-dashes or en-dashes for sentence breaks.** Use commas, periods, colons, semicolons, or parentheses instead. Plain hyphens in compound words (kebab-case) are fine. The user explicitly forbade em-dashes on 2026-05-08; this applies to all wiki output.

## After writing the page

1. **Update `prompting-system/wiki/index.md`**, add a one-line entry under `## Voices`:
   ```
   - [[voices/<slug>|<Voice Name>]], <one-line tagline>
   ```

2. **Append to `prompting-system/wiki/log.md`**:
   ```
   ## [YYYY-MM-DD] ingest | <Voice Name> voice, full git history walk
   - Wrote [[voices/<slug>]].
   - Traced N pivotal commits across <repos>.
   - Captured: <key sections>.
   - Sources: <key files>.
   - Open question for the user: <texture/accuracy question>.
   ```

3. **Tell the user, briefly**: the path to the page + 2-3 questions:
   - Does the **voice** of the page sound like you?
   - Anything **wrong** in the facts/dates/quotes?
   - Anything **missing** before the next voice?

## What I do NOT do

- Write to `raw/`. Ever.
- Modify any source code.
- Make commits in any of the four app repos.
- Speculate beyond what diffs prove. (If a move's intent isn't visible from the prompt or commit message, say so.)
- Soften the user's voice. The Obsidian page should be as direct as the prompts themselves.
- Skip dead ends. They are part of the philosophy.
- Confuse the app name with the folder name. The app is "1 in a Billion"; the folder happens to be `1-in-a-billion-v2/`.
- Build the page from commit messages alone. Read the diffs.

## Cross-reference

- Top-level wiki conventions: [[CLAUDE.md]] (the wiki's three operations + Obsidian conventions).
- Prompting-system schema: `prompting-system/schema.md` (this sub-wiki's page types and routing).
- The first executed walk (use as model): `prompting-system/wiki/voices/western.md`.
