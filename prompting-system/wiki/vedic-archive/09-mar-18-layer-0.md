---
title: 09-mar-18-layer-0
type: archive
date: 2026-03-18
commit: 623ba8e8
---

# Wire Vedic Layer 0 digest into reading pipeline

Commit `623ba8e8` (2026-03-18). The full diff, verbatim from `git show 623ba8e8`.

```diff
commit 623ba8e8a2f561b015b5501ac5c3bf7d4d01373c
Author: Michael <michael@forbidden-yoga.com>
Date:   Wed Mar 18 22:40:54 2026 +0400

    feat: wire Vedic Layer 0 digest into reading pipeline — shift interpretive weight from Layer 1 to Layer 0
    
    Layer 0 (digest) now does the real reading: dharmic archetype, Rahu hunger,
    karmic mechanism, sexual/desire pattern, current dasha season, Mahavidya
    governance, and narrative arc. Layer 1 receives this alive interpretation
    and focuses purely on writing literary prose — no longer trying to interpret
    AND write simultaneously. Falls back to old trigger if digest fails.
    
    Co-Authored-By: Claude Opus 4.6 (1M context) <noreply@anthropic.com>

diff --git a/1-in-a-billion-v2/backend/src/promptEngine/triggerEngine/vedicTrigger.ts b/1-in-a-billion-v2/backend/src/promptEngine/triggerEngine/vedicTrigger.ts
index 9fd659d8..6c9bff9a 100644
--- a/1-in-a-billion-v2/backend/src/promptEngine/triggerEngine/vedicTrigger.ts
+++ b/1-in-a-billion-v2/backend/src/promptEngine/triggerEngine/vedicTrigger.ts
@@ -7,6 +7,7 @@ import type { OutputLanguage } from '../../config/languages';
 import { buildVedicSection, VEDIC_TERMINOLOGY_RULE } from '../../prompts/systems/vedic';
 import { buildWritingEnhancements } from './writingEnhancements';
 import { renderVedicNarrativeStrip, type VedicNarrativeMode, type VedicNarrativeSeed } from './vedicNarrative';
+import type { VedicDigest } from '../digests/vedicDigest';
 
 /**
  * VEDIC TRIGGER ENGINE
@@ -231,14 +232,107 @@ export function buildVedicWritingPrompt(params: {
   targetWords: number;
   spiceLevel?: number;
   language?: OutputLanguage;
+  digest?: VedicDigest;
 }): string {
-  const { personName, narrativeTrigger, strippedChartData, targetWords } = params;
+  const { personName, narrativeTrigger, strippedChartData, targetWords, digest } = params;
   const trigger = NARRATIVE_TRIGGER_LABEL;
   const triggerTitle = NARRATIVE_TRIGGER_TITLE;
 
   // Inject the Vedic system guidance — use the user's actual spice level (not hardcoded 7)
   const vedicGuidance = buildVedicSection(false, params.spiceLevel ?? 7);
 
+  // ── When digest is present, Layer 0 already did the reading. Layer 1 just writes. ──
+  if (digest) {
+    // Build the interpretive spine from the digest
+    const spineLines: string[] = [
+      '══════════════════════════════════════════════════════════',
+      'INTERPRETIVE SPINE — Layer 0 has read this chart. Your job is to WRITE, not re-interpret.',
+      'The interpretive decisions below are final. Do not second-guess them. Expand them into literary prose.',
+      '══════════════════════════════════════════════════════════',
+      '',
+    ];
+
+    if (digest.archetype) {
+      spineLines.push(`DHARMIC ARCHETYPE: ${digest.archetype}`);
+    }
+    if (digest.rahuHunger) {
+      spineLines.push('', 'RAHU — THE HUNGER:', digest.rahuHunger);
+    }
+    if (digest.karmicContract) {
+      spineLines.push('', 'THE KARMIC CONTRACT:', digest.karmicContract);
+    }
+    if (digest.karmicScene) {
+      spineLines.push('', 'THE RECURRING SCENE:', digest.karmicScene);
+    }
+    if (digest.sexualLooksLike) {
+      spineLines.push('', `DESIRE PATTERN (${digest.sexualMechanism || 'unclassified'}):`, digest.sexualLooksLike);
+    }
+    if (digest.sexualCost) {
+      spineLines.push('DESIRE COST:', digest.sexualCost);
+    }
+    if (digest.currentSeason) {
+      spineLines.push('', 'CURRENT DASHA SEASON:', digest.currentSeason);
+    }
+    if (digest.presidingMahavidya && digest.presidingMahavidya !== 'none') {
+      spineLines.push('', `PRESIDING MAHAVIDYA: ${digest.presidingMahavidya}`);
+      if (digest.goddessDemand) spineLines.push(digest.goddessDemand);
+    }
+
+    // Narrative arc from digest
+    if (digest.openingImage) {
+      spineLines.push('', 'NARRATIVE ARC:', `OPENING IMAGE: ${digest.openingImage}`);
+    }
+    if (digest.arcMiddle) {
+      spineLines.push(`BREAK-THROUGH: ${digest.arcMiddle}`);
+    }
+    if (digest.arcReckoning) {
+      spineLines.push(`RECKONING: ${digest.arcReckoning}`);
+    }
+    if (digest.landing) {
+      spineLines.push(`LANDING TEMPERATURE: ${digest.landing}`);
+    }
+    if (digest.avoidTrap) {
+      spineLines.push('', `FLATTERY TRAP TO AVOID: ${digest.avoidTrap}`);
+    }
+
+    spineLines.push('', '══════════════════════════════════════════════════════════');
+
+    return [
+      'You are a novelist rendering a Jyotish reading that has already been interpreted by a master astrologer.',
+      'The interpretive spine below contains the READING — the alive, specific, psychologically-real interpretation of this chart.',
+      'Your job is to expand it into literary prose. You are the WRITER, not the reader.',
+      '',
+      'You have read the Mahabharata, Tagore, Premchand, and the Kama Sutra.',
+      'You write with fatalistic irony — the cosmos has written the story, and it is often brutal, but there is something absurdly funny about that too.',
+      CORE_FAIRYTALE_SEED,
+      '',
+      vedicGuidance,
+      '',
+      buildWritingEnhancements('production', true, params.language, 'vedic'),
+      '',
+      ...spineLines,
+      '',
+      'WRITING INSTRUCTIONS:',
+      '- One continuous essay. NO section titles, NO chapter headings, NO standalone headline lines.',
+      '- Third person only. Never "you" or "your". Use the name.',
+      '- WRITE ABOUT THE PERSON, NOT THE CHART. A placement may be named ONCE as an anchor. After that, describe the behavior, the cost, the 3am feeling, the recurring scene.',
+      '- The interpretive spine gives you the WHAT. Your job is the HOW — the prose, the scenes, the rhythms, the images.',
+      '- Each paragraph should feel like a different room in the same haunted house. Do not repeat the same insight in different words.',
+      '- Do not sanitize the Grahas. Rahu is obsession. Ketu is loss. Shani is the weight. The Nakshatras carry erotic and violent undertow.',
+      '- Do not replace "obsession" with "deep connection." Do not replace "karmic debt" with "learning opportunity."',
+      '- The ending does not resolve. It names where the pressure is pressing now — with a wink.',
+      '- NARRATIVE COMPRESSION: Each paragraph carries mechanism + behavior + inner experience + cost.',
+      '',
+      `LENGTH: ${targetWords.toLocaleString('en-US')} words. Do not pad. Do not repeat. Do not add a hopeful ending.`,
+      '',
+      'CHART DATA (authoritative — do not invent or contradict):',
+      strippedChartData,
+      '',
+      `Write ${personName}'s Jyotish reading now. Begin directly with the narrative:`,
+    ].join('\n');
+  }
+
+  // ── Fallback: no digest, original trigger-guided writing prompt ──
   return [
     'You are a Jyotish practitioner who has studied the Brihat Parashara Hora Shastra for decades and writes like someone who has sat with death.',
     'You think in karma and consequence, seasonal inevitability, the creditor who always collects.',
diff --git a/1-in-a-billion-v2/backend/src/workers/textWorker.ts b/1-in-a-billion-v2/backend/src/workers/textWorker.ts
index 31096f47..aa968b92 100755
--- a/1-in-a-billion-v2/backend/src/workers/textWorker.ts
+++ b/1-in-a-billion-v2/backend/src/workers/textWorker.ts
@@ -51,6 +51,12 @@ import {
   buildVedicTriggerPrompt,
   buildVedicWritingPrompt,
 } from '../promptEngine/triggerEngine/vedicTrigger';
+import {
+  buildVedicChartDigestPrompt,
+  validateVedicDigest,
+  extractVedicDigest,
+} from '../promptEngine/digests/vedicDigest';
+import type { VedicDigest } from '../promptEngine/digests/vedicDigest';
 import { VEDIC_TERMINOLOGY_RULE } from '../prompts/systems/vedic';
 import {
   stripHDChartData,
@@ -1169,7 +1175,11 @@ export class TextWorker extends BaseWorker {
         generationComplete = true;
       }
 
-      // ── VEDIC narrativeTrigger engine ──────────────────────────────────────────────
+      // ── VEDIC: digest engine (strip → digest call → writing call) ──────────────────────────────────
+      // Layer 0: digest pre-pass produces deep interpretive reading
+      // (DHARMIC_ARCHETYPE, RAHU_READING, KARMIC_MECHANISM, SEXUAL_DESIRE_PATTERN, CURRENT_SEASON, NARRATIVE_ARC)
+      // which feeds into the writing prompt as a pre-planned interpretive spine.
+      // Falls back to the old 80-120 word trigger paragraph if digest fails validation.
       if (!generationComplete && system === 'vedic' && docType !== 'overlay') {
         const subject = docType === 'person2' ? person2 : person1;
         if (!subject?.name) throw new Error(`Missing subject name for vedic ${docType}`);
@@ -1180,20 +1190,56 @@ export class TextWorker extends BaseWorker {
         );
 
         const stripped = stripVedicChartData(chartData, { seed: vedicPrimarySeed, mode: 'individual', maxAnchors: 10 });
-        const triggerPrompt = buildVedicTriggerPrompt({ personName: subject.name, strippedChartData: stripped, spiceLevel });
-        console.log(`🩸 [TextWorker] Vedic narrativeTrigger call for ${subject.name}...`);
-        const triggerRaw = await llmPaid.generateStreaming(triggerPrompt, `${label}:narrativeTrigger`, {
-          maxTokens: 300, temperature: 0.7, maxRetries: 3,
-          systemPrompt: getSystemPromptForStyle(style, 'individual', 'vedic', params.outputLanguage),
-        });
-        const narrativeTrigger = String(triggerRaw || '').trim();
-        if (!narrativeTrigger) {
-          throw new Error(`Trigger call returned empty for vedic ${docType}: ${subject.name}`);
+
+        // ── Layer 0: digest call ──
+        let vedicDigest: VedicDigest | undefined;
+        let narrativeTrigger = '';
+
+        await updateTextProgress('analyzing', `🔍 Analyzing ${subject.name}'s chart...`, 0.20);
+        console.log(`📊 [TextWorker] Vedic digest call for ${subject.name}...`);
+        try {
+          const digestPrompt = buildVedicChartDigestPrompt({ personName: subject.name, chartData: stripped });
+          const digestRaw = await llmPaid.generateStreaming(digestPrompt, `${label}:digest`, {
+            maxTokens: 3000,
+            temperature: 0.5,
+            maxRetries: 3,
+            systemPrompt: getSystemPromptForStyle(style, 'individual', 'vedic', params.outputLanguage),
+          });
+          const digestText = String(digestRaw || '').trim();
+
+          const validation = validateVedicDigest(digestText);
+          if (validation.ok) {
+            vedicDigest = extractVedicDigest(digestText);
+
+            // Use karmic contract as narrativeTrigger for output metadata
+            narrativeTrigger = vedicDigest.karmicContract || vedicDigest.karmicScene || digestText.slice(0, 200);
+            console.log(`✅ [TextWorker] Vedic digest valid. Archetype: ${vedicDigest.archetype}, Mechanism: ${vedicDigest.sexualMechanism}`);
+          } else {
+            console.warn(`⚠️ [TextWorker] Vedic digest invalid (${validation.reason}) — falling back to trigger call`);
+          }
+        } catch (digestErr: any) {
+          console.warn(`⚠️ [TextWorker] Vedic digest call failed (${digestErr?.message}) — falling back to trigger call`);
         }
+
+        // ── Fallback: old trigger call if digest failed ──
+        if (!vedicDigest) {
+          const triggerPrompt = buildVedicTriggerPrompt({ personName: subject.name, strippedChartData: stripped, spiceLevel });
+          console.log(`🩸 [TextWorker] Vedic trigger fallback for ${subject.name}...`);
+          const triggerRaw = await llmPaid.generateStreaming(triggerPrompt, `${label}:narrativeTrigger`, {
+            maxTokens: 300, temperature: 0.7, maxRetries: 3,
+            systemPrompt: getSystemPromptForStyle(style, 'individual', 'vedic', params.outputLanguage),
+          });
+          narrativeTrigger = String(triggerRaw || '').trim();
+          if (!narrativeTrigger) {
+            throw new Error(`Trigger call returned empty for vedic ${docType}: ${subject.name}`);
+          }
+          console.log(`✅ [TextWorker] Vedic trigger: ${narrativeTrigger.slice(0, 80)}...`);
+        }
+
         narrativeTriggerForOutput = narrativeTrigger;
-        console.log(`✅ [TextWorker] Vedic narrativeTrigger: ${narrativeTrigger.slice(0, 80)}...`);
         await updateTextProgress('writing', `✍️ Writing ${title}...`, 0.35);
 
+        // ── Layer 1: writing call — uses digest as pre-planned spine if available ──
         const chartProvocationsV = buildChartAwareProvocations(subject.name, 'vedic', chartData, spiceLevel, {
           vedicSeed: vedicPrimarySeed,
         });
@@ -1204,9 +1250,10 @@ export class TextWorker extends BaseWorker {
           targetWords: WORD_COUNT_LIMITS.min,
           spiceLevel,
           language: params.outputLanguage,
+          digest: vedicDigest,
         });
         const writingPrompt = `${chartProvocationsV}\n\n${baseWritingPromptV}`;
-        console.log(`✍️ [TextWorker] Vedic writing call for ${subject.name}...`);
+        console.log(`✍️ [TextWorker] Vedic writing call for ${subject.name} (${vedicDigest ? 'digest-guided' : 'trigger-guided'})...`);
         text = await llmPaid.generateStreaming(writingPrompt, `${label}:writing`, {
           maxTokens: 20000, temperature: 0.7, maxRetries: 3,
           systemPrompt: getSystemPromptForStyle(style, 'individual', 'vedic', params.outputLanguage),
```
