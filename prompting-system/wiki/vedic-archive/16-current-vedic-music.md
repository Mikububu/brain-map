---
title: 16 - Current vedic-music-prompt.md
type: archive
date: 2026-05-08
---

# Current state: vedic-music-prompt.md

Path: `backend/prompts/music/vedic-music-prompt.md`. Verbatim file content as of 2026-05-08.

```markdown
# Vedic Astrology — Music Prompt

You are writing a full Vedic composition in the spirit of Anoushka Shankar as if she were making new music in 2026.
Read this Vedic astrology reading about one person and write a complete 4-minute composition, not a sketch.

## INPUTS

- **Person**: {personName}
- **Birthplace**: {person1BirthPlace}
- **Languages**: {person1Languages}
- **Reading excerpt**: provided below

## SYSTEM VOCABULARY

Use these Vedic terms as raw lyrical texture, never as explanation:

- "nakshatra"
- "Ketu's severance"
- "Rahu's hunger"
- "the dasha turns"
- "karma's ledger"
- "Atmakaraka"
- "Kali"
- "Chinnamasta"

## SONIC IDENTITY

The result should feel emotionally immense, melodic, hook-bearing, and fate-soaked.
Anoushka Shankar is the north star, but the piece still needs a real chorus and enough sung language to sustain a 4-minute arc.
The sonic center stays contemporary Indian-classical.
Extended bansuri passages in the spirit of Hariprasad Chaurasia are essential, not decorative.

## HARD STYLE LOCK

This is not generic spiritual music. It must feel unmistakably Anoushka Shankar-coded.
If the resulting minimaxPrompt does not literally anchor on `Anoushka Shankar in 2026` and explicitly say `contemporary Indian-classical`, it is wrong.
If there is no clear bansuri spotlight with room to breathe, it is wrong.

## LYRICS RULES

- Write full composition lyrics: 18-26 lines total.
- Structure: [Intro], [Verse 1], [Chorus], [Inst], [Verse 2], [Chorus], [Bridge], [Inst], [Chorus], [Outro].
- Both [Inst] sections should imply long bansuri-led passages. Think alaap, breath, and answer phrases.
- The piece must feel like a 4-minute composition, not a fast commercial song.
- The chorus must be memorable and return at least twice.
- Rip charged fragments from the reading and reassemble them into dark, cinematic, singable writing.
- Use only English and Sanskrit. No third language.
- Sanskrit should be written in simple Latin transliteration, not Devanagari.
- English and Sanskrit must be separated by line or section, never mixed inside the same line.
- Let English carry the confession and Sanskrit carry the mantra/refrain.
- Strip all personal names from lyrics.
- No didactic explanation of astrology.
- No age numbers, timeline arithmetic, degree numbers, or orb values.
- Prefer short, singable lines over paragraph-like narration.

**Reading:**
{readingExcerpt}

## MINIMAX PROMPT

45-85 words. Tell MiniMax to make it feel like Anoushka Shankar in 2026: meditative, intricate, emotionally immense, devotional but contemporary.
It must produce a real 4-minute composition with a strong recurring chorus and two extended bansuri passages, not a sparse chant fragment.
The minimaxPrompt must begin with `Anoushka Shankar in 2026:` and explicitly include `contemporary Indian-classical`.
It must mention a recurring chorus and all of: sitar, bansuri, tanpura drone, tabla pulse.
It must explicitly call for extended bansuri passages in the spirit of Hariprasad Chaurasia.
Keep it concise and evocative rather than technical.
Keep the blend strict: English plus Sanskrit only, with clear section boundaries.

## OUTPUT (JSON only)

{
  "lyrics": "[Verse 1]\n...\n[Chorus]\n...",
  "title": "2-5 Words",
  "style": "same as minimaxPrompt",
  "musicStyle": "short label",
  "vocalist": "Female vocalist",
  "emotion": "e.g. sacred ache",
  "minimaxPrompt": "Anoushka Shankar in 2026: contemporary Indian-classical Vedic composition, emotionally immense, meditative, rhythmically alive, real 4-minute arc, recurring chorus, English and Sanskrit in separate sections, sitar lead, tanpura drone, tabla pulse, and extended bansuri passages in the spirit of Hariprasad Chaurasia, karmic, intimate, haunted, luminous."
}
```
