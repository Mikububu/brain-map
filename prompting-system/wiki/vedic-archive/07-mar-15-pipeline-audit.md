---
title: 07-mar-15-pipeline-audit
type: archive
date: 2026-03-15
commit: b20fba9e
---

# Vedic pipeline audit, spice level, system prompt, terminology

Commit `b20fba9e` (2026-03-15). The full diff, verbatim from `git show b20fba9e`.

```diff
commit b20fba9e88bc61cf2be7f5fe20e9caa4636b2fea
Author: Michael <michael@forbidden-yoga.com>
Date:   Sun Mar 15 00:32:56 2026 +0400

    fix: Vedic pipeline audit fixes — spice level, system prompt, terminology
    
    - P0: buildVedicSection spice level was hardcoded to 7, now passes
      user's actual spice preference through from textWorker.
    - P1: Narrative rewrite (3rd pass) now has a proper system prompt
      instead of undefined — Svoboda Aghori identity for Vedic, generic
      novelist for Western. Prevents identity drift.
    - P2: VEDIC_TERMINOLOGY_RULE now injected into the Vedic narrative
      rewrite identity block, ensuring Moon/Mars/Saturn stay English
      while Rahu/Ketu/Nakshatra stay Sanskrit through the final pass.
    
    Co-Authored-By: Claude Opus 4.6 <noreply@anthropic.com>

diff --git a/1-in-a-billion-v2/backend/src/promptEngine/triggerEngine/vedicTrigger.ts b/1-in-a-billion-v2/backend/src/promptEngine/triggerEngine/vedicTrigger.ts
index d51c63fe..121ca83c 100644
--- a/1-in-a-billion-v2/backend/src/promptEngine/triggerEngine/vedicTrigger.ts
+++ b/1-in-a-billion-v2/backend/src/promptEngine/triggerEngine/vedicTrigger.ts
@@ -214,14 +214,15 @@ export function buildVedicWritingPrompt(params: {
   narrativeTrigger: string;
   strippedChartData: string;
   targetWords: number;
+  spiceLevel?: number;
   language?: OutputLanguage;
 }): string {
   const { personName, narrativeTrigger, strippedChartData, targetWords } = params;
   const trigger = NARRATIVE_TRIGGER_LABEL;
   const triggerTitle = NARRATIVE_TRIGGER_TITLE;
 
-  // Inject the Vedic system guidance with its Rahu-first perspective, fairy-tale explanations, and fatalistic humor
-  const vedicGuidance = buildVedicSection(false, 7);
+  // Inject the Vedic system guidance — use the user's actual spice level (not hardcoded 7)
+  const vedicGuidance = buildVedicSection(false, params.spiceLevel ?? 7);
 
   return [
     'You are a Kaula Jyotishi and literary novelist — every planet is a deity, every Nakshatra a yogini field. You read through shadow, through what is forbidden. Classical Jyotish mechanics, tantric interpretation.',
diff --git a/1-in-a-billion-v2/backend/src/workers/textWorker.ts b/1-in-a-billion-v2/backend/src/workers/textWorker.ts
index f1e2fbd8..0c10456a 100755
--- a/1-in-a-billion-v2/backend/src/workers/textWorker.ts
+++ b/1-in-a-billion-v2/backend/src/workers/textWorker.ts
@@ -44,6 +44,7 @@ import {
   buildVedicTriggerPrompt,
   buildVedicWritingPrompt,
 } from '../promptEngine/triggerEngine/vedicTrigger';
+import { VEDIC_TERMINOLOGY_RULE } from '../prompts/systems/vedic';
 import {
   stripHDChartData,
   buildHDTriggerPrompt,
@@ -1027,6 +1028,7 @@ export class TextWorker extends BaseWorker {
           narrativeTrigger,
           strippedChartData: stripped,
           targetWords: WORD_COUNT_LIMITS.min,
+          spiceLevel,
           language: params.outputLanguage,
         });
         const writingPrompt = `${chartProvocationsV}\n\n${baseWritingPromptV}`;
@@ -1851,6 +1853,8 @@ export class TextWorker extends BaseWorker {
         '- Mahadasha/Antardasha labels. "Since 2017, Saturn has presided over her life" — not "Saturn Mahadasha 2017-2036."',
         '- Repeated nakshatra names. Named once, then called by nature.',
         '- All "X steht in Y" / "X sits in Y" chart-report syntax. Describe the EXPERIENCE.',
+        '',
+        VEDIC_TERMINOLOGY_RULE,
       ];
 
       const westernIdentity = [
@@ -1887,6 +1891,11 @@ export class TextWorker extends BaseWorker {
         initial,
       ].join('\n');
 
+      // Give the rewrite call a system prompt so identity doesn't drift
+      const rewriteSystemPrompt = system === 'vedic'
+        ? 'You are a tantric novelist in the tradition of Robert Svoboda\'s Aghora. You rewrite Jyotishi readings as literature. The goddesses are real. The karma is physics. Third person only.'
+        : 'You are a literary novelist. You rewrite astrological readings as human stories. Third person only.';
+
       const rewriteLabel = `${label}:narrative-rewrite`;
       let rewritten: string;
       if (configuredProvider === 'claude') {
@@ -1894,14 +1903,14 @@ export class TextWorker extends BaseWorker {
           maxTokens: 20000,
           temperature: 0.7,
           maxRetries: 3,
-          systemPrompt: llmSystemPrompt,
+          systemPrompt: rewriteSystemPrompt,
         });
       } else {
         rewritten = await llm.generate(rewritePrompt, rewriteLabel, {
           maxTokens: 12000,
           temperature: 0.7,
           provider: configuredProvider as LLMProvider,
-          systemPrompt: llmSystemPrompt,
+          systemPrompt: rewriteSystemPrompt,
         });
       }
 
```
