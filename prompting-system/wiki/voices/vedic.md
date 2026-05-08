---
title: Vedic
type: voice
system: vedic
narrator: Aghori witness at the cremation ground
created: 2026-05-08
updated: 2026-05-08
tags: [voice, vedic, jyotish]
---

# Vedic

Second of the five voices. Built right after [[western]]; the first system to demand its own metaphor world and refuse all Western mapping.

## Now

> An Aghori witness at the cremation ground, long enough to stop being afraid of it. Patient. Awed. Unflinching. Does not rescue, does not judge.

Lahiri sidereal, whole-sign houses, Vimshottari Dasha, Navamsha (D9), nakshatras, Vedic drishti, Rahu-Ketu axis. Outer planets excluded from the start. The chart is what the person looks like once the obstruction is removed.

## Timeline

*Note: the Vedic system existed from the first commit (2026-01-07). A 411-line writing guide ("left-handed perspective, fatalistic irony") was added on 2026-01-09 (`418ea42b`), the lineage of the Aghori-witness archetype already present at v0. The dates below trace the v2 narrator's emergence. See [[topics/january-foundation]].*

| Date | Move | What changed |
|---|---|---|
| 2026-02-16 | Vedic spec locked | Lahiri, whole-sign, Vimshottari, Navamsha set as the foundation |
| 2026-02-18 | Aghori witness narrator | Incarnation voice born; Zone 2 ban on technical vocabulary |
| 2026-03-10 | Music prompt added | Tantric texture, female vocalist, cultural overlay |
| 2026-03-22 | Synastry music overhaul | Ethno-ambient; birthCity from data, no name injection |
| 2026-03-30 | Goddess vocabulary | Rahu as decapitated woman still standing; Ketu as widow |
| 2026-04-08 | Unhinged Vedic fork | Same chart, full Sanskrit, escalated goddess voice |
| 2026-04-17 | Past-Life Contracts spawn | Vedic stripped to a two-person karmic contract; Swiss Ephemeris constrains the LLM |

*Want any row expanded into its own page? Say "expand <date>".*

## Dialectic

Three positions on the same chart engine:

| | 1 in a Billion | Unhinged | Past-Life Contracts |
|---|---|---|---|
| Vocabulary | banned in Zone 2 | full Sanskrit graha names | computed metadata only |
| Trust | the narrator's refusal | the goddess voice | the machine numbers |
| Scope | individual + synastry + incarnation | full system in noir tone | one unfinished vow, two souls |

## Branches researched

- **Ayanamsa**: Lahiri only, locked from genesis
- **Divisional charts**: D9 Navamsha (mandatory), D60 Shashtiamsha (Past-Life Contracts backend)
- **Dasha**: Vimshottari only
- **Houses**: whole-sign only
- **Synastry**: Ashtakuta engine attempted, then replaced. Canonical uses D9 overlay + Rahu-Ketu. Past-Life Contracts uses computed nodal axis only
- **Reference school**: Brihat Parashara Hora Shastra. Mahavidya goddesses. Left-hand (Aghori, Tantra) tradition texturally woven. No Jaimini, no KP

## Dead ends

- Ashtakuta vectorized scoring (replaced by deterministic nodal-axis logic)
- Bowie cut-up music prompts (replaced by Tantric storytelling)
- Cultural data hallucination in music (solved with birthCity lookup, not LLM research)
- Outer planets as significators (forbidden from first commit)
- Generic astrology phrasing ("great teacher", "lord of karma"), banned in Zone 2

## Texture

How this builder thinks about Vedic:

- Rivers: the person inside a current older than memory
- Fire: chapter burning through them
- Inheritance: weight carried unpacked
- The Moon as container, not emotion
- Nakshatra as the species you are before language
- "Dignity is transformation, not failure" (neecha as cooked metal)
- "Dasha as chapter felt in the body at 3am"

Refused: numeric scoring, prediction, redemption, teaching, abstraction.

The paradox: Zone 2 bans every Jyotish word, but the reader must never notice they are reading astrology.

## Sources

- `raw/1-in-a-billion/backend/prompt-layers/systems/vedic-individual.md`
- `raw/1-in-a-billion/backend/prompt-layers/systems/vedic-individual-incarnation.md`
- `raw/1-in-a-billion/backend/prompt-layers/systems/vedic-synastry.md`
- `raw/1-in-a-billion/backend/prompts/music/vedic-music-prompt.md`
- `raw/unhinged/toxic-app/backend/prompt-layers/style/style-guide-insert-vedic-voice.md`
- `raw/past-life-contracts/backend/src/prompts/layer2-mandate.ts`
- `raw/families-app/Families-app-src/backend/prompt-layers/style/style-guide-insert-vedic-voice.md`

Commits: `4cba79c2` · `af0553d2` · `c1abc2de` · `82d44f01` · `c595f9d9` · `6b4363e` · `dd0d34d`
