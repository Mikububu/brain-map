---
title: Gender-Blind Matching (Connection Over Gender)
type: decision
date: ongoing
created: 2026-05-08
updated: 2026-05-08
tags: [decision, matching, modernity, philosophy, ayurvedic]
---

# Gender-Blind Matching

Not a single commit; a structural commitment that holds across the entire deep-matching engine. Verified by code: **zero references to `gender`** in any of the five synastry engines.

## The user's framing

> *"The deep matching, the Ayurvedic deep matching, is not based on gender; even if we specify our own gender, we can match. I included the gender only so the long readings have the correct pronouns. Even this is worth PhD documentation, and it's very modern because you're not swiping for a gender. You are swiping for connections."*

## What's gender-blind

The five synastry engines (Western, Vedic, HD, Gene Keys, Kabbalah) compute compatibility from:

- Cross-chart aspects (orb-weighted)
- House overlays (4th, 5th, 7th, 8th, 10th especially)
- Sect (day / night chart distinction)
- Nakshatra resonance (Vedic)
- Defined / open centre interactions (Human Design)
- Shadow / gift overlap (Gene Keys)
- Sephiroth balance, pillar weighting, klipot exposure (Kabbalah)

**None of these are gender-keyed.** The chart is not a gender. The aspects are not gendered. The synastry mechanics are gender-blind by construction.

## What gender IS used for

Downstream of matching, in the **long-form reading**, gender informs:

- Pronouns ("she," "he," "they")
- Voice anchor selection in some cases (gendered vocalist preference for music)
- Cultural pronoun conventions in non-English readings

Gender is a **rendering parameter**, not a matching filter.

## The modernity move

Most contemporary matching apps gate on gender first ("I want to date men / women / both"), then rank within that filter. The deep-matching engine does the opposite:

- **Chart-first**: rank by karmic resonance and synastry compatibility
- **Connection-first**: surface deep matches regardless of gender
- **Pronoun is downstream**: gender enters only at the rendering layer

This is an architectural commitment, not a configuration option. The engine *cannot* do gender-keyed matching even if asked, because the engines do not see gender as input.

## Why "Ayurvedic"

The user uses "Ayurvedic" colloquially to mean the deep / Vedic / karmic-tradition flavour of the matching, not the medical system. The actual implementation is the [[topics/matching-algorithm|deterministic synastry engine]] (Mar 10, `fa8a327c` and successors), with the Vedic engine carrying particular weight given the karmic / nakshatra emphasis. *"Ayurvedic deep matching"* signals: matching that takes karma seriously, that sees beyond surface preference, that treats the chart as the primary unit of resonance.

## The user's claim

> *"Even this is worth PhD documentation."*

Not a hyperbole. Gender-blind matching is a deliberate inversion of the contemporary matching-app default. It's not a bug, not an oversight, not a "we'll add a filter later." It's an explicit architectural stance about what swiping is *for*: connection, not gender.

## Connections

- [[topics/matching-algorithm]] (the deep-matching engine this commits sit on top of)
- [[decisions/deterministic-synastry-engine]] (the Mar 10 pivot that established chart-first-not-LLM-first; gender-blind is its philosophical extension)
- [[apps/1-in-a-billion]] (the canonical app implementing this)
- [[apps/unhinged]] (inherits gender-blind matching)
- [[topics/four-app-constellation]] (where this stance fits in the suite-wide philosophy)

## Sources

Verified by `grep -r gender raw/1-in-a-billion/backend/src/services/{synastry,vedic,hd,geneKeys,kabbalah}*Engine.ts compatibilityScoring.ts` returning **zero matches**.

User testimony, 2026-05-08.
