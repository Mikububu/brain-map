---
title: Music Philosophy
type: music
created: 2026-05-08
updated: 2026-05-08
tags: [music, philosophy, principles]
---

# Music Philosophy

The cross-cutting principles holding the [[music|music architecture]] together. Why the music sounds the way it sounds. Why some moves were tried and abandoned. The "weighted crossover" paradox.

## What the builder reaches for

1. **Sonic anchors grounded in real artists**, not abstract mood-boards.
   Sienna Rose, Anoushka Shankar 2026, Dead Can Dance 2026, Bon Iver / FKA Twigs / Sigur Rós (random), Kamasi meets Esperanza. **Real people's actual 2026-era work as the north star.** Not "ambient meditation" or "dark electronic." Specific named artists in specific named eras.

2. **Surrealism over explanation.**
   Cut-up framing was tried then stripped. *"Surreal storytelling, dark, cinematic, fractured"* is the replacement. The lyrics should sound like art, not astrology translation.

3. **Silence and space as material.**
   Vocal-centric for Western (indie-pop). Instrumental passages **non-negotiable** for Vedic (bansuri breathing room), Kabbalah (long reverb), even Gene Keys (jazz sparseness). The space between notes is as charged as the notes.

4. **Weighted cultural crossover, not generic fusion.**
   The 50/25/25 rule is strict. 50% sonic centre, 25% Person 1 culture, 25% Person 2 culture. **Not a blur, a deliberate hierarchy with ratios.** Anoushka Shankar is the centre for Vedic; the two birthplace traditions are *secondary colours*. Intentional weighted collision, not "world music."

5. **Language as texture, not translation.**
   Sanskrit, Hebrew, regional languages woven in as raw sound. Sanskrit mantric refrain. Hebrew invocation. Regional phrase answering fate. **Never mixed within a line.** Each language holds its own section.

6. **Hard bans that lock intention.**
   No names, no city names, no system jargon as explanation, no age numbers, no timeline arithmetic. These bans protect the listener from feeling lectured.

## What the builder refuses

1. **Generic world-music fusion.** *"Ethno ambient"* means traditional / folk instruments processed through modern sonic space, not a blend soup.
2. **Didactic explanation.** The song is not a horoscope or reading summary. The chart is input; the emotional truth is output.
3. **Micromanaged instrumentation.** Prompt points the artist toward sonic direction; MiniMax decides specifics. *"Don't list instruments"* (March 22 policy).
4. **Over-hedging.** The Final Verdict commits removed *"trim negative instructions, remove 'Both lose,' cut energy instruction."* The verdict should feel inevitable, not wishy-washy.
5. **Mixing languages within a single line.** Enforced in [[music/vedic|Vedic]], [[music/kabbalah|Kabbalah]], and family overlays. Language switching is structural, not word-by-word code-switch.

## The weighted crossover paradox

The system claims to blend 50% system + 25% Person 1 + 25% Person 2, yet keeps the centre of gravity (Anoushka, Sienna Rose, Dead Can Dance) **unmoved**. This is intentional.

> The weighting is not about diluting the centre. It's about the centre absorbing secondary colours without losing its identity.

Anoushka Shankar in 2026, hearing a Viennese folk melody or a Shanghainese opera phrase, should still sound like Anoushka. The secondary textures are **ghosts in the production, not co-leads**.

## What MiniMax does (and doesn't see)

MiniMax receives:

- A `minimaxPrompt` (concise mood / style / instrumentation language)
- The actual lyrics
- An emotion tag
- A vocalist descriptor

MiniMax does NOT receive:

- City names (banned; only country-level traditional / folk references make it through)
- Birthplace data raw
- The reading text
- Personal names
- Astrology terminology
- Age numbers or timeline arithmetic

The prompt does the cultural research; the LLM converts research into mood / instrumentation language; MiniMax produces the audio. The chain protects the audio model from leaking specifics that should remain implicit.

## The post-March-30 dense iteration

The user said *"thousands of modifications, worth a PhD in itself."* The git history shows:

- **27 commits in 23 minutes** on March 31 (00:14 to 00:37 UTC). Mostly [[music/gene-keys|Gene Keys]] and [[music/final-verdict|Final Verdict]]
- Some changes lived **1 to 5 minutes** before being reversed (the cultural-input experiment in Gene Keys synastry; the artist-list strip-and-restore)
- The session reads like a real-time edit, the user holding the keyboard, watching outputs, refining mid-session

This is the most volatile period in the whole prompt corpus. After April 15 (`7f21ce4f`, *"Sharpen hook and synastry preview readings"*) the music architecture stabilises. A test suite was added to `lyricsGeneration.ts`; the prompts have not changed materially since.

## Connections

- [[music|Music hub]]
- [[music/western]] · [[music/vedic]] · [[music/kabbalah]] · [[music/gene-keys]] · [[music/human-design]] · [[music/final-verdict]]
- [[topics/app-soundtrack]] (the *other* music: in-app theme tracks, separate philosophy)
- [[topics/per-language-llms]] (the same per-language dispatch logic governs the music prompt's language choice)
- [[decisions/native-script-voice-anchors]] (the language-anchoring move that propagated into music as the cultural-pairing rule)
