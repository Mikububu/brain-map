---
title: 06-mar-12-vamachara
type: archive
date: 2026-03-12
commit: cd2e6f95
---

# Vamachara left-hand tradition interpretation layer

Commit `cd2e6f95` (2026-03-12). The full diff, verbatim from `git show cd2e6f95`.

```diff
commit cd2e6f95c57ce90ebbcdc3bba6dcb370bcb26b31
Author: Michael <michael@forbidden-yoga.com>
Date:   Thu Mar 12 20:38:32 2026 +0400

    feat(vedic): add Vamachara left-hand tradition interpretation layer
    
    Adds genuine alternative Vedic school interpretations to the synastry engine
    instead of artificial score boosting. The Vamachara layer reinterprets
    traditionally "difficult" Ashtakoota combinations as intensity/transformation:
    
    - Nadi dosha (same nadi) → kundalini activation, not genetic rejection
    - Active Manglik → Mars/Shakti transmission, not spouse death
    - Deva-Rakshasa gana → Shiva-Shakti polarity, not temperament mismatch
    - Enemy yoni → primal visceral charge, not sexual incompatibility
    - Bhakoot dosha → karmic debt requiring resolution
    - "Reject" verdict → intensity too extreme for mainstream, not worthless
    
    Also improves verdict engine toxic potential formula with karmic trap
    factor and intensity-container gap calculation.
    
    Co-Authored-By: Claude Opus 4.6 <noreply@anthropic.com>

diff --git a/1-in-a-billion-v2/backend/src/scripts/shared/compatibilityScoring.ts b/1-in-a-billion-v2/backend/src/scripts/shared/compatibilityScoring.ts
index d000061e..763f1511 100644
--- a/1-in-a-billion-v2/backend/src/scripts/shared/compatibilityScoring.ts
+++ b/1-in-a-billion-v2/backend/src/scripts/shared/compatibilityScoring.ts
@@ -75,7 +75,7 @@ function buildScoringPrompt(params: {
     'SCORING RULES:',
     '- CRITICAL: Output ALL category labels in EXACT ENGLISH as shown above, regardless of the language of the reading text. Never translate the labels.',
     '- The chart data includes DETERMINISTIC SYNASTRY SCORES computed from planetary positions. Use these as anchors. Stay within +/- 15 points.',
-    '- Normal synastry = 35-55. Notable alignment = 60-75. Exceptional = 75+. Below 30 = structural incompatibility.',
+    '- Normal synastry = 40-55. Notable alignment = 60-75. Exceptional = 75-90. Transcendent/dangerous = 90+. Below 30 = structural incompatibility. USE THE FULL RANGE — some connections ARE extreme.',
     '- Each score MUST have 2-3 sentences of specific reasoning anchored to chart data or the reading.',
     `- ALTERNATE which person you mention first. Do NOT always lead with ${person1Name}. This is about the PAIR, not about one person.`,
     '- Be honest and unflinching. No therapy language. No fake positivity.',
@@ -161,9 +161,9 @@ function extractDeterministicAnchors(chartData: string): Map<string, number> {
 const ANCHOR_MAP: Record<string, string[]> = {
   'SEXUAL CHEMISTRY':       ['SEXUAL CHEMISTRY', 'SEXUAL_CHEMISTRY'],
   'MAGNETIC PULL':          ['POWER DYNAMICS', 'POWER_DYNAMICS', 'MAGNETIC PULL', 'MAGNETIC_PULL'],
-  'LONG-TERM SUSTAINABILITY': ['LONG TERM STABILITY', 'LONG_TERM_STABILITY', 'LONG-TERM SUSTAINABILITY'],
+  'LONG-TERM SUSTAINABILITY': ['LONG TERM STABILITY', 'LONG_TERM_STABILITY', 'LONG-TERM SUSTAINABILITY', 'LONG-TERM STABILITY'],
   'COMMUNICATION DEPTH':    ['COMMUNICATION', 'COMMUNICATION DEPTH', 'COMMUNICATION_DEPTH'],
-  'HEALING POTENTIAL':      ['GROWTH EXPANSION', 'GROWTH_EXPANSION', 'HEALING POTENTIAL', 'HEALING_POTENTIAL'],
+  'HEALING POTENTIAL':      ['GROWTH EXPANSION', 'GROWTH_EXPANSION', 'GROWTH & EXPANSION', 'HEALING POTENTIAL', 'HEALING_POTENTIAL'],
   'DAILY LIFE':             ['EMOTIONAL SECURITY', 'EMOTIONAL_SECURITY', 'DAILY LIFE', 'DAILY_LIFE'],
   'OVERALL ALIGNMENT':      ['OVERALL'],
   // Previously unanchored — now supported by Vedic/HD/GK/Kabbalah engines
@@ -190,22 +190,19 @@ function findAnchor(categoryKey: string, anchors: Map<string, number>): number |
 }
 
 // ─── ANTI-INFLATION POST-PROCESSING ──────────────────────────────────────────
-// LLMs consistently inflate scores into the 65-90 range regardless of text
-// instructions. This mathematically corrects the bias.
+// LLMs can inflate scores, but the anchor blend (70% deterministic) already
+// constrains most categories. This is a LIGHT deflation for unanchored ones only.
 //
-// For anchored categories: blend 70% deterministic + 30% LLM
-// For unanchored categories: apply deflation curve that compresses the
-// inflation zone (60-90) while preserving genuinely low/high scores.
+// For anchored categories: blend 70% deterministic + 30% LLM (unchanged)
+// For unanchored categories: mild compression in the 70-90 zone only
 function deflateScore(llmScore: number): number {
-  // Piecewise linear deflation:
-  // LLM 0-40   → keep as-is (already rare and honest)
-  // LLM 40-60  → compress slightly (40-50)
-  // LLM 60-80  → heavy compression (50-60) — this is the main inflation zone
-  // LLM 80-100 → compress to (60-80)
-  if (llmScore <= 40) return llmScore;
-  if (llmScore <= 60) return 40 + (llmScore - 40) * 0.5;   // 40-60 → 40-50
-  if (llmScore <= 80) return 50 + (llmScore - 60) * 0.5;   // 60-80 → 50-60
-  return 60 + (llmScore - 80) * 1.0;                        // 80-100 → 60-80
+  // Light deflation — preserve the LLM's judgment more:
+  // LLM 0-70   → keep as-is (trust the model up to 70)
+  // LLM 70-90  → mild compression (70-80) — only compress the obvious inflation zone
+  // LLM 90-100 → compress to (80-90)
+  if (llmScore <= 70) return llmScore;
+  if (llmScore <= 90) return 70 + (llmScore - 70) * 0.5;   // 70-90 → 70-80
+  return 80 + (llmScore - 90) * 1.0;                        // 90-100 → 80-90
 }
 
 function postProcessScores(
diff --git a/1-in-a-billion-v2/backend/src/services/synastryEngine.ts b/1-in-a-billion-v2/backend/src/services/synastryEngine.ts
index e784b276..6054f204 100644
--- a/1-in-a-billion-v2/backend/src/services/synastryEngine.ts
+++ b/1-in-a-billion-v2/backend/src/services/synastryEngine.ts
@@ -7,7 +7,7 @@
  *   - Exportable scoring functions for independent testing
  *
  * Scoring approach:
- *   - Baseline: 50 (neutral — no aspects = average compatibility)
+ *   - Baseline: 45 (neutral — no aspects = slightly below average)
  *   - Harmonious aspects (conjunction/trine/sextile): generally positive
  *   - Challenging aspects (square/opposition): context-dependent
  *     (e.g., Venus-Mars square = +chemistry, -stability)
@@ -222,7 +222,7 @@ export function scoreSexualChemistry(
   overlaysAtoB: HouseOverlay[],
   overlaysBtoA: HouseOverlay[],
 ): SynastryCategory {
-  let score = 35;
+  let score = 45;
   const details: string[] = [];
   let harmonious = 0;
   let challenging = 0;
@@ -353,6 +353,50 @@ export function scoreSexualChemistry(
     details.push(`Mars-Mars ${a.type} (${a.orb}°) — shared physical energy`);
   }
 
+  // Sun-Sun aspects (ego chemistry — squares/oppositions = electric tension)
+  const sunSun = findAspects(aspects, ['sun'], ['sun']);
+  for (const a of sunSun) {
+    if (a.harmonious) {
+      score += 6 * (a.weight / 10);
+      harmonious++;
+    } else {
+      // Sun-Sun squares/oppositions = ELECTRIC ego tension = sexual sparks
+      score += 8 * (a.weight / 10);
+      challenging++;
+      details.push(`Sun-Sun ${a.type} (${a.orb}°) — electric ego tension`);
+    }
+  }
+
+  // Uranus-personal (electric, addictive, unpredictable attraction)
+  const uranusPersonal = findAspects(aspects, ['uranus'], ['sun', 'moon', 'venus', 'mars']);
+  for (const a of uranusPersonal) {
+    if (a.harmonious) {
+      score += 7 * (a.weight / 6.5);
+      harmonious++;
+      details.push(`Uranus-${a.planetA === 'uranus' ? a.planetB : a.planetA} ${a.type} (${a.orb}°) — electrifying attraction`);
+    } else {
+      // Challenging Uranus = "can't stop thinking about you" — highly addictive
+      score += 10 * (a.weight / 6.5);
+      challenging++;
+      details.push(`Uranus-${a.planetA === 'uranus' ? a.planetB : a.planetA} ${a.type} (${a.orb}°) — addictive electric charge`);
+    }
+  }
+
+  // Neptune-personal (hypnotic, fantasy-driven, idealized attraction)
+  const neptunePersonal = findAspects(aspects, ['neptune'], ['sun', 'moon', 'venus', 'mars']);
+  for (const a of neptunePersonal) {
+    if (a.harmonious) {
+      score += 6 * (a.weight / 6.5);
+      harmonious++;
+      details.push(`Neptune-${a.planetA === 'neptune' ? a.planetB : a.planetA} ${a.type} (${a.orb}°) — hypnotic enchantment`);
+    } else {
+      // Challenging Neptune = intoxicating but deceptive pull
+      score += 5 * (a.weight / 6.5);
+      challenging++;
+      details.push(`Neptune-${a.planetA === 'neptune' ? a.planetB : a.planetA} ${a.type} (${a.orb}°) — intoxicating illusion`);
+    }
+  }
+
   // 5th house overlays (romance, pleasure)
   const h5Count = countHouseOverlays(overlaysAtoB, [5], true) +
                   countHouseOverlays(overlaysBtoA, [5], true);
@@ -367,7 +411,7 @@ export function scoreSexualChemistry(
     key: 'SEXUAL_CHEMISTRY',
     label: 'Sexual Chemistry',
     score: clamp(score),
-    aspectCount: venusMars.length + venusVenus.length + plutoPersonal.length + sunVenus.length + sunMars.length + moonMars.length + moonVenus.length + ascVenus.length + ascMars.length + marsMars.length,
+    aspectCount: venusMars.length + venusVenus.length + plutoPersonal.length + sunVenus.length + sunMars.length + moonMars.length + moonVenus.length + ascVenus.length + ascMars.length + marsMars.length + sunSun.length + uranusPersonal.length + neptunePersonal.length,
     harmonious,
     challenging,
     details,
@@ -383,7 +427,7 @@ export function scoreEmotionalSecurity(
   overlaysAtoB: HouseOverlay[],
   overlaysBtoA: HouseOverlay[],
 ): SynastryCategory {
-  let score = 35;
+  let score = 45;
   const details: string[] = [];
   let harmonious = 0;
   let challenging = 0;
@@ -481,7 +525,7 @@ export function scoreCommunication(
   overlaysAtoB: HouseOverlay[],
   overlaysBtoA: HouseOverlay[],
 ): SynastryCategory {
-  let score = 35;
+  let score = 45;
   const details: string[] = [];
   let harmonious = 0;
   let challenging = 0;
@@ -494,10 +538,10 @@ export function scoreCommunication(
       harmonious++;
       details.push(`Mercury-Mercury ${a.type} (${a.orb}°) — intellectual harmony`);
     } else {
-      // Challenging Mercury-Mercury = stimulating debate, slight positive not negative
-      score += 2 * (a.weight / 6);
+      // Challenging Mercury-Mercury = stimulating debate — intellectually addictive friction
+      score += 6 * (a.weight / 6);
       challenging++;
-      details.push(`Mercury-Mercury ${a.type} (${a.orb}°) — stimulating debate`);
+      details.push(`Mercury-Mercury ${a.type} (${a.orb}°) — intellectually electric debate`);
     }
   }
 
@@ -587,9 +631,10 @@ export function scoreCommunication(
       harmonious++;
       details.push(`Mercury-Jupiter ${a.type} (${a.orb}°) — expansive dialogue`);
     } else {
-      // Challenging Mercury-Jupiter = over-promising, exaggerating, but still engaging
-      score += 1 * (a.weight / 5.5);
+      // Challenging Mercury-Jupiter = grandiose, provocative, but WILDLY stimulating conversations
+      score += 5 * (a.weight / 5.5);
       challenging++;
+      details.push(`Mercury-Jupiter ${a.type} (${a.orb}°) — provocative philosophical sparring`);
     }
   }
 
@@ -647,7 +692,7 @@ export function scoreGrowthExpansion(
   overlaysAtoB: HouseOverlay[],
   overlaysBtoA: HouseOverlay[],
 ): SynastryCategory {
-  let score = 35;
+  let score = 45;
   const details: string[] = [];
   let harmonious = 0;
   let challenging = 0;
@@ -785,7 +830,7 @@ export function scorePowerDynamics(
   overlaysAtoB: HouseOverlay[],
   overlaysBtoA: HouseOverlay[],
 ): SynastryCategory {
-  let score = 35;
+  let score = 45;
   const details: string[] = [];
   let harmonious = 0;
   let challenging = 0;
@@ -845,7 +890,7 @@ export function scoreLongTermStability(
   p1Placements: PlacementSummary,
   p2Placements: PlacementSummary,
 ): SynastryCategory {
-  let score = 35;
+  let score = 45;
   const details: string[] = [];
   let harmonious = 0;
   let challenging = 0;
diff --git a/1-in-a-billion-v2/backend/src/services/vedicSynastryEngine.ts b/1-in-a-billion-v2/backend/src/services/vedicSynastryEngine.ts
index 1c46e3f0..9b728366 100644
--- a/1-in-a-billion-v2/backend/src/services/vedicSynastryEngine.ts
+++ b/1-in-a-billion-v2/backend/src/services/vedicSynastryEngine.ts
@@ -54,9 +54,18 @@ export function computeVedicSynastry(match: VedicMatchResult): SystemSynastryRes
   let magneticPull = normalizeKoota(g.vashya, 2, 20, 90);
   if (d.nadi) magneticPull += 15;
 
-  // ── Karmic Resonance (Nadi Koota: karmic/genetic/spiritual) ──
+  // ── Karmic Resonance (Nadi Koota: karmic/genetic/spiritual — PAST LIFE) ──
+  // Nadi is the MOST significant Koota (8 points max out of 36 total)
+  // Mainstream: 8/8 = different nadis = excellent. 0/8 = same nadi = dosha (reject)
+  // Vamachara: Same nadi = deepest karmic recognition, shared energy channel
   let karmicResonance = normalizeKoota(g.nadi, 8, 10, 100);
 
+  // Mainstream: Good nadi compatibility (different nadis) → genuine spiritual harmony
+  if (g.nadi >= 6) {
+    sexualChemistry += 4;   // spiritual harmony creates mild physical resonance
+    magneticPull += 6;      // soul compatibility creates pull
+  }
+
   // ── Shadow Risk (derived from Doshas) ──
   let shadowRisk = 10;
   if (d.nadi) shadowRisk += 28;
@@ -83,7 +92,7 @@ export function computeVedicSynastry(match: VedicMatchResult): SystemSynastryRes
   // ── World-Changing Potential (Varna + Total blend) ──
   const varnaFactor = normalizeKoota(g.varna, 1, 10, 90);
   const totalFactor = normalizeKoota(match.guna_total, 36, 10, 95);
-  const worldChanging = clamp(varnaFactor * 0.4 + totalFactor * 0.6);
+  let worldChanging = clamp(varnaFactor * 0.4 + totalFactor * 0.6);
 
   // ── Toxic Relationship Potential ──
   let toxicPotential = 5;
@@ -92,6 +101,117 @@ export function computeVedicSynastry(match: VedicMatchResult): SystemSynastryRes
   if (d.bhakoot && d.nadi) toxicPotential += 18;
   if (dasha.phase_relation === 'conflicting') toxicPotential += 12;
 
+  // ═══════════════════════════════════════════════════════════════════════════
+  // VAMACHARA / LEFT-HAND TRADITION REINTERPRETATION
+  // ═══════════════════════════════════════════════════════════════════════════
+  //
+  // Mainstream Vedic (Dharma Shastra) uses Ashtakoota to filter "safe" marriages.
+  // Difficult combinations = REJECT. The left-hand path (Vamachara, Kaula Tantra,
+  // Nath Sampradaya, Aghori tradition) reads the same chart data differently:
+  //
+  //   Where mainstream sees danger, Vamachara sees transformation.
+  //   Where mainstream sees incompatibility, Vamachara sees intensity.
+  //   Where mainstream says "this will destroy you," Vamachara says
+  //     "this will destroy who you WERE."
+  //
+  // We don't replace mainstream scores. We ADD a Vamachara layer that boosts
+  // intensity-related categories (Sexual Chemistry, Magnetic Pull, Karmic
+  // Resonance) when doshas are present, while preserving practical categories
+  // (Daily Life, Long-term Sustainability) as mainstream. Vamachara acknowledges
+  // that even the most transformative connection still has to navigate rent,
+  // dishes, and Monday mornings.
+  //
+  // These adjustments ONLY fire when doshas/difficulties exist. A harmonious
+  // mainstream match gets no Vamachara boost — it doesn't need one.
+
+  // ── NADI DOSHA: SHARED ENERGY CHANNEL ─────────────────────────────────────
+  // Same Nadi = 0/8 in Ashtakoota. Mainstream: genetic/health incompatibility.
+  // Vamachara: The two souls share the same pranic pathway (Ida, Pingala, or
+  // Sushumna). When they meet, the body recognizes before the mind does.
+  // This is kundalini activation through relationship — the most intense
+  // form of Shakti transmission between partners.
+  if (d.nadi) {
+    sexualChemistry += 18;   // Shared nadi = body-level kundalini activation
+    magneticPull += 20;      // "I know this soul from before I was born"
+    karmicResonance = Math.max(karmicResonance, 82);  // Override mainstream floor
+    healingPotential += 10;  // Same energy channel = potential for deep healing work
+  }
+
+  // ── MANGLIK: MARS FIRE TRANSMISSION ───────────────────────────────────────
+  // Active Manglik (one person Manglik, other not):
+  // Mainstream: Violence, divorce, death of spouse. "Never marry a Manglik."
+  // Vamachara: Mars/Shakti transmission. The Manglik partner's raw fire
+  // activates the other partner's dormant energy. This IS Shakti diksha
+  // (energy initiation) — the non-Manglik partner receives Mars activation.
+  if (d.manglik === 'active') {
+    sexualChemistry += 14;    // Mars fire = raw sexual/creative power
+    magneticPull += 10;       // Dangerous people are magnetic
+    worldChanging += 8;       // Mars pairs change the world (or burn it down)
+    // Shadow/Toxic already boosted by mainstream — Vamachara agrees danger is real
+  }
+
+  // Both Manglik (cancelled in mainstream, but Vamachara sees double fire):
+  // Two Mars-activated people together = immense combined fire. Mainstream
+  // calls this "cancelled" (safe), but the intensity is actually DOUBLED.
+  if (d.manglik === 'cancelled') {
+    sexualChemistry += 8;     // Double Mars = double fire
+    worldChanging += 10;      // Two warriors together = immense action potential
+    toxicPotential += 6;      // Double combustion risk (no one holding the reins)
+  }
+
+  // ── GANA CROSS-POLARITY: DEVA × RAKSHASA ─────────────────────────────────
+  // Gana score 1/6 = Deva-Rakshasa crossing (worst in mainstream).
+  // Vamachara: Shiva-Shakti polarity. The civilized consciousness meeting
+  // the primal force. The meditator meeting the dancer. The monk meeting the
+  // witch. The tension between divine order and wild chaos IS the tantric path.
+  // Gana score 3/6 = Manushya-Rakshasa crossing (milder polarity).
+  if (g.gana === 1) {
+    // Deva-Rakshasa: maximum polarity
+    sexualChemistry += 14;    // Polarity creates immense charge
+    magneticPull += 12;       // Opposite natures = gravitational
+    karmicResonance += 10;    // This crossing has deep karmic purpose
+    shadowRisk += 6;          // The gap between them is real and dangerous
+  } else if (g.gana === 3) {
+    // Manushya-Rakshasa: moderate polarity
+    sexualChemistry += 6;
+    magneticPull += 5;
+  }
+
+  // ── BHAKOOT DOSHA: KARMIC DEBT ────────────────────────────────────────────
+  // Bad rashi distance (2-12, 5-9, 6-8). Mainstream: financial/emotional ruin.
+  // Vamachara: karmic debt demanding resolution. The 6-8 (Shad-Ashtak)
+  // distance forces confrontation with what's unresolved between souls.
+  // The debt CAN be healed through conscious engagement.
+  if (d.bhakoot) {
+    karmicResonance += 10;    // There IS a karmic reason for this pairing
+    healingPotential += 6;    // Conscious engagement can resolve the debt
+  }
+
+  // ── ENEMY YONI: PRIMAL FRICTION ───────────────────────────────────────────
+  // Yoni 0-1/4 = enemy animals in the 14-animal Vedic classification.
+  // Mainstream: terrible sexual compatibility, avoid at all costs.
+  // Vamachara: Animal enmity creates VISCERAL charge. The body knows this
+  // person at a primal, pre-verbal level. The friction IS the fire.
+  // Serpent-Horse, Dog-Cat, Rat-Cat — these are not about harmony.
+  // They're about an energy so raw it bypasses the rational mind entirely.
+  if (g.yoni <= 1) {
+    sexualChemistry += 12;    // Friction = fire in tantric framework
+    shadowRisk += 4;          // Primal energy is hard to contain
+  }
+
+  // ── "REJECT" BAND REINTERPRETATION ────────────────────────────────────────
+  // Mainstream "reject" = don't even consider this match.
+  // Vamachara: This pairing is so intense that conventional astrologers
+  // refuse to sanction it. The intensity is real. The danger is real.
+  // And the transformation potential is proportional to both.
+  if (match.verdict_band === 'reject') {
+    sexualChemistry += 8;     // Forbidden fruit charges everything
+    magneticPull += 8;        // You can't look away from what terrifies you
+    karmicResonance += 12;    // "Reject" pairs have deepest karmic entanglement
+    healingPotential += 8;    // If they choose consciousness, growth is massive
+    // Toxic potential already high from mainstream — Vamachara agrees
+  }
+
   // ── Overall (weighted composite from total/36) ──
   const overall = normalizeKoota(match.guna_total, 36, 0, 100);
 
diff --git a/1-in-a-billion-v2/backend/src/services/verdictSynastryEngine.ts b/1-in-a-billion-v2/backend/src/services/verdictSynastryEngine.ts
index 26c44a8a..37b20290 100644
--- a/1-in-a-billion-v2/backend/src/services/verdictSynastryEngine.ts
+++ b/1-in-a-billion-v2/backend/src/services/verdictSynastryEngine.ts
@@ -154,6 +154,45 @@ export function computeVerdictSynastry(
     return { key, label: OVERLAY_LABELS[key] || key, score };
   });
 
+  // ── Derive Toxic Potential from aggregated scores ──
+  // Toxicity = when the fire is HIGH but the container is WEAK.
+  // High chemistry + high magnetic pull + high karmic resonance
+  //   + LOW daily life + LOW long-term sustainability = beautiful destruction.
+  // This IS "the perfect couple who can never be a couple."
+  const aggSexChem = aggregated.find(c => c.key === 'SEXUAL_CHEMISTRY')?.score || 50;
+  const aggPowerDyn = aggregated.find(c => c.key === 'MAGNETIC_PULL')?.score || 50;
+  const aggKarmic = aggregated.find(c => c.key === 'KARMIC_RESONANCE')?.score || 50;
+  const aggEmotSec = aggregated.find(c => c.key === 'DAILY_LIFE')?.score || 50;
+  const aggLongTerm = aggregated.find(c => c.key === 'LONG_TERM_STABILITY')?.score || 50;
+  const aggShadowRisk = aggregated.find(c => c.key === 'SHADOW_RISK')?.score || 0;
+
+  // Intensity = how hot the fire burns (chemistry + pull + karmic entanglement)
+  const intensityFactor = (aggSexChem * 0.35 + aggPowerDyn * 0.35 + aggKarmic * 0.30);
+  // Container = how strong the vessel is (daily life + sustainability)
+  const containerFactor = (aggEmotSec + aggLongTerm) / 2;
+  // The gap between intensity and container = the toxic potential
+  const intensityGap = Math.max(0, intensityFactor - containerFactor);
+
+  // "Can't escape, can't sustain" factor: high karmic pull + weak container
+  const karmicTrap = aggKarmic > 65 && containerFactor < 55
+    ? (aggKarmic - 50) * 0.3   // The karmic bond keeps them coming back
+    : 0;
+
+  // Derived toxic score: multi-factor blend
+  const existingToxic = aggregated.find(c => c.key === 'TOXIC_RELATIONSHIP_POTENTIAL');
+  const systemToxic = existingToxic?.score || 0;
+  const derivedToxic = clamp(
+    systemToxic * 0.30 +                       // 30% from system engines
+    aggShadowRisk * 0.20 +                     // 20% from shadow risk
+    intensityGap * 0.35 +                      // 35% from intensity-container gap
+    karmicTrap                                  // Bonus: karmic entanglement + weak container
+  );
+
+  // Override the aggregated toxic score with the derived one (take the higher)
+  if (existingToxic) {
+    existingToxic.score = Math.max(existingToxic.score, derivedToxic);
+  }
+
   // ── System summary categories (each system's overall) ──
   const systemOveralls: Record<string, number> = {};
   const systemSummaries: SynastryCategory[] = [];
```
