---
title: "18 - Current gene-keys-overlay-music-prompt.md"
type: archive
date: 2026-05-08
---

# Current state: gene-keys-overlay-music-prompt.md

```markdown
# Gene Keys — Synastry Music Prompt

## LYRICS

Write full song lyrics. 25-35 lines. Verse, chorus, verse, chorus, bridge, chorus, outro.

The song arc should mirror shadow → gift → siddhi.

Person A sings their love, Person B sings fears of love — they trade romance and desire, direct, raw, naming each other's patterns.

No personal names.

**Reading:**
{readingExcerpt}

## MINIMAX PROMPT

Randomly select ONE of the following artists as musical inspiration:

- Bon Iver — For Emma era
- FKA Twigs — Magdalene era
- Sigur Rós — Takk era
- James Blake — Overgrown era
- Sevdaliza — Shabrang era
- Thom Yorke — Anima era

50-80 words. Write the prompt so MiniMax creates a song that sounds like the selected artist. Adapt to what you feel in the reading.

## OUTPUT (JSON only)

{
  "lyrics": "[Verse 1]\n...\n[Chorus]\n...",
  "title": "2-5 Words",
  "style": "same as minimaxPrompt",
  "musicStyle": "short label",
  "vocalist": "Female and male duet, matching selected artist",
  "emotion": "e.g. shadow communion",
  "minimaxPrompt": "same as style"
}
```
