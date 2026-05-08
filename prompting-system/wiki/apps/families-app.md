---
title: Families-app
type: app
created: 2026-05-08
updated: 2026-05-08
tags: [app, fork, relational, family-myth]
---

# Families-app

The relational fork. Where the other three apps read individuals (or pairs), this one reads a **family unit as a single living organism**.

## What it is

A reader for 1 to 4 people analysed together. Outputs a 3rd-person family myth narrative. Includes a "ghost field" for deceased members, who shape the reading without being its analytical subject. Word count scales with members: 8000 base + 1200 per member + 600 per pair.

## Tonal posture

**Empathetic family myth.** Removed the provocative literary anchors (Henry Miller, Elfriede Jelinek). Replaced with grief-and-inheritance writers: Marilynne Robinson, W.G. Sebald, Annie Ernaux. The sexual mechanism block was *deliberately disabled* in this fork. The voice is tenderness directed at attachment, lineage, family role pressure, transgenerational inheritance.

## Voices in use

| Voice | Notable variation |
|---|---|
| [[vedic]] | Ashtakuta + Navamsha resonance for pair dynamics; transgenerational karma framing |
| [[kabbalah]] | Klipoth reframed as *"shell that became the self"*; Tikkun as *"repetition signature in the body, in the reflexes"* |
| [[gene-keys]] | "Relational habitat" added: shadow mating patterns, gift compatibility, gift-transmission across lineage |
| [[human-design]] | Circuits as family nervous systems; conditioning exposed across the family graph |
| [[western]] | Present, but family-myth tone (3rd person, no "you" address) |

## Architecture

- Same three-layer architecture as canonical, plus:
  - `familyMode.ts`: routing for `docType: 'family'`. Detects child roles, deceased members, relationship tags
  - `family.ts`: family reading structure with dynamic word-count scaling
  - `chartProvocations.ts`: relational stress-tests (parent-child karmic debt, sibling inheritance splits, multigenerational trauma)
  - `buildFamilyChartData()`: cross-synastry charts across all family members
- **One job = one system = one family document.** Not N separate readings; the family is the unit.
- Backend: Hono on Fly. Bundle ID: `app.families`.

## Origin

- First commit: **2026-04-10** (`9f067e7`, "Initial commit: Families app with unified reading flow")
- Tone rewrite: **2026-04-12** (`de30f75`, "Total tone rewrite: empathetic family philosophy across all layers"). This is the moment the app's voice diverges hardest from canonical.
- Pipeline rewrite: **2026-04-12** (`0ec0017`, "Rewrite reading pipeline: 1 job = 1 system = 1 family document")
- Conversational intake: **2026-04-28** (`c3606c8`)

## What makes it specific

- **The only app with the sexual mechanism block disabled.** A deliberate philosophical move at the tone rewrite.
- **3rd-person narrative.** No "you" address. The family is observed, not coached.
- **Ghost field**: deceased members flow through birth data and prompt context, shaping the reading without being its analytical subject.
- **Empathy anchors over provocation anchors.** Robinson / Sebald / Ernaux instead of Miller / Jelinek.
- **Synastry scoring categories specific to family**: Soul Contract Significance, Shadow Danger, Shared-Void Risk.

## Connection back to engine

Inherits from [[apps/1-in-a-billion]]:
- Voice/style/system architecture in `prompt-layers/`
- Multi-language rewrite pipeline
- Vedic depth (Ashtakuta + Navamsha + D9)
- Final-verdict synthesis layer

Diverges:
- Layer 2 system prompts rewritten from individual-centric (*"your Shani"*) to field-centric (*"inherited Shani debt"*)
- Sexual mechanism block disabled
- Empathy anchors swapped in
- Relational scope (1-4 people) instead of individual or pair

## Sources

- `raw/families-app/Families-app-src/backend/src/prompts/familyMode.ts`
- `raw/families-app/Families-app-src/backend/src/prompts/structures/family.ts`
- `raw/families-app/Families-app-src/backend/src/prompts/chartProvocations.ts`
- `raw/families-app/Families-app-src/backend/prompt-layers/style/` (all four voice inserts, family-toned)
