---
title: "14 - Current kabbalah-overlay-music-prompt.md"
type: archive
date: 2026-05-08
---

# Current state: kabbalah-overlay-music-prompt.md

```markdown
# Kabbalah — Synastry Music Prompt

You are writing a sparse, ritual, emotionally devastating song in the spirit of Dead Can Dance as if they were making new music in 2026.
Read this Kabbalistic synastry reading about two people and write a full four-minute song.

## CULTURAL INPUTS

- **Person 1** from {person1BirthPlace} — languages: {person1Languages}
- **Person 2** from {person2BirthPlace} — languages: {person2Languages}

Research each birthplace. What music lives in that soil? Folk, sacred, court, street. Use that cultural DNA as texture in the lyrics and in the MiniMax prompt.

## LYRICS

Write sparse song lyrics. 16-22 sung lines maximum. The rest is instrumental space.

Use a section architecture that helps MiniMax stretch the piece toward 3:45-4:15:
[Intro]
[Verse 1]
[Inst]
[Chorus]
[Inst]
[Verse 2]
[Chorus]
[Inst]
[Verse 3]
[Bridge]
[Inst]
[Outro]

More silence than words. More sound than singing. Long instrumental passages are essential, not decorative. Every vocal line must earn its place.

Use only known Kabbalistic terms as raw texture: "ein sof", "tikkun", "the vessels shatter", "klipot", "Gevurah", "Binah", "Yesod", "the tree of life".

Language behavior — three distinct blocks, never overlapping:
- One Hebrew section.
- One Person 1 language section.
- One Person 2 language section.
- Use only those three language streams. Do not introduce a fourth language.
- Do not use English unless English is actually Person 1's or Person 2's language.
- Each language must hold its own full section or cluster of consecutive lines.
- Never switch languages line-by-line.
- Never blend languages inside the same line.
- Hebrew should act as the sacred axis. Person 1 and Person 2 languages should answer it from their own worlds.

Hard bans:
- No personal names.
- No didactic explanation of Kabbalah.
- No age numbers or timeline arithmetic.

**Reading:**
{readingExcerpt}

## MINIMAX PROMPT

80-120 words. Tell MiniMax to make it feel like Dead Can Dance in 2026: sacred, dark, spacious, devotional, cinematic, slow-burning.
It must support a four-minute arc with long instrumental passages and sparse lyrics.
Describe a three-part vocal arrangement: one Hebrew section, one Person 1 language section, one Person 2 language section, each clearly separated in time.
Reference the two cultural regions as flavor, not formula.
Do not list instruments. Use only concise style/mood language.

## OUTPUT (JSON only)

{
  "lyrics": "[Verse 1]\n...\n[Chorus]\n...",
  "title": "2-5 Words",
  "style": "same as minimaxPrompt",
  "musicStyle": "short label",
  "vocalist": "Female vocalist",
  "emotion": "e.g. sacred concealment",
  "minimaxPrompt": "Dead Can Dance in 2026: sacred darkwave, ritual and cinematic, slow-burning four-minute arc, long instrumental passages, sparse vocals, female-led or mixed-voice lament, one Hebrew section, one Person 1 language section, one Person 2 language section, each clearly separated in time, immersive, reverent, haunted, emotionally immense."
}
```
