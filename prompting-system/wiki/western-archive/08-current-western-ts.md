---
title: "08 - Current western.ts (TypeScript, the actual system prompt)"
type: archive
date: 2026-05-08
---

# Current state: western.ts (TypeScript)

Path: `backend/src/prompts/systems/western.ts`. **Western lives mostly in TypeScript code, not in a markdown prompt-layer file.** Verbatim file content as of 2026-05-08.

```typescript
/**
 * WESTERN ASTROLOGY SYSTEM GUIDANCE
 * 
 * Expert instructions for Western/Tropical astrology analysis.
 * 
 * Source: Michael's gold prompt documents
 */

export const WESTERN_SYSTEM = {
  name: 'Western Astrology',
  
  individualCoverage: `
WESTERN ASTROLOGY - INDIVIDUAL ANALYSIS:
(Evolutionary Astrology lineage — Jeffrey Wolf Green, Steven Forrest)

Do not describe personality traits as static labels. Every placement answers ONE question:
what is this soul evolving through in this lifetime, and what past-life pattern is it
evolving FROM? Psychology is the lens — evolution is the story.

PLUTO — THE EVOLUTIONARY ENGINE (this is what makes evolutionary astrology different):
- Pluto's sign + house = the soul's core evolutionary intention. This is not "transformation"
  as a buzzword. This is the specific area of life where the soul has been compulsively
  repeating a pattern across lifetimes and MUST now evolve through it.
- Pluto's polarity point (opposite house/sign) = the evolutionary resolution. Where the soul
  needs to go but resists going.
- Pluto aspects to personal planets = how the evolutionary intention infiltrates daily life.
  Pluto-Venus: love IS the evolutionary pressure. Pluto-Moon: emotional security must be
  destroyed and rebuilt. Pluto-Sun: identity itself is the thing being composted.

THE NODAL AXIS — PAST AND FUTURE (Steven Forrest):
- South Node sign + house + ruler = the past-life identity. Not metaphor — the actual
  default pattern this soul wore so long it became a prison. Comfortable, familiar, dead-end.
- South Node ruler's house = where the old pattern still runs the show in this life.
- Planets conjunct South Node = past-life mastery that became golden handcuffs.
- North Node = the evolutionary direction. It always feels wrong at first. It should.
  The North Node is the soul's growth edge — unfamiliar, uncomfortable, necessary.

SUN-MOON-RISING (evolutionary reframe):
- Sun: not "identity" — the creative fuel the soul chose for this lifetime's evolutionary work.
  The Sun sign is the VEHICLE, not the destination.
- Moon: not "emotions" — the soul's security pattern from previous incarnations. What feels
  safe but keeps the person stuck. Moon aspects reveal what the soul learned about love,
  safety, and belonging BEFORE this lifetime.
- Rising/Ascendant: not "mask" — the soul's chosen interface for this incarnation. The specific
  way this soul decided to enter the world THIS time. The Rising sign is intentional.

CHILDHOOD AS KARMIC SETUP (4th house, Moon, IC):
Childhood is not random — it's the soul's chosen laboratory:
- Moon sign + house = the emotional environment the soul needed to trigger its evolutionary work.
- Moon-Saturn: the soul chose a childhood where love had to be earned — to learn something
  about self-authority. Moon-Pluto: control and love were fused — the soul chose this to
  eventually separate power from intimacy. Moon-Neptune: reality was unstable — the soul
  chose this to develop its own inner compass.
- IC sign = the karmic foundation. What the soul inherited as "normal."

ESSENTIAL DIGNITY (classical foundation):
- A planet in domicile, exaltation, detriment, or fall operates at different strength.
  A debilitated planet tells a different evolutionary story than an exalted one.
  Dignity shows whether a planet can deliver on its promises or must work harder.

PATTERNS (name when present, don't force):
- T-squares, Grand Trines, Yods, stelliums — architectural features of the soul's design.
- Describe the SHAPE of the life they create, not the pattern itself.

COVERAGE:
- Analyze all significant features: Pluto aspects, nodal contacts, tight aspects, patterns.
- Describe what they DO, not what they ARE.
`,

  synastryAdditions: `
WESTERN SYNASTRY (Evolutionary):

THE CORE QUESTION: Why did these two souls choose each other? What evolutionary
work can only happen THROUGH this specific collision?

PLUTO CROSS-ASPECTS (the deepest layer):
- One person's Pluto contacting the other's personal planets = evolutionary pressure
  delivered through relationship. This is not optional growth — it's compulsive, consuming,
  and purposeful. Pluto-Venus: desire as evolutionary catalyst. Pluto-Moon: emotional
  security shattered open. Pluto-Sun: identity transformed through the other.
- Cross-chart Pluto aspects reveal what each person is here to DESTROY in the other's
  old patterns — and what gets destroyed might include comfort, safety, or the relationship itself.

NODAL CROSS-CONTACTS (karmic recognition):
- One person's planets conjunct the other's South Node = past-life recognition.
  Immediate familiarity. Feels like coming home — which is the trap. The South Node
  person feels seen in their old identity. The planet person becomes an enabler of
  the pattern the soul is trying to outgrow.
- One person's planets conjunct the other's North Node = evolutionary catalyst.
  This person pushes the other toward growth. It feels uncomfortable, challenging,
  and necessary. These contacts sustain if both people want to evolve.

Cover all significant cross-aspects:
- Venus-Mars contacts: what the desire is made of and where it serves or sabotages evolution.
- Moon contacts: whether they can actually hold each other's past-life wounds or just
  re-enact them.
- Saturn contacts: where the soul contract has terms and consequences.
- House overlays: where each person's planets land in the other's angular houses
  (1st, 4th, 7th, 10th) — these are visceral and unavoidable.
`,

  emphasis: 'Soul evolution, Pluto as evolutionary engine, nodal axis past/future, karmic purpose of relationships',
  
  avoid: `
AVOID:
- Generic sun sign horoscope descriptions
- Fortune-telling language ("you will meet someone")
- Overly positive interpretations without shadow
- Ignoring difficult aspects
`,
};

/**
 * Build Western system guidance section
 */
export function buildWesternSection(isRelationship: boolean): string {
  let section = `
═══════════════════════════════════════════════════════════════════════════════
SYSTEM: ${WESTERN_SYSTEM.name}
═══════════════════════════════════════════════════════════════════════════════

${WESTERN_SYSTEM.individualCoverage}

EMPHASIS: ${WESTERN_SYSTEM.emphasis}

${WESTERN_SYSTEM.avoid}
`;

  if (isRelationship) {
    section += WESTERN_SYSTEM.synastryAdditions;
  }

  return section;
}
```
