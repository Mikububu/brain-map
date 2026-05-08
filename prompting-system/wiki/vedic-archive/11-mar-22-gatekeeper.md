---
title: 11-mar-22-gatekeeper
type: archive
date: 2026-03-22
commit: 4208c3ca
---

# Five-layer Vedic gatekeeper, 2nd chakra, 7th house, karmic resonance

Commit `4208c3ca` (2026-03-22). The full diff, verbatim from `git show 4208c3ca`.

```diff
commit 4208c3ca4ee4a066387f34d3b44115c071169681
Author: Michael <michael@forbidden-yoga.com>
Date:   Sun Mar 22 18:43:06 2026 +0400

    feat: five-layer vedic gatekeeper — 2nd chakra, 7th house, karmic resonance
    
    Rewrite shouldFlashMatch() with 5 vedic layers gated by spice slider:
    - Safe (1-3): full Ashtakoota + doshas block (traditional system)
    - Medium (4-6): structure + happiness + 7th house readiness
    - Spicy (7-10): 2nd chakra (Yoni+Gana) + happiness + 7th house + karmic depth
    
    All layers use real vedic signals. No watering down. The spice slider
    shifts which planetary dimensions gate the match, not whether vedic runs.
    
    Co-Authored-By: Claude Opus 4.6 (1M context) <noreply@anthropic.com>

diff --git a/1-in-a-billion-v2/backend/src/services/vedic/dharmic_archetype.classifier.ts b/1-in-a-billion-v2/backend/src/services/vedic/dharmic_archetype.classifier.ts
index 7f7b2e7f..b3f51f5c 100644
--- a/1-in-a-billion-v2/backend/src/services/vedic/dharmic_archetype.classifier.ts
+++ b/1-in-a-billion-v2/backend/src/services/vedic/dharmic_archetype.classifier.ts
@@ -342,30 +342,30 @@ export function computeArchetypeCompatibility(
 /**
  * MATCH GATEKEEPER — "1 in a billion" or nothing.
  *
- * The vedic engine ALWAYS runs. All 8 kootas always computed.
- * The spice slider determines which kootas the gatekeeper prioritizes:
+ * Five-layer vedic engine. All layers always computed. The spice slider (1-10)
+ * determines which layers gate the flash:
  *
- *   SAFE (1-3):   Full Ashtakoota — traditional system as designed for arranged marriages.
- *                  High guna total required. Doshas matter. Household stability.
+ *   Layer 1: ASHTAKOOTA    — traditional 8-koota score (max 36, ceiling-adjusted)
+ *   Layer 2: HAPPINESS     — Gana + Graha Maitri + Yoni (chemistry signal)
+ *   Layer 3: 2ND CHAKRA    — Yoni + Gana (Svadhisthana: sexual + temperamental fire)
+ *   Layer 4: 7TH HOUSE     — combined partnership capacity of both people (0-6)
+ *   Layer 5: KARMIC DEPTH  — karmic nakshatras, kama motivation, Rahu/Venus dasha
  *
- *   MEDIUM (4-6): Balanced — needs good total AND good happiness.
- *                  Both structure and chemistry must be present.
- *
- *   SPICY (7-10): 2nd chakra (Svadhisthana) prioritized — Yoni + Gana.
- *                  Sexual chemistry and temperamental fire must be high.
- *                  Full vedic score still used but 2nd chakra is the gate.
+ *   SAFE (1-3):   Layers 1+2. Traditional Ashtakoota as designed. Doshas block.
+ *   MEDIUM (4-6): Layers 1+2+4. Structure + chemistry + relationship readiness.
+ *   SPICY (7-10): Layers 2+3+4+5. Chemistry + fire + capacity + karmic resonance.
  *
  * One label only: "1 in a billion" or no flash.
  */
 export function shouldFlashMatch(params: {
   gunaTotal: number;
   personalCeiling: number;
-  happinessScore?: number;        // Gana + Graha Maitri + Yoni (0-15)
-  happinessCeiling?: number;      // Max achievable for this person
+  happinessScore?: number;
+  happinessCeiling?: number;
   archetypeA: DharmicArchetype;
   archetypeB: DharmicArchetype;
-  intensityPreference: number;    // 1-10 from user
-  gunaBreakdown?: {               // individual koota scores
+  intensityPreference: number;
+  gunaBreakdown?: {
     varna: number;
     vashya: number;
     tara: number;
@@ -375,46 +375,82 @@ export function shouldFlashMatch(params: {
     bhakoot: number;
     nadi: number;
   };
+  // Extended vedic signals (from vedic_people table)
+  seventhHouseA?: number;           // 0-3 (source person's 7th house strength)
+  seventhHouseB?: number;           // 0-3 (candidate's 7th house strength)
+  isKarmicA?: boolean;              // source has karmic nakshatra
+  isKarmicB?: boolean;              // candidate has karmic nakshatra
+  motivationA?: string;             // nakshatra motivation: dharma/artha/kama/moksha
+  motivationB?: string;
+  dashaLordA?: number;              // 0-8 (Sun..Ketu)
+  dashaLordB?: number;
+  doshaActive?: boolean;            // true if unresolved major dosha (nadi + active manglik)
 }): MatchGatekeeperResult {
   const { gunaTotal, personalCeiling, intensityPreference, gunaBreakdown } = params;
 
+  // Layer 1: Ashtakoota (ceiling-adjusted)
+  const gunaPct = personalCeiling > 0 ? (gunaTotal / personalCeiling) * 100 : 0;
+
+  // Layer 2: Happiness Index
   const hCeiling = params.happinessCeiling ?? 15;
   const hScore = params.happinessScore ?? 0;
   const hPct = hCeiling > 0 ? (hScore / hCeiling) * 100 : 0;
 
-  const gunaPct = personalCeiling > 0 ? (gunaTotal / personalCeiling) * 100 : 0;
+  // Layer 3: 2nd Chakra (Svadhisthana) — Yoni + Gana
+  const yoni = gunaBreakdown?.yoni ?? 0;
+  const gana = gunaBreakdown?.gana ?? 0;
+  const chakra2 = yoni + gana; // max 10
 
-  const intensity = Math.max(1, Math.min(10, intensityPreference));
+  // Layer 4: 7th House — combined relationship capacity (max 6)
+  const house7sum = (params.seventhHouseA ?? 0) + (params.seventhHouseB ?? 0);
 
-  // 2nd chakra score: Yoni (max 4) + Gana (max 6) = max 10
-  const yoniScore = gunaBreakdown?.yoni ?? 0;
-  const ganaScore = gunaBreakdown?.gana ?? 0;
-  const chakra2 = yoniScore + ganaScore; // 0-10
-  const chakra2Pct = Math.round((chakra2 / 10) * 100);
+  // Layer 5: Karmic Resonance — at least one signal required
+  const RAHU = 7;
+  const VENUS = 5;
+  const hasKarmicResonance =
+    (params.isKarmicA === true || params.isKarmicB === true) ||
+    (params.motivationA === 'kama' || params.motivationB === 'kama') ||
+    (params.dashaLordA === RAHU || params.dashaLordA === VENUS ||
+     params.dashaLordB === RAHU || params.dashaLordB === VENUS);
 
-  // ── SAFE (1-3): Traditional vedic — full 36-guna system as designed ──
-  // The ancient algorithm built for arranged marriages: household stability, health, prosperity.
+  const intensity = Math.max(1, Math.min(10, intensityPreference));
+
+  // ── SAFE (1-3): Traditional Ashtakoota ──
+  // The ancient system designed for arranged marriages: household stability, health, prosperity.
+  // Gates: high guna total + good happiness + no unresolved doshas.
   if (intensity <= 3) {
-    if (gunaPct >= 75 && hPct >= 70) {
+    if (params.doshaActive) {
+      return { flash: false, label: '1 in a billion', confidence: 'low', reason: `Safe: blocked by unresolved dosha` };
+    }
+    if (gunaPct >= 75 && hPct >= 60) {
       return { flash: true, label: '1 in a billion', confidence: 'high', reason: `Safe: guna ${Math.round(gunaPct)}% + happiness ${Math.round(hPct)}%` };
     }
-    return { flash: false, label: '1 in a billion', confidence: 'low', reason: `Safe: needs guna >= 75% (got ${Math.round(gunaPct)}%) AND happiness >= 70% (got ${Math.round(hPct)}%)` };
+    return { flash: false, label: '1 in a billion', confidence: 'low', reason: `Safe: needs guna >= 75% (got ${Math.round(gunaPct)}%) AND happiness >= 60% (got ${Math.round(hPct)}%)` };
   }
 
-  // ── MEDIUM (4-6): Balanced — both structure and chemistry needed ──
+  // ── MEDIUM (4-6): Structure + Chemistry + Readiness ──
+  // Both the traditional score AND the feeling must be there.
+  // 7th house checks that at least one person is relationship-ready.
   if (intensity <= 6) {
-    if (gunaPct >= 60 && hPct >= 65) {
-      return { flash: true, label: '1 in a billion', confidence: 'high', reason: `Balanced: guna ${Math.round(gunaPct)}% + happiness ${Math.round(hPct)}%` };
+    if (gunaPct >= 55 && hPct >= 65 && house7sum >= 3) {
+      return { flash: true, label: '1 in a billion', confidence: 'high', reason: `Balanced: guna ${Math.round(gunaPct)}% + happiness ${Math.round(hPct)}% + 7th house ${house7sum}/6` };
     }
-    return { flash: false, label: '1 in a billion', confidence: 'low', reason: `Balanced: needs guna >= 60% (got ${Math.round(gunaPct)}%) AND happiness >= 65% (got ${Math.round(hPct)}%)` };
+    return { flash: false, label: '1 in a billion', confidence: 'low', reason: `Balanced: needs guna >= 55% (got ${Math.round(gunaPct)}%), happiness >= 65% (got ${Math.round(hPct)}%), 7th house >= 3 (got ${house7sum})` };
   }
 
-  // ── SPICY (7-10): 2nd chakra gate — Yoni + Gana must be lit ──
-  // Full vedic score still runs, but the gate is the 2nd chakra.
-  // Sexual chemistry (Yoni) + temperamental fire (Gana) = Svadhisthana.
-  // Benchmark: Michael & Charmaine = 9/10 (Yoni 3 + Gana 6).
-  if (chakra2 >= 8 && hPct >= 60) {
-    return { flash: true, label: '1 in a billion', confidence: 'high', reason: `Spicy: 2nd chakra ${chakra2}/10 (yoni=${yoniScore} gana=${ganaScore}) + happiness ${Math.round(hPct)}%` };
+  // ── SPICY (7-10): Svadhisthana + Capacity + Karmic Depth ──
+  // 2nd chakra (sexual chemistry + temperamental fire) is the primary gate.
+  // Both people must have relationship capacity (7th house).
+  // Karmic resonance adds the fated dimension.
+  if (chakra2 >= 7 && hPct >= 55 && house7sum >= 4 && hasKarmicResonance) {
+    return { flash: true, label: '1 in a billion', confidence: 'high', reason: `Spicy: 2nd chakra ${chakra2}/10 + happiness ${Math.round(hPct)}% + 7th house ${house7sum}/6 + karmic resonance` };
   }
-  return { flash: false, label: '1 in a billion', confidence: 'low', reason: `Spicy: needs 2nd chakra >= 8/10 (got ${chakra2}) AND happiness >= 60% (got ${Math.round(hPct)}%)` };
+
+  // Build specific failure reason
+  const fails: string[] = [];
+  if (chakra2 < 7) fails.push(`2nd chakra ${chakra2}/10 (need >= 7)`);
+  if (hPct < 55) fails.push(`happiness ${Math.round(hPct)}% (need >= 55%)`);
+  if (house7sum < 4) fails.push(`7th house ${house7sum}/6 (need >= 4)`);
+  if (!hasKarmicResonance) fails.push('no karmic resonance');
+  return { flash: false, label: '1 in a billion', confidence: 'low', reason: `Spicy: ${fails.join(', ')}` };
 }
diff --git a/1-in-a-billion-v2/backend/src/workers/vedicMatchWorker.ts b/1-in-a-billion-v2/backend/src/workers/vedicMatchWorker.ts
index 26a50cec..3987a86d 100644
--- a/1-in-a-billion-v2/backend/src/workers/vedicMatchWorker.ts
+++ b/1-in-a-billion-v2/backend/src/workers/vedicMatchWorker.ts
@@ -212,15 +212,15 @@ async function processNextJob() {
             // Only consider matches above happiness threshold (saves DB queries)
             if (happinessPct < 35) continue;
 
-            // Load archetype data for both people
+            // Load full vedic data for both people
             const { data: vedicA } = await supabase
                 .from('vedic_people')
-                .select('dharmic_archetype')
+                .select('dharmic_archetype, seventh_house_strength, is_karmic_nakshatra, nakshatra_motivation, dasha_lord')
                 .eq('person_id', m.person_a_id)
                 .single();
             const { data: vedicB } = await supabase
                 .from('vedic_people')
-                .select('dharmic_archetype')
+                .select('dharmic_archetype, seventh_house_strength, is_karmic_nakshatra, nakshatra_motivation, dasha_lord')
                 .eq('person_id', m.person_b_id)
                 .single();
 
@@ -236,7 +236,10 @@ async function processNextJob() {
                 .single();
             const intensity = userPref?.relationship_intensity ?? 5;
 
-            // Run the three-dimensional gatekeeper (now happiness-primary)
+            // Dosha check: unresolved nadi + active manglik = hard block for safe users
+            const doshaActive = m.dosha.nadi === true && m.dosha.manglik === 'active';
+
+            // Run the five-layer gatekeeper
             const gate = shouldFlashMatch({
                 gunaTotal: m.guna_total,
                 personalCeiling: m.personal_ceiling ?? 36,
@@ -246,6 +249,15 @@ async function processNextJob() {
                 archetypeB,
                 intensityPreference: intensity,
                 gunaBreakdown: m.guna_breakdown,
+                seventhHouseA: vedicA?.seventh_house_strength ?? 0,
+                seventhHouseB: vedicB?.seventh_house_strength ?? 0,
+                isKarmicA: vedicA?.is_karmic_nakshatra ?? false,
+                isKarmicB: vedicB?.is_karmic_nakshatra ?? false,
+                motivationA: vedicA?.nakshatra_motivation,
+                motivationB: vedicB?.nakshatra_motivation,
+                dashaLordA: vedicA?.dasha_lord,
+                dashaLordB: vedicB?.dasha_lord,
+                doshaActive,
             });
 
             if (gate.flash) {
```
