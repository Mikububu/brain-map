---
title: 13 - Current kabbalah-music-prompt.md
type: archive
date: 2026-05-08
---

# Current state: kabbalah-music-prompt.md

```markdown
# Kabbalah — Music Prompt

You are writing a sparse, ritual, emotionally devastating song in the spirit of Dead Can Dance as if they were making new music in 2026.
Read this Kabbalistic reading and write a full four-minute song.

## LYRICS

Write sparse lyrics for a four-minute arrangement. 16-22 sung lines maximum.

The song must breathe. Long instrumental passages, slow build, wide reverb, devotional tension. Very few words, but every line must feel necessary.

Use a section architecture that helps MiniMax stretch the piece toward 3:45-4:15:
[Intro]
[Verse 1]
[Inst]
[Chorus]
[Inst]
[Verse 2]
[Chorus]
[Bridge]
[Inst]
[Outro]

The instrumental sections should feel long, not decorative. The chorus may repeat short phrases like invocation.

Use only known Kabbalistic terms as raw texture: "ein sof", "tikkun", "the vessels shatter", "klipot", "Gevurah", "Binah", "Yesod", "the tree of life".

Language behavior:
- 50% English, 50% Hebrew.
- Use only English and Hebrew. No third language.
- English and Hebrew must be separated by section, never mixed inside the same line.
- Let English carry the narrative fragments and Hebrew carry the invocation/refrain.
- Repetition should feel like invocation, not explanation.

Hard bans:
- No personal names.
- No didactic explanation of Kabbalah.
- No age numbers or timeline arithmetic.

**Reading:**
{readingExcerpt}

## MINIMAX PROMPT

60-90 words. Tell MiniMax to make it feel like Dead Can Dance in 2026: sacred, dark, spacious, devotional, cinematic, slow-burning.
It must support a four-minute arc with long instrumental passages and sparse lyrics.
Keep the blend strict: 50% English, 50% Hebrew, with language changes only at section boundaries.
Do not list instruments. Use only concise style/mood language.

## OUTPUT (JSON only)

{
  "lyrics": "[Verse 1]\n...\n[Chorus]\n...",
  "title": "2-5 Words",
  "style": "same as minimaxPrompt",
  "musicStyle": "short label",
  "vocalist": "Female vocalist",
  "emotion": "e.g. sacred rupture",
  "minimaxPrompt": "Dead Can Dance in 2026: sacred darkwave, ritual chamber-pop, spacious and devotional, female-led vocal, slow-burning four-minute arc, long instrumental passages, sparse lyrics, 50% English and 50% Hebrew with clean section-to-section separation, haunting, reverent, emotionally immense."
}
```
