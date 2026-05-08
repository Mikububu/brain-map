# raw/

Source materials for ingestion. **This folder is local-only**; nothing inside (except this README) is committed to the repo.

In a working local copy, this folder contains symlinks to the four app repos:

- `1-in-a-billion/` → the canonical engine
- `unhinged/` → the dialectical fork
- `past-life-contracts/` → the Vedic-only contract narratives
- `families-app/` → the relational scope

The symlinks make it possible to walk git history of those repos in-place, without copying their contents. The schema (`../schema.md`) records the live mapping. If you cloned this wiki and want to reproduce the source-walks, set up your own symlinks; the wiki references the structure, not the contents.

Files in here are never edited; the wiki only reads from them.
