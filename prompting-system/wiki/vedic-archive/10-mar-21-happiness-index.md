---
title: "10-mar-21-happiness-index"
type: archive
date: 2026-03-21
commit: 2aef2407
---

# Ashtakuta tables fix + Happiness Index (the 9th category)

Commit `2aef2407` (2026-03-21). The full diff, verbatim from `git show 2aef2407`.

```diff
commit 2aef24071aaeee1ab81f912b04aa9ced3f0e1714
Author: Michael <michael@forbidden-yoga.com>
Date:   Sat Mar 21 12:06:12 2026 +0400

    fix: Ashtakoota tables (Graha Maitri, Yoni, Gana) + Happiness Index
    
    - Fix GRAHA_MAITRI_TABLE: full Parashara compound friendship (was only 3/5, now 0-5)
    - Fix YONI_TABLE: enemy pairs score 0, Tiger row corrected (was copy of Cow)
    - Fix GANA_TABLE: Deva-Rakshasa=0, Manushya-Rakshasa=1 (strict traditional)
    - Sync vedic_yoni_gana_dasha.tables.ts with identical fixes
    - Add Ashtakoota breakdown to synastry PDF page 2 (chart reference)
    - Add "The Happiness" as 9th deterministic compatibility category (Gana+Graha Maitri+Yoni)
    - Add translations for "The Happiness" in all 10 languages
    
    Co-Authored-By: Claude Opus 4.6 <noreply@anthropic.com>

diff --git a/1-in-a-billion-v2/backend/src/services/pdf/pdfGenerator.ts b/1-in-a-billion-v2/backend/src/services/pdf/pdfGenerator.ts
index 2893a493..26cd4be7 100755
--- a/1-in-a-billion-v2/backend/src/services/pdf/pdfGenerator.ts
+++ b/1-in-a-billion-v2/backend/src/services/pdf/pdfGenerator.ts
@@ -119,6 +119,7 @@ const PDF_TRANSLATIONS: Record<string, Partial<Record<OutputLanguage, string>>>
   'What Remains': { de: 'Was bleibt', es: 'Lo Que Queda', fr: 'Ce Qui Reste', ja: '残るもの', ko: '남는 것', hi: 'जो बचता है', pt: 'O Que Resta', it: 'Quello Che Resta', ru: 'Что остаётся', zh: '留下的' },
   'The Damage': { de: 'Der Schaden', es: 'El Daño', fr: 'Les Dégâts', ja: '傷跡', ko: '상처', hi: 'नुकसान', pt: 'O Dano', it: 'Il Danno', ru: 'Урон', zh: '伤害' },
   'The Agreement': { de: 'Die Vereinbarung', es: 'El Acuerdo', fr: 'L\'Accord', ja: '合意', ko: '합의', hi: 'समझौता', pt: 'O Acordo', it: 'L\'Accordo', ru: 'Договорённость', zh: '约定' },
+  'The Happiness': { de: 'Das Glück', es: 'La Felicidad', fr: 'Le Bonheur', ja: '幸福', ko: '행복', hi: 'सुख', pt: 'A Felicidade', it: 'La Felicità', ru: 'Счастье', zh: '幸福' },
 };
 
 function translateLabel(label: string, lang?: string): string {
diff --git a/1-in-a-billion-v2/backend/src/services/vedic/vedic_ashtakoota.tables.ts b/1-in-a-billion-v2/backend/src/services/vedic/vedic_ashtakoota.tables.ts
index fa373e8d..0fa071eb 100644
--- a/1-in-a-billion-v2/backend/src/services/vedic/vedic_ashtakoota.tables.ts
+++ b/1-in-a-billion-v2/backend/src/services/vedic/vedic_ashtakoota.tables.ts
@@ -135,21 +135,24 @@ export const NAKSHATRA_TO_YONI: number[] = [
     0, 1, 2, 3, 4, 5, 6, 2, 6, 7, 7, 8, 9, 10, 9, 10, 4, 4, 5, 11, 12, 11, 13, 0, 13, 8, 1
 ];
 
+// Sworn enemy pairs score 0: Horse↔Buffalo, Elephant↔Lion, Sheep↔Monkey,
+// Serpent↔Mongoose, Cat↔Rat, Cow↔Tiger. Symmetric matrix.
 export const YONI_TABLE: number[][] = [
-    [4, 2, 2, 1, 3, 1, 2, 1, 3, 2, 3, 2, 1, 2],
-    [2, 4, 2, 1, 3, 1, 2, 1, 3, 2, 3, 2, 1, 2],
-    [2, 2, 4, 2, 3, 2, 3, 2, 3, 2, 3, 2, 2, 2],
-    [1, 1, 2, 4, 1, 1, 1, 1, 2, 1, 2, 1, 1, 1],
-    [3, 3, 3, 1, 4, 2, 3, 2, 4, 3, 4, 3, 2, 3],
-    [1, 1, 2, 1, 2, 4, 1, 1, 2, 1, 2, 1, 1, 1],
-    [2, 2, 3, 1, 3, 1, 4, 1, 3, 2, 3, 2, 1, 2],
-    [1, 1, 2, 1, 2, 1, 1, 4, 2, 1, 2, 1, 1, 1],
-    [3, 3, 3, 2, 4, 2, 3, 2, 4, 3, 4, 3, 2, 3],
-    [2, 2, 2, 1, 3, 1, 2, 1, 3, 4, 3, 2, 1, 2],
-    [3, 3, 3, 2, 4, 2, 3, 2, 4, 3, 4, 3, 2, 3],
-    [2, 2, 2, 1, 3, 1, 2, 1, 3, 2, 3, 4, 1, 2],
-    [1, 1, 2, 1, 2, 1, 1, 1, 2, 1, 2, 1, 4, 1],
-    [2, 2, 2, 1, 3, 1, 2, 1, 3, 2, 3, 2, 1, 4],
+    /*  Ho El Sh Se De Do Ca Ra Co Bu Ti Mo Mg Li */
+    [4, 2, 2, 1, 3, 1, 2, 1, 3, 0, 3, 2, 1, 2], // 0  Horse
+    [2, 4, 2, 1, 3, 1, 2, 1, 3, 2, 3, 2, 1, 0], // 1  Elephant
+    [2, 2, 4, 2, 3, 2, 3, 2, 3, 2, 3, 0, 2, 2], // 2  Sheep
+    [1, 1, 2, 4, 1, 1, 1, 1, 2, 1, 2, 1, 0, 1], // 3  Serpent
+    [3, 3, 3, 1, 4, 2, 3, 2, 3, 3, 1, 3, 2, 3], // 4  Deer
+    [1, 1, 2, 1, 2, 4, 1, 1, 2, 1, 2, 1, 1, 1], // 5  Dog
+    [2, 2, 3, 1, 3, 1, 4, 0, 3, 2, 3, 2, 1, 2], // 6  Cat
+    [1, 1, 2, 1, 2, 1, 0, 4, 2, 1, 2, 1, 1, 1], // 7  Rat
+    [3, 3, 3, 2, 3, 2, 3, 2, 4, 3, 0, 3, 2, 3], // 8  Cow
+    [0, 2, 2, 1, 3, 1, 2, 1, 3, 4, 3, 2, 1, 2], // 9  Buffalo
+    [3, 3, 3, 2, 1, 2, 3, 2, 0, 3, 4, 3, 2, 3], // 10 Tiger (was copy of Cow — FIXED)
+    [2, 2, 0, 1, 3, 1, 2, 1, 3, 2, 3, 4, 1, 2], // 11 Monkey
+    [1, 1, 2, 0, 2, 1, 1, 1, 2, 1, 2, 1, 4, 1], // 12 Mongoose
+    [2, 0, 2, 1, 3, 1, 2, 1, 3, 2, 3, 2, 1, 4], // 13 Lion
 ];
 // Alias for consistency with Step 595 export
 export const YONI_MATRIX = YONI_TABLE;
@@ -199,84 +202,65 @@ export const FULL_YONI_MATRIX = YONI_MATRIX;
 
 /* =====================================================
    GRAHA MAITRI (5)
+   Parashara Naisargika Maitri (Natural Planetary Friendship)
+   Compound friendship scoring for Moon rashi lords.
+
+   Values: 0=Enemy, 1=Neutral, 2=Friend
+   Scoring: F+F=5, F+N=4, N+N=3, F+E=1, N+E=0.5, E+E=0
 ===================================================== */
 
+// Rashi → Lord planet index
+// 0=Sun, 1=Moon, 2=Mars, 3=Mercury, 4=Jupiter, 5=Venus, 6=Saturn
 export const RASHI_LORD: number[] = [
     2, 5, 3, 1, 0, 3, 5, 2, 4, 6, 6, 4
+    // Ar:Mars Ta:Ven Ge:Mer Ca:Mo Le:Su Vi:Mer Li:Ven Sc:Mars Sa:Jup Cp:Sat Aq:Sat Pi:Jup
 ];
 
+// Parashara Natural Friendship Matrix (Naisargika Maitri)
+// 0=Enemy, 1=Neutral, 2=Friend
 export const PLANET_FRIENDSHIP: number[][] = [
-    /*        Su Mo Ma Me Ju Ve Sa */
-    [5, 5, 0, 0, 5, 0, 0], // Standard numeric friend scores usually 5/0/0.5?
-    // User snippet Step 595 has:
-    // [2,1,0,1,2,0,0]
-    // This implies scores 0-5 mapping?
-    // Let's copy user matrix exactly.
-    [2, 1, 0, 1, 2, 0, 0],
-    [1, 2, 1, 1, 2, 1, 0],
-    [0, 1, 2, 1, 1, 0, 0],
-    [1, 1, 1, 2, 1, 1, 0],
-    [2, 2, 1, 1, 2, 1, 0],
-    [0, 1, 0, 1, 1, 2, 1],
-    [0, 0, 0, 0, 0, 1, 2],
+    /*        Su  Mo  Ma  Me  Ju  Ve  Sa */
+    /* Su */ [2,  2,  2,  1,  2,  0,  0],
+    /* Mo */ [2,  2,  1,  2,  1,  1,  1],
+    /* Ma */ [2,  2,  2,  0,  2,  1,  1],
+    /* Me */ [2,  0,  1,  2,  1,  2,  1],
+    /* Ju */ [2,  2,  2,  0,  2,  0,  1],
+    /* Ve */ [0,  0,  1,  2,  1,  2,  2],
+    /* Sa */ [0,  0,  0,  2,  1,  2,  2],
 ];
 
-// Calculation Logic
+// Compound friendship → Graha Maitri points (Parashara standard)
+function compoundMaitriPoints(lordA: number, lordB: number): number {
+    if (lordA === lordB) return 5;
+    const fAB = PLANET_FRIENDSHIP[lordA][lordB];
+    const fBA = PLANET_FRIENDSHIP[lordB][lordA];
+    if (fAB === 2 && fBA === 2) return 5;                        // mutual friends
+    if (fAB + fBA === 3) return 4;                                // friend + neutral
+    if (fAB === 1 && fBA === 1) return 3;                         // both neutral
+    if (fAB + fBA === 2 && fAB !== fBA) return 1;                 // friend + enemy
+    if (fAB + fBA === 1) return 0.5;                              // neutral + enemy
+    return 0;                                                      // mutual enemies
+}
+
 export function grahaMaitriScore(rashiA: number, rashiB: number): number {
-    // Basic logic if not pre-mapped, but typical Graha Maitri table is Rashi x Rashi
-    // User Step 595 has PLANET_FRIENDSHIP (7x7) and RASHI_LORD (12).
-    // The Engine expects GRAHA_MAITRI_TABLE (12x12).
-    // We derive it.
-    // BUT! The values in PLANET_FRIENDSHIP [2,1,0...] do not look like points (0..5).
-    // Usually points are 0, 0.5, 3, 4, 5.
-    // The matrix values 2,1,0 might be "Friend, Neutral, Enemy".
-    // 2=Friend, 1=Neutral, 0=Enemy.
-    // Score Rules:
-    // F-F = 5
-    // F-N = 4
-    // F-E = 1 (or 0?)
-    // N-N = 3
-    // N-E = 0.5
-    // E-E = 0
-    // I need the SCORING FUNCTION to map these pairs to 0-5 points.
-    // Without it, I can't generate the 12x12 table accurately.
-    // **CRITICAL**: User Step 595 did *not* provide the `friendsMap` logic.
-    // However, Step 536 (previous Authoritative Tables) provided `GRAHA_MAITRI_TABLE` full 12x12.
-    // Values were 5, 3, 0.5 etc.
-    // I will use `GRAHA_MAITRI_TABLE` from Step 536 as the derived table, assuming it matches the logic of Step 595.
-    // Unless Step 595 implies a different scoring system.
-    // Step 595 is "Full Ashtakoota...".
-    // I will rely on the PREVIOUS valid full table for certainty, 
-    // OR implement the standard Vedic logic: 
-    // Friend=Friend(5), Friend=Neutral(4), Friend=Enemy(1), Neutral=Neutral(3), Neutral=Enemy(0.5), Enemy=Enemy(0).
-    // Let's verify Step 536 table: [0][0] is Aries-Aries (Mars-Mars). Mars-Mars is same (Friend/Friend?). 
-    // Step 536 says [0][0] = 5. Correct.
-    // Aries(Mars)-Gemini(Mercury). Mars-Mercury.
-    // Mars treats Mercury as Enemy (0). Mercury treats Mars as Neutral (1).
-    // Enemy-Neutral -> 0.5.
-    // Step 536 [0][2] = 3? Wait.
-    // [0][2] is Aries(0) vs Gemini(2).
-    // Step 536 row 0: 5,5,3,3,5...
-    // So [0][2] is 3. 
-    // This implies Neutral-Neutral? Or Friend-Enemy?
-    // I will trust Step 536 `GRAHA_MAITRI_TABLE` as the "Compiled" version.
-    return 0;
+    return compoundMaitriPoints(RASHI_LORD[rashiA], RASHI_LORD[rashiB]);
 }
 
-// Re-using Step 536 table for safety as Step 595 didn't give full scoring logic
+// Derived 12×12 Rashi table — full range: 0, 0.5, 1, 3, 4, 5
 export const GRAHA_MAITRI_TABLE: number[][] = [
-    [5, 5, 3, 3, 5, 3, 3, 5, 3, 3, 3, 5],
-    [5, 5, 3, 3, 5, 3, 3, 5, 3, 3, 3, 5],
-    [3, 3, 5, 5, 3, 5, 5, 3, 5, 5, 5, 3],
-    [3, 3, 5, 5, 3, 5, 5, 3, 5, 5, 5, 3],
-    [5, 5, 3, 3, 5, 3, 3, 5, 3, 3, 3, 5], // Leo (Sun)
-    [3, 3, 5, 5, 3, 5, 5, 3, 5, 5, 5, 3], // Virgo (Merc)
-    [3, 3, 5, 5, 3, 5, 5, 3, 5, 5, 5, 3], // Libra (Ven)
-    [5, 5, 3, 3, 5, 3, 3, 5, 3, 3, 3, 5], // Scorpio (Mars)
-    [3, 3, 5, 5, 3, 5, 5, 3, 5, 5, 5, 3], // Sag (Jup)
-    [3, 3, 5, 5, 3, 5, 5, 3, 5, 5, 5, 3], // Cap (Sat)
-    [3, 3, 5, 5, 3, 5, 5, 3, 5, 5, 5, 3], // Aq (Sat)
-    [5, 5, 3, 3, 5, 3, 3, 5, 3, 3, 3, 5], // Pi (Jup)
+    /*         Ar   Ta   Ge   Ca   Le   Vi   Li   Sc   Sa   Cp   Aq   Pi  */
+    /* Ar */ [  5,   3, 0.5,   4,   5, 0.5,   3,   5,   5, 0.5, 0.5,   5],
+    /* Ta */ [  3,   5,   5, 0.5,   0,   5,   5,   3, 0.5,   5,   5, 0.5],
+    /* Ge */ [0.5,   5,   5,   1,   4,   5,   5, 0.5, 0.5,   4,   4, 0.5],
+    /* Ca */ [  4, 0.5,   1,   5,   5,   1, 0.5,   4,   4, 0.5, 0.5,   4],
+    /* Le */ [  5,   0,   4,   5,   5,   4,   0,   5,   5,   0,   0,   5],
+    /* Vi */ [0.5,   5,   5,   1,   4,   5,   5, 0.5, 0.5,   4,   4, 0.5],
+    /* Li */ [  3,   5,   5, 0.5,   0,   5,   5,   3, 0.5,   5,   5, 0.5],
+    /* Sc */ [  5,   3, 0.5,   4,   5, 0.5,   3,   5,   5, 0.5, 0.5,   5],
+    /* Sa */ [  5, 0.5, 0.5,   4,   5, 0.5, 0.5,   5,   5,   3,   3,   5],
+    /* Cp */ [0.5,   5,   4, 0.5,   0,   4,   5, 0.5,   3,   5,   5,   3],
+    /* Aq */ [0.5,   5,   4, 0.5,   0,   4,   5, 0.5,   3,   5,   5,   3],
+    /* Pi */ [  5, 0.5, 0.5,   4,   5, 0.5, 0.5,   5,   5,   3,   3,   5],
 ];
 
 // Alias for backward compatibility with engine
@@ -307,15 +291,13 @@ export const NAKSHATRA_TO_GANA: number[] = [
     2, 1, 2, 0, 2, 2, 1, 1, 0, 2, 2, 2, 0
 ];
 
+// Deva-Rakshasa = 0 (sworn incompatibility), Manushya-Rakshasa = 1 (hostile)
+// Same gana = 6, Deva-Manushya = 5
 export const GANA_TABLE: number[][] = [
-    [6, 5, 1],
-    [5, 6, 3], // Step 595 has 3 for Manushya-Rakshasa? Step 536 had 1??
-    [1, 3, 6],
+    [6, 5, 0], // Deva
+    [5, 6, 1], // Manushya
+    [0, 1, 6], // Rakshasa
 ];
-// Note: Step 536 GANA_TABLE had [5,6,1] in row 1!
-// Step 595 GANA_MATRIX has [5,6,3].
-// 3 points for Manushya-Rakshasa is unusual (commonly 0 or 1).
-// But Step 595 is LATEST. I will use Step 595 values.
 export const GANA_MATRIX = GANA_TABLE;
 
 // Gana mapping from Nakshatra names for vedic_matchmaking.engine.ts
@@ -353,12 +335,12 @@ export const GANA_BY_NAKSHATRA: Record<string, string> = {
 export const GANA_SCORE: Record<string, number> = {
     'deva_deva': 6,
     'deva_manushya': 5,
-    'deva_rakshasa': 1,
+    'deva_rakshasa': 0,
     'manushya_deva': 5,
     'manushya_manushya': 6,
-    'manushya_rakshasa': 3,
-    'rakshasa_deva': 1,
-    'rakshasa_manushya': 3,
+    'manushya_rakshasa': 1,
+    'rakshasa_deva': 0,
+    'rakshasa_manushya': 1,
     'rakshasa_rakshasa': 6
 };
 
diff --git a/1-in-a-billion-v2/backend/src/services/vedic/vedic_yoni_gana_dasha.tables.ts b/1-in-a-billion-v2/backend/src/services/vedic/vedic_yoni_gana_dasha.tables.ts
index 9cd8ce9b..26027573 100644
--- a/1-in-a-billion-v2/backend/src/services/vedic/vedic_yoni_gana_dasha.tables.ts
+++ b/1-in-a-billion-v2/backend/src/services/vedic/vedic_yoni_gana_dasha.tables.ts
@@ -43,24 +43,26 @@ export const NAKSHATRA_TO_YONI: number[] = [
 /*
 Yoni compatibility matrix
 Score values: 0, 1, 2, 3, 4
+Sworn enemy pairs score 0: Horse↔Buffalo, Elephant↔Lion,
+Sheep↔Monkey, Serpent↔Mongoose, Cat↔Rat, Cow↔Tiger.
 */
 
 export const YONI_MATRIX: number[][] = [
-    /*            Ho El Sh Se De Do Ca Ra Co Bu Ti Mo Mg Li */
-    [4, 2, 2, 1, 3, 1, 2, 1, 3, 2, 3, 2, 1, 2], // Horse
-    [2, 4, 2, 1, 3, 1, 2, 1, 3, 2, 3, 2, 1, 2], // Elephant
-    [2, 2, 4, 2, 3, 2, 3, 2, 3, 2, 3, 2, 2, 2], // Sheep
-    [1, 1, 2, 4, 1, 1, 1, 1, 2, 1, 2, 1, 1, 1], // Serpent
-    [3, 3, 3, 1, 4, 2, 3, 2, 4, 3, 4, 3, 2, 3], // Deer
-    [1, 1, 2, 1, 2, 4, 1, 1, 2, 1, 2, 1, 1, 1], // Dog
-    [2, 2, 3, 1, 3, 1, 4, 1, 3, 2, 3, 2, 1, 2], // Cat
-    [1, 1, 2, 1, 2, 1, 1, 4, 2, 1, 2, 1, 1, 1], // Rat
-    [3, 3, 3, 2, 4, 2, 3, 2, 4, 3, 4, 3, 2, 3], // Cow
-    [2, 2, 2, 1, 3, 1, 2, 1, 3, 4, 3, 2, 1, 2], // Buffalo
-    [3, 3, 3, 2, 4, 2, 3, 2, 4, 3, 4, 3, 2, 3], // Tiger
-    [2, 2, 2, 1, 3, 1, 2, 1, 3, 2, 3, 4, 1, 2], // Monkey
-    [1, 1, 2, 1, 2, 1, 1, 1, 2, 1, 2, 1, 4, 1], // Lion
-    [2, 2, 2, 1, 3, 1, 2, 1, 3, 2, 3, 2, 1, 4], // Mongoose
+    /*  Ho El Sh Se De Do Ca Ra Co Bu Ti Mo Mg Li */
+    [4, 2, 2, 1, 3, 1, 2, 1, 3, 0, 3, 2, 1, 2], // 0  Horse
+    [2, 4, 2, 1, 3, 1, 2, 1, 3, 2, 3, 2, 1, 0], // 1  Elephant
+    [2, 2, 4, 2, 3, 2, 3, 2, 3, 2, 3, 0, 2, 2], // 2  Sheep
+    [1, 1, 2, 4, 1, 1, 1, 1, 2, 1, 2, 1, 0, 1], // 3  Serpent
+    [3, 3, 3, 1, 4, 2, 3, 2, 3, 3, 1, 3, 2, 3], // 4  Deer
+    [1, 1, 2, 1, 2, 4, 1, 1, 2, 1, 2, 1, 1, 1], // 5  Dog
+    [2, 2, 3, 1, 3, 1, 4, 0, 3, 2, 3, 2, 1, 2], // 6  Cat
+    [1, 1, 2, 1, 2, 1, 0, 4, 2, 1, 2, 1, 1, 1], // 7  Rat
+    [3, 3, 3, 2, 3, 2, 3, 2, 4, 3, 0, 3, 2, 3], // 8  Cow
+    [0, 2, 2, 1, 3, 1, 2, 1, 3, 4, 3, 2, 1, 2], // 9  Buffalo
+    [3, 3, 3, 2, 1, 2, 3, 2, 0, 3, 4, 3, 2, 3], // 10 Tiger
+    [2, 2, 0, 1, 3, 1, 2, 1, 3, 2, 3, 4, 1, 2], // 11 Monkey
+    [1, 1, 2, 0, 2, 1, 1, 1, 2, 1, 2, 1, 4, 1], // 12 Mongoose
+    [2, 0, 2, 1, 3, 1, 2, 1, 3, 2, 3, 2, 1, 4], // 13 Lion
 ];
 
 /* =====================================================
@@ -75,10 +77,11 @@ export const NAKSHATRA_TO_GANA: number[] = [
     2, 1, 2, 0, 2, 2, 1, 1, 0, 2, 2, 2, 0
 ];
 
+// Deva-Rakshasa = 0 (sworn incompatibility), Manushya-Rakshasa = 1 (hostile)
 export const GANA_MATRIX: number[][] = [
-    [6, 5, 1], // Deva
-    [5, 6, 3], // Manushya
-    [1, 3, 6], // Rakshasa
+    [6, 5, 0], // Deva
+    [5, 6, 1], // Manushya
+    [0, 1, 6], // Rakshasa
 ];
 
 /* =====================================================
diff --git a/1-in-a-billion-v2/backend/src/workers/textWorker.ts b/1-in-a-billion-v2/backend/src/workers/textWorker.ts
index 0635b870..ac3a406b 100755
--- a/1-in-a-billion-v2/backend/src/workers/textWorker.ts
+++ b/1-in-a-billion-v2/backend/src/workers/textWorker.ts
@@ -36,6 +36,8 @@ import { computeGeneKeysSynastry } from '../services/geneKeysSynastryEngine';
 import { computeKabbalahSynastry } from '../services/kabbalahSynastryEngine';
 import { computeVerdictSynastry } from '../services/verdictSynastryEngine';
 import { computeRelationalStyle, computeRelationalStyleGap } from '../services/relationalStyleEngine';
+import { GRAHA_MAITRI_TABLE, GANA_TABLE, NAKSHATRA_TO_YONI, YONI_TABLE, NAKSHATRA_TO_GANA } from '../services/vedic/vedic_ashtakoota.tables';
+import { nakshatraToIndex, rashiToIndex } from '../services/vedic/vedic_ashtakoota.converters';
 import { buildChartReferencePage } from '../services/chartReferencePage';
 import {
   stripWesternChartData,
@@ -1695,6 +1697,24 @@ Do not recompute or contradict them.
             combinedChartData = layer0Block + combinedChartData;
 
             console.log(`🔢 [TextWorker] Layer 0 Vedic math injected: ${total}/${ceilingVal} (${ceilingPct}%) — ${tier}`);
+
+            // ── Append Ashtakoota breakdown to chart reference page (PDF page 2) ──
+            const gunaLines = [
+              '',
+              `ASHTAKOOTA MATCHING (${total}/${ceilingVal})`,
+              `  Varna:        ${a.varna.score}/1`,
+              `  Vashya:       ${a.vashya.score}/2`,
+              `  Tara:         ${a.tara.score}/3`,
+              `  Yoni:         ${a.yoni.score}/4`,
+              `  Graha Maitri: ${a.graha_maitri.score}/5`,
+              `  Gana:         ${a.gana.score}/6`,
+              `  Bhakoot:      ${a.bhakoot.score}/7`,
+              `  Nadi:         ${a.nadi.score}/8`,
+              `  Total:        ${total}/${ceilingVal} (${ceilingPct}%)`,
+              `  Verdict:      ${tier}`,
+              ...(doshas.length > 0 ? doshas.map(d => `  ${d}`) : []),
+            ];
+            chartRefPage += '\n' + gunaLines.join('\n');
           }
         } catch (err: any) {
           console.warn(`⚠️ [TextWorker] Ashtakoot scoring failed for overlay, continuing without: ${err?.message}`);
@@ -2432,6 +2452,49 @@ Do not recompute or contradict them.
           console.warn(`⚠️ Failed to compute relational style: ${err.message}`);
         }
       }
+
+      // ─── Inject The Happiness as fully deterministic 9th category ───
+      // South Indian tradition: Gana (6) + Graha Maitri (5) + Yoni (4) = 15 max.
+      // "Do you feel the same way about life? Do your minds naturally agree?
+      //  Do your bodies want the same thing?"
+      // Computed from Vedic data whenever both people have sidereal moon data.
+      if (compatibilityScores && p1Placements?.sidereal && p2Placements?.sidereal) {
+        try {
+          const p1Sid = p1Placements.sidereal;
+          const p2Sid = p2Placements.sidereal;
+          if (p1Sid.janmaNakshatra && p2Sid.janmaNakshatra && p1Sid.chandraRashi && p2Sid.chandraRashi) {
+            const nak1 = nakshatraToIndex(p1Sid.janmaNakshatra);
+            const nak2 = nakshatraToIndex(p2Sid.janmaNakshatra);
+            const rashi1 = rashiToIndex(p1Sid.chandraRashi);
+            const rashi2 = rashiToIndex(p2Sid.chandraRashi);
+
+            const ganaScore = GANA_TABLE[NAKSHATRA_TO_GANA[nak1]][NAKSHATRA_TO_GANA[nak2]];
+            const maitriScore = GRAHA_MAITRI_TABLE[rashi1][rashi2];
+            const yoniScore = YONI_TABLE[NAKSHATRA_TO_YONI[nak1]][NAKSHATRA_TO_YONI[nak2]];
+
+            const happinessRaw = ganaScore + maitriScore + yoniScore; // 0-15
+            const happinessScore100 = Math.round((happinessRaw / 15) * 100);
+            const happinessScoreTen = Math.max(0, Math.min(10, Math.round((happinessScore100 / 10) * 10) / 10));
+
+            // Build descriptive note from the three components
+            const ganaLabel = ganaScore >= 5 ? 'matched temperaments' : ganaScore >= 3 ? 'workable temperaments' : 'clashing temperaments';
+            const maitriLabel = maitriScore >= 4 ? 'harmonious minds' : maitriScore >= 3 ? 'neutral minds' : 'hostile minds';
+            const yoniLabel = yoniScore >= 3 ? 'physical ease' : yoniScore >= 2 ? 'physical neutrality' : 'physical friction';
+            const note = `Gana ${ganaScore}/6 (${ganaLabel}), Graha Maitri ${maitriScore}/5 (${maitriLabel}), Yoni ${yoniScore}/4 (${yoniLabel}). This is the potential for genuine happiness — not whether they stay, but whether staying feels like relief.`;
+
+            compatibilityScores.push({
+              label: 'The Happiness',
+              score: happinessScore100,
+              scoreTen: happinessScoreTen,
+              note,
+            });
+
+            console.log(`😊 The Happiness: Gana=${ganaScore}/6, Maitri=${maitriScore}/5, Yoni=${yoniScore}/4 → ${happinessRaw}/15 (${happinessScore100}/100)`);
+          }
+        } catch (err: any) {
+          console.warn(`⚠️ Failed to compute happiness index: ${err.message}`);
+        }
+      }
     }
 
     // Extract FINAL VERDICT score + punchline for verdict documents
```
