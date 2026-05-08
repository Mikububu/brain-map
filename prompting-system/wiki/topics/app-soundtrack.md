---
title: App Soundtrack
type: topic
created: 2026-05-08
updated: 2026-05-08
tags: [topic, music, soundtrack, in-app, distinct-from-user-music]
---

# App Soundtrack

**Not** the same as [[topics/music-prompts|the user-reading music]]. This is the music **the customer hears while using the app**: theme music, hook-sequence ambient, offer-screen scoring. Its philosophical development is separate, parallel.

## Two music threads, separate

| | User-reading music ([[topics/music-prompts]]) | App soundtrack (this page) |
|---|---|---|
| Audience | The reader receiving their reading | The user navigating the app |
| Method | LLM writes lyrics → MiniMax synthesises song per reading | Builder writes lyrics (with GPT / Claude) → MiniMax synthesises a static track |
| Output | Per-reading custom songs (5 voices × 2 modes per reading) | Static named tracks deployed inside the app |
| Lives in | `backend/prompts/music/*-music-prompt.md` | `assets/sounds/*.mp3` |

## The named tracks (history)

| Track | Purpose | Status |
|---|---|---|
| `one_in_a_billion_new.mp3` | App theme | **live** |
| `one_in_a_billion_2.mp3` | App theme (variant) | **live** |
| **Whispering Breeze** | Hook-sequence ambient | **deleted** (Jan 15) |
| **Glass Horizon** | Offer-screen ambient | **deleted** (after a brief reign) |

## The 30-minute night

In a single 30-minute window on **2026-01-15**, the builder iterated through every plausible combination of two ambient tracks across two screens. The commit log reads like a real-time edit, preserved verbatim:

| Time | Commit | Move |
|---|---|---|
| 02:48 | `fa4ba8e9` | Add Whispering Breeze to HookSequence |
| 02:49 | `8be931e0` | Reduce Whispering Breeze volume to 12% (60% reduction) |
| 02:49 | `444729fd` | Fade out Whispering Breeze when navigating to offer screens |
| 02:51 | `8085523e` | Remove Glass Horizon, make voice audio louder (100%) |
| 03:07 | `2d3f971c` | Add Glass Horizon background music (to Offer) |
| 03:11 | `3384dfec` | Offer: use Whispering Breeze (not Glass Horizon) |
| 03:12 | `e67a379b` | Offer: Glass Horizon only (NOT Whispering Breeze) |
| 03:14 | `e8d0bdf1` | HookSequence: STOP Whispering Breeze immediately before offer screens |
| 03:16 | `8b7e2c77` | STOP Whispering Breeze on blur (focus loss), both screens |
| 03:19 | `c01960a6` | **DELETE Whispering Breeze completely** |

The capitalised DELETE is the user's, in the actual commit message. Whispering Breeze did not survive the night. Glass Horizon survived a few minutes longer, then was also removed.

The current app uses only the two `one_in_a_billion_*.mp3` theme tracks.

## What this captures (method)

The builder's working method on app sound is **rapid surgical iteration**. Not weeks of tweaking; one focused session, A / B / neither, and a final cull. The whole episode is preserved in commits, including the dead-ends. This is one of the cleanest documented examples in the corpus of **tried, abandoned, decided** at sub-hour resolution.

## What I haven't yet captured

The user said: *"You could see the evolution of One in a Billion's music and the different lyrics and songs I wrote with GPT and Claude. Let MiniMax interpret them."*

The actual lyric drafts for `one_in_a_billion_new.mp3` and `one_in_a_billion_2.mp3` are **not currently in the codebase**. Possible homes:

- An earlier commit, since cleaned (would surface via `git log --diff-filter=D`)
- A drafts folder outside the repo (the builder's local notes)
- Conversation transcripts with GPT / Claude during composition (not in this wiki's context)

If the builder wants the lyric history fully captured, the next ingest is: locate the lyric drafts and walk the timeline of theme-song iteration alongside this commit history.

## Why this matters

The app soundtrack is the smallest, most concrete example of how the builder works:
- **Make it.** Add Whispering Breeze.
- **Tune it.** Volume, fade, blur-stop, screen-pairing.
- **Test it against alternatives.** Glass Horizon. Switch. Switch back.
- **Cut it.** Capital-letter DELETE.
- **Keep what stays.** The two theme tracks live; everything else is artefact.

The same method shapes [[topics/music-prompts]], [[topics/matching-algorithm]], [[topics/layer-3-rewrite]], and the voice pages. The 30-minute night on Jan 15 is the method in its purest form.

## Connections

- [[topics/music-prompts]] (the OTHER music: per-reading user-music, MiniMax-driven from LLM-written lyrics)
- [[apps/1-in-a-billion]] (where the theme tracks live)
- [[topics/january-foundation]] (Jan 15 sits inside the foundational period)

## Sources

- `~/Desktop/my Iphone apps/1-in-a-billion/1-in-a-billion-v2/assets/sounds/one_in_a_billion_new.mp3`
- `~/Desktop/my Iphone apps/1-in-a-billion/1-in-a-billion-v2/assets/sounds/one_in_a_billion_2.mp3`
- Commits (all 2026-01-15, ~30 minutes total): `fa4ba8e9` · `8be931e0` · `444729fd` · `8085523e` · `2d3f971c` · `3384dfec` · `e67a379b` · `e8d0bdf1` · `8b7e2c77` · `c01960a6`
