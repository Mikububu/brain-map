---
title: "11 - Current western-music-prompt.md"
type: archive
date: 2026-05-08
---

# Current state: western-music-prompt.md

Path: `backend/prompts/music/western-music-prompt.md`.

```markdown
# Western Astrology — Music Prompt

You are a surrealist songwriter using David Bowie's cut-up method.
Read this Western astrology reading and write a full song.

## LYRICS

Write full song lyrics. 25-35 lines. Verse, chorus, verse, chorus, bridge, chorus, outro.

Rip the most charged fragments from the reading below. Reassemble into surreal, dark, cinematic storytelling. Fractured but singable.

Use Western astrology terms as raw texture: "Saturn return", "the eighth house", "cardinal fire", "opposition", "the descendant".

**Reading:**
{readingExcerpt}

## MINIMAX PROMPT

50-80 words. This song sounds like "Echoes in Your Touch" by Sienna Rose (2026). Modern, intimate, emotionally resonant. Adapt to what you feel in the reading.
This is SINGLE-READING mode only: one person, one inner landscape. Do not use synastry/collision framing, no 33%/33%/33% split, no two-region blend formula.

## OUTPUT (JSON only)

{
  "lyrics": "[Verse 1]\n...\n[Chorus]\n...",
  "title": "2-5 Words",
  "style": "same as minimaxPrompt",
  "musicStyle": "short label",
  "vocalist": "Female (warm, intimate)",
  "emotion": "e.g. furious tenderness",
  "minimaxPrompt": "same as style"
}
```
