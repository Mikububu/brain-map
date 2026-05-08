---
title: Matching Algorithm
type: topic
created: 2026-05-08
updated: 2026-05-08
tags: [topic, matching, synastry, deterministic, philosophy]
---

# Matching Algorithm

The compatibility scoring engine inside [[apps/1-in-a-billion]]. The system most refined, most argued over. The user named it explicitly: *"the matching algorithm of one in a billion. I've been refining, changing this, discussing that."*

## Now

Six deterministic categories, scored from real cross-chart aspects:

- **Sexual Chemistry**
- **Emotional Security**
- **Communication**
- **Growth**
- **Power Dynamics**
- **Long-term Stability**

Plus a **verdict meta-engine** that aggregates all five system engines ([[western]], [[vedic]], [[human-design]], [[gene-keys]], [[kabbalah]]) into 16 verdict categories via weighted blending: Western 25%, Vedic 20%, HD 20%, GK 18%, Kabbalah 17%.

## Architecture

- **Western synastry engine** (`synastryEngine.ts`, ~900 lines): orb-weighted aspects + house overlays + sect; baseline 45; deltas per aspect
- **Four parallel engines** for Vedic, HD, Gene Keys, Kabbalah, same shape, different mechanics
- **Verdict meta-engine** (`verdictSynastryEngine.ts`): weighted blend of all five
- **Code → prompt symbiosis**: deterministic scores flow via `textWorker.ts` into LLM anchor keys. The prompt receives them as **truth constraints, not suggestions**. LLM stays within ±15 of the computed value.

## The pivotal move

**2026-03-10** (`fa8a327c`): *"feat: deterministic Western synastry engine replacing LLM-guessed compatibility scores."*

Before: ask the LLM to score each dimension. After: compute real cross-chart synastry deterministically; feed scores as hard anchors.

The Charmaine & Mike validation case proved it. Old approach clustered 60-80 across categories. New: full 0-100 spread.

> Communication **32** (was ~70). Growth **46** (was ~76). Overall **56** (was ~70).

## The earliest deterministic weighting

The Mar 10 engine was not the first deterministic synastry weighting in the user's work. A month earlier (Jan 19 to Feb 12), the user built a **Vedic-only toxicity engine** in [[apps/seeking-toxic-relationships]]: Rahu 25%, Saturn 15%, Mars 20%, 8th house 20%, 12th house 10%, Shared Nakshatras 5%, Lunar 5%. That codebase was abandoned, but the *principle* (computed weights, not LLM intuition) carried forward into the Mar 10 Western engine.

## Timeline

| Date | Move | What changed |
|---|---|---|
| 2026-03-10 | Deterministic Western engine | LLM-guessed scores killed |
| 2026-03-11 | Four parallel engines | Vedic, HD, GK, Kabbalah added in one deploy |
| 2026-03-11 | Score injection wired | `textWorker.ts` pushes deterministic block into all 5 prompts |
| 2026-03-11 | Baselines lowered | Western 50→25; HD 35→5; enables true 0-100 polarity |
| 2026-03-11 | Verdict meta-engine born | 16 categories from weighted 5-system blend |
| 2026-03-12 | Broaden scorers | Sun-Venus, Sun-Mars, Moon-Mars, Moon-Venus, ASC-Venus (Western). Pillar-balance weighting (Kabbalah) |
| 2026-03-12 | Raise baselines | Eliminate unrealistic 0-scores; toxic / shadow risk stays at 0 |
| 2026-03-12 | Vamachara reinterpretation | Vedic "difficult" combos as intensity, not failure. Nadi dosha = kundalini activation |
| 2026-03-21 | Hellenistic absorbed into Western | 7-category system folded in; fatalistic malefics inherited |

*Want any row expanded? Say "expand <date>".*

## What the 6 categories measure

- **Sexual Chemistry**: Venus-Mars, Pluto contacts, Uranus (addictive +10), Neptune (intoxicating illusion +5), 5th/8th house overlays
- **Emotional Security**: Moon-Moon (+14 / -12), Saturn-Moon, Saturn-Venus, 4th house
- **Communication**: Mercury contacts, Sun-Moon, Uranus-Mercury, 3rd house
- **Growth**: Jupiter contacts, Uranus (electrifying +7), North Node aspects, 9th house
- **Power Dynamics**: Saturn (grounding / oppression), Pluto (+8-10 intensity), 10th / MC
- **Long-term Stability**: Saturn-Venus +10 (commitment), Moon-Moon +14. **Saturn is the linchpin.**

## Dead ends

- **Vedic Ashtakuta vectorized engine** (8-point traditional): replaced within days by category-based scoring for parity with Western
- **7-category Hellenistic system**: merged into Western 2026-03-21; standalone files deleted
- **Scoreless house-overlay-only approach**: couldn't differentiate quality (exact conjunction vs. wide square)
- **LLM-anchored deflation correction**: pre-Mar-10 hack; obsolete once deterministic scores existed
- **Kabbalah equal-weight Sephiroth enumeration**: replaced by pillar-strength weighting (strong=2, moderate=1, weak=0.5)

## How it plays across the four apps

- **[[apps/1-in-a-billion]]**: full 6-category Western + 5-system verdict
- **[[apps/unhinged]]**: same engines; darker prose tone, shadow risk amplified
- **[[apps/past-life-contracts]]**: Western + Vedic engines, but only nodal axis weighed; other aspects = karmic echoes, not current-life mechanics
- **[[apps/families-app]]**: extends to family relationships. Adds Soul Contract Significance, Shadow Danger, Shared-Void Risk

## Gender-blind matching (the modernity move)

The deep matching engine has **zero references to `gender`** in any of its code. Verified across all five synastry engines (Western, Vedic, HD, Gene Keys, Kabbalah) and the verdict aggregator.

What this means in practice:

> *"The deep matching (the Ayurvedic deep matching) is not based on gender; even if we specify our own gender, we can match. I included the gender only so the long readings have the correct pronouns. Even this is worth PhD documentation, and it's very modern because you're not swiping for a gender. You are swiping for connections."*

The architectural commitment:

- **Gender does not enter the synastry computation.** Aspects, house overlays, sect, lots, dasha periods, nakshatra resonance, shadow / gift overlap, defined-vs-open centre interactions, sephiroth balance: none of these are gender-keyed
- **Gender is used only downstream**, in the long-form reading, to choose pronouns ("she," "he," "they")
- **The user picks who to swipe on by gender preference if they want**, but the matching itself does not require it. Two people of the same gender can be deeply karmically matched and the engine surfaces that match

The user's framing: *"You're not swiping for a gender. You are swiping for connections."*

This is one of the most distinctive architectural decisions in the suite. Most contemporary matching apps gate-match on gender first, then refine. The deep matching engine does the opposite: chart-first, connection-first; gender is a downstream pronoun question, not a filter.

See [[decisions/gender-blind-matching]] for the dedicated decision page.

## The historical lineage

The deep matching engine is descended from **Ashtakuta**, the eight-fold Vedic compatibility system used in arranged marriages for thousands of years. Two inversions distinguish the modern version: **gender-blind** (traditional Ashtakuta is gendered) and **happiness-oriented** (traditional Ashtakuta optimises for longevity, progeny, family welfare, dharma). For the full lineage, the philosophical inversion, and the comparison with Hinge / Tinder, see [[topics/matching-philosophy]].

## Texture

How this builder thinks about matching:

- **The deterministic turn was existential.** LLMs are ornamental when they guess; computation is the skeleton.
- **Matching is unforgiving.** Wrong advice ruins lives. Refuse to inflate scores to please.
- **32 / 100 is a real answer, not a sales tactic.** (Charmaine & Mike)
- **Same planetary contact can be heaven or hell.** Computation names it; prose decides the spin. (Uranus-challenging Venus = "addictive electric charge.")

Refused: false consensus, score inflation, LLM intuition pretending to be math, sales-driven 60-80 clustering.

The paradox: **perfect synastry is rare and boring; controversy in the 35-55 gray zone is honest and drives the deeper reading.**

## Sources

- `raw/1-in-a-billion/backend/src/services/synastryEngine.ts`
- `raw/1-in-a-billion/backend/src/services/vedicSynastryEngine.ts`
- `raw/1-in-a-billion/backend/src/services/verdictSynastryEngine.ts`
- `raw/1-in-a-billion/backend/src/services/{hd,geneKeys,kabbalah}SynastryEngine.ts`
- `raw/1-in-a-billion/backend/src/scripts/shared/compatibilityScoring.ts`
- `raw/1-in-a-billion/backend/src/workers/textWorker.ts`

Commits: `fa8a327c` · `6cb7ca5e` · `06e7f146` · `3cee6f75` · `09104683` · `0ca4c0a7` · `ca728d3c` · `cd2e6f95` · `843f4989` · `ae467290`
