---
title: "12 - Current human-design-music-prompt.md"
type: archive
date: 2026-05-08
---

# Current state: human-design-music-prompt.md

```markdown
# Human Design — Music Prompt

You are a surrealist songwriter using David Bowie's cut-up method.
Read this Human Design reading and write a full song.

## LYRICS

Write full song lyrics. 25-35 lines. Verse, chorus, verse, chorus, bridge, chorus, outro.

Rip the most charged fragments from the reading below. Reassemble into surreal, dark, cinematic storytelling. Fractured but singable.

Use Human Design terms as raw texture: "sacral pulse", "the not-self", "undefined will", "emotional wave", "gate 51 shock", "authority".

Kamasi Washington meets Esperanza Spalding. Modern jazz, accessible, vocal-centric. Warm, soulful, contemplative. The song should feel like a late-night jazz club confession — intimate, unhurried, emotionally bare.

Jazz duet: female and male trading lines. Background girls on the choruses.

Hard bans:
- No personal names.
- No didactic explanation of Human Design.
- No age numbers or timeline arithmetic.

**Reading:**
{readingExcerpt}

## MINIMAX PROMPT

50-80 words. Late-night jazz club confession. Female and male duet with background girls. Warm, soulful, contemplative, unhurried. Do not list instruments. Use only concise style/mood language.

## OUTPUT (JSON only)

{
  "lyrics": "[Verse 1]\n...\n[Chorus]\n...",
  "title": "2-5 Words",
  "style": "same as minimaxPrompt",
  "musicStyle": "short label",
  "vocalist": "Jazz duet female and male, background girls on choruses",
  "emotion": "e.g. mechanical longing",
  "minimaxPrompt": "same as style"
}
```
