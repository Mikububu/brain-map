---
title: "17 - Current vedic-overlay-music-prompt.md"
type: archive
date: 2026-05-08
---

# Current state: vedic-overlay-music-prompt.md

Path: `backend/prompts/music/vedic-overlay-music-prompt.md`. Verbatim file content as of 2026-05-08.

```markdown
# Vedic Astrology — Synastry Music Prompt

You are writing a full Vedic synastry composition in the spirit of Anoushka Shankar as if she were making new music in 2026.
Read this Vedic synastry reading about two people and write a complete 4-minute composition, not a sparse ritual fragment.

## INPUTS

- **Person 1**: {person1Name}
- **Person 1 Birthplace**: {person1BirthPlace}
- **Person 1 Languages**: {person1Languages}
- **Person 1 Music Region**: {person1MusicRegion}
- **Person 2**: {person2Name}
- **Person 2 Birthplace**: {person2BirthPlace}
- **Person 2 Languages**: {person2Languages}
- **Person 2 Music Region**: {person2MusicRegion}
- **Reading excerpt**: provided below

## CULTURAL RESEARCH

Research each birthplace as a center of musical gravity. What folk, sacred, court, street, or operatic textures live there?
Use that as secondary and tertiary DNA in the composition.
Default weighting for synastry: 50% Anoushka Shankar / contemporary Indian-classical center, 25% Person 1 cultural memory, 25% Person 2 cultural memory.
This is intentional crossover, not generic world-music blur.

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

Anoushka Shankar is the center of gravity.
The sonic language must stay rooted in contemporary Indian-classical composition: intricate, devotional, cinematic, intimate, and rhythmically alive.
The two birthplace traditions should enter as specific secondary colors: rhythm ghosts, melodic turns, vocal phrasing, ceremonial atmosphere, or emotional weather.
Do not flatten them into generic "fusion" shorthand. The mix should feel weighted and deliberate.
Extended bansuri passages in the spirit of Hariprasad Chaurasia are essential, not optional.
It still needs a real chorus, enough sung text to support a 4-minute arc, and a strong sense of inevitability.

## HARD STYLE LOCK

This is not "adjacent to" Anoushka Shankar. It must feel authored in her lane.
If the resulting minimaxPrompt does not literally anchor on `Anoushka Shankar in 2026` and explicitly say `contemporary Indian-classical`, it is wrong.
If the minimaxPrompt does not preserve the weighted crossover logic, it is wrong.
If there is no clear bansuri spotlight with room to breathe, it is wrong.

## LYRICS RULES

- Write full composition lyrics: 20-28 lines total.
- Structure: [Intro], [Verse 1], [Chorus], [Inst], [Verse 2], [Chorus], [Bridge], [Inst], [Chorus], [Outro].
- Both [Inst] sections should imply long bansuri-led passages. Think alaap, breath, answering phrases, and release.
- The piece must feel like a 4-minute composition, not a fast commercial song.
- Two unnamed voices trading fragments is fine, but keep the lines singable, concise, and chorus-led.
- Use only three language streams: Sanskrit, Person 1's language, Person 2's language.
- Sanskrit should be written in simple Latin transliteration, not Devanagari.
- Never mix two languages inside the same line.
- Languages may alternate across sections, but the chorus must be memorable and recur at least twice.
- Sanskrit should feel like the karmic axis; Person 1 and Person 2 languages should feel like memory answering fate.
- Strip all personal names from lyrics.
- No didactic explanation of astrology.
- No age numbers, timeline arithmetic, degree numbers, or orb values.
- Prefer short, repeatable lyric lines over explanatory narration.

**Reading:**
{readingExcerpt}

## MINIMAX PROMPT

55-95 words. Tell MiniMax to make it feel like Anoushka Shankar in 2026: meditative, intricate, emotionally immense, devotional but contemporary.
It must produce a real 4-minute composition with a recurring chorus, two extended bansuri passages, and enough vocal material to sustain the arc without overcrowding it.
Keep the weighting explicit: roughly 50% Anoushka center, 25% Person 1 cultural memory, 25% Person 2 cultural memory.
The minimaxPrompt must begin with `Anoushka Shankar in 2026:` and explicitly include `contemporary Indian-classical`.
It must mention a recurring chorus and all of: sitar, bansuri, tanpura drone, tabla pulse.
It must explicitly call for extended bansuri passages in the spirit of Hariprasad Chaurasia.
It should describe the other two cultural streams as specific secondary colors, not as a generic fusion blob.
Keep it concise and evocative rather than technical.

## OUTPUT (JSON only)

{
  "lyrics": "[Verse 1]\n...\n[Chorus]\n...",
  "title": "2-5 Words",
  "style": "same as minimaxPrompt",
  "musicStyle": "short label",
  "vocalist": "Female vocalist",
  "emotion": "e.g. karmic gravity",
  "minimaxPrompt": "Anoushka Shankar in 2026: contemporary Indian-classical Vedic synastry composition, emotionally immense, meditative, rhythmically alive, real 4-minute arc, recurring chorus, sitar lead, tanpura drone, tabla pulse, and extended bansuri passages in the spirit of Hariprasad Chaurasia, with a weighted crossover of 50% Anoushka center, 25% Person 1 cultural memory, and 25% Person 2 cultural memory as specific secondary colors, haunted and luminous."
}
```
