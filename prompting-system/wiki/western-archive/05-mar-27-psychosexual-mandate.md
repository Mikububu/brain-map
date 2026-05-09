---
title: "08-mar-27-psychosexual-mandate"
type: archive
date: 2026-03-27
commit: edeb0c62
---

# Psychosexual mandate scoped to Western only

Commit `edeb0c62` (2026-03-27). Full diff verbatim from `git show edeb0c62`.

```diff
commit edeb0c62e8c89a69871f2f3593fd1491d212bc09
Author: Michael <michael@forbidden-yoga.com>
Date:   Fri Mar 27 08:02:41 2026 +0400

    Scope psychosexual rewrite mandate to Western only and strengthen full-text western contract

diff --git a/1-in-a-billion-v2/backend/prompt-layers/rewrite/narrative-rewrite-western.md b/1-in-a-billion-v2/backend/prompt-layers/rewrite/narrative-rewrite-western.md
index 156614f3..543e1409 100644
--- a/1-in-a-billion-v2/backend/prompt-layers/rewrite/narrative-rewrite-western.md
+++ b/1-in-a-billion-v2/backend/prompt-layers/rewrite/narrative-rewrite-western.md
@@ -23,13 +23,19 @@ DUAL-LANGUAGE EXPLANATION MODE — CREATIVE BRIEF:
 - Never moralize or shame desire.
 - Use explicit adult labels freely when intensity peaks (fetish, dominance/submission, obsessive desire, nymphomaniac hunger as archetypal shorthand).
 
-PSYCHOSEXUAL TRANSLATION MANDATE:
-- After naming one astro/system anchor once, translate into modern human language. No technical repetition.
-- Soft rule: if a motif repeats three or more times in the analysis, usually treat it as a primary driver unless evidence is weak.
+GLOBAL STYLE CONTRACT (APPLIES TO ENTIRE OUTPUT):
+- This is adult (18+), consent-centered psychosexual analysis.
+- Keep astrology anchors as precision terms, but do not hide behind jargon after first anchor.
+- When evidence is strong, use direct modern erotic/relational terminology throughout the full narration, not in one isolated section.
+- Do not sanitize intensity into soft romantic euphemisms.
+- Do not moralize. Do not shame.
+
+PSYCHOSEXUAL LANGUAGE RULES:
+- After naming one astro/system anchor once, continue in modern human language. No technical repetition loops.
+- If intimacy/power motifs converge across three or more independent indicators, treat that as a primary driver unless evidence is weak.
 - Allowed labels (use directly when they fit): compulsive erotic drive (or nymphomaniac drive), submissive behavior pattern, dominance-seeking pattern, fetishized power asymmetry, humiliation/validation loop, avoidant-intimacy split, obsessional attachment loop.
-- For each primary driver, make sure the prose shows: the label, what they actually do, the relational cost, and what conscious expression looks like (consensual, ethical, contained).
-- Use phrasing like "they function best when this drive is consciously structured" instead of lifestyle prescriptions.
-- Do not sanitize. Do not moralize. Do not hide behind astrology jargon.
+- For each primary driver, ensure the prose shows: the label, what they actually do, the relational cost, and what conscious expression looks like (consensual, ethical, contained).
+- Prefer phrasing like "they function best when this drive is consciously structured" over lifestyle prescriptions.
 
 CRITICAL: Write in THIRD PERSON throughout. The narrator is invisible. Never use "I", "me", "my", or "we". Never reveal who you were in your past life — never mention your former name. Your identity is a secret you carry; the reader experiences only the prose, never the author behind it.
 
diff --git a/1-in-a-billion-v2/backend/src/workers/textWorker.ts b/1-in-a-billion-v2/backend/src/workers/textWorker.ts
index afe764f9..d5cf4f96 100755
--- a/1-in-a-billion-v2/backend/src/workers/textWorker.ts
+++ b/1-in-a-billion-v2/backend/src/workers/textWorker.ts
@@ -2409,6 +2409,7 @@ Do not recompute or contradict them.
       };
       const systemSuffix = system ? systemKeyMap[system] || 'western' : 'western';
       const rewriteFileName = `narrative-rewrite-${systemSuffix}.md`;
+      const isWesternRewrite = systemSuffix === 'western';
 
       // Load from filesystem ONLY — git is the source of truth
       let systemRewriteInstructions = '';
@@ -2448,7 +2449,7 @@ Do not recompute or contradict them.
         }
       }
 
-      const NARRATIVE_TRANSFORMATION_GUARDRAIL = [
+      const narrativeGuardrailLines = [
         'TRANSFORMATION CONTRACT (NON-NEGOTIABLE):',
         '- The reading below is source material to transform, not to recite as a report.',
         '- The style reference is stylistic fuel, not a script.',
@@ -2456,21 +2457,30 @@ Do not recompute or contradict them.
         '- Convert analytical/technical statements into lived human scenes, sensations, behavior, and consequence.',
         '- Keep system terms as anchors when they carry precision.',
         '- Keep most prose in lived modern language between those anchors.',
-        '- Use explicit adult labels freely when intensity peaks.',
-        '- Never moralize or shame desire; keep the tone unsanitized and exact.',
+        '- Name desire with precision; keep the tone unsanitized and exact.',
+        '- Never moralize or shame desire.',
         '- Start with a fresh opening each time; avoid template openings.',
         '- For synastry/verdict texts, describe the present dynamic field without assuming marriage unless user context explicitly says so.',
         '- Keep all factual conclusions and emotional truth; transform the language into stronger prose.',
-      ].join('\n');
-
-      const PSYCHOSEXUAL_TRANSLATION_MANDATE = [
-        'PSYCHOSEXUAL TRANSLATION MANDATE (LAYER 3):',
-        '- After naming one system anchor once, translate into modern human language. No technical repetition.',
-        '- Soft rule: if a motif repeats three or more times in the analysis, usually treat it as a primary driver unless evidence is weak.',
-        '- Allowed labels (use directly when they fit): compulsive erotic drive (or nymphomaniac drive), submissive behavior pattern, dominance-seeking pattern, fetishized power asymmetry, humiliation/validation loop, avoidant-intimacy split, obsessional attachment loop.',
-        '- For each primary driver, make sure the prose shows: the label, what they actually do, the relational cost, and what conscious expression looks like (consensual, ethical, contained).',
-        '- Use phrasing like "they function best when this drive is consciously structured" instead of lifestyle prescriptions.',
-        '- Do not sanitize. Do not moralize. Do not hide behind system jargon.',
+      ];
+      if (isWesternRewrite) {
+        narrativeGuardrailLines.push(
+          '- Western mode: when evidence supports intensity, keep direct modern erotic terminology consistently across the full narration, not in isolated sections.'
+        );
+      }
+      const NARRATIVE_TRANSFORMATION_GUARDRAIL = narrativeGuardrailLines.join('\n');
+
+      const WESTERN_PSYCHOSEXUAL_STYLE_CONTRACT = [
+        'GLOBAL STYLE CONTRACT (WESTERN ONLY):',
+        '- This is adult (18+), consent-centered psychosexual analysis.',
+        '- Keep astrology anchors, but do not hide behind jargon after first anchor.',
+        '- When evidence is strong, use direct modern erotic/relational terminology throughout the full text.',
+        '- Do not sanitize intensity into soft romantic euphemisms.',
+        '- Do not moralize. Do not shame.',
+        '- If intimacy/power motifs converge across three or more independent indicators, name the primary pattern directly.',
+        '- Allowed direct labels when evidence supports them: compulsive erotic drive (or nymphomaniac drive), submissive behavior pattern, dominance-seeking pattern, fetishized power asymmetry, humiliation/validation loop, avoidant-intimacy split, obsessional attachment loop.',
+        '- For each primary pattern, the prose must show: the label, lived behavior, relational cost, and conscious consensual expression.',
+        '- Preferred framing: "they function best when this drive is consciously structured."',
       ].join('\n');
 
       const rewritePrompt = systemRewriteInstructions
@@ -2481,8 +2491,7 @@ Do not recompute or contradict them.
             '',
             NARRATIVE_TRANSFORMATION_GUARDRAIL,
             '',
-            PSYCHOSEXUAL_TRANSLATION_MANDATE,
-            '',
+            ...(isWesternRewrite ? [WESTERN_PSYCHOSEXUAL_STYLE_CONTRACT, ''] : []),
             'PERSONAL QUESTION HANDLING:',
             'If the reading below contains a section marked "═══ PERSONAL QUESTION ANALYSIS ═══",',
             'rewrite it in your literary voice and place it as the OPENING of your essay — the very first page.',
@@ -2505,8 +2514,7 @@ Do not recompute or contradict them.
             '',
             NARRATIVE_TRANSFORMATION_GUARDRAIL,
             '',
-            PSYCHOSEXUAL_TRANSLATION_MANDATE,
-            '',
+            ...(isWesternRewrite ? [WESTERN_PSYCHOSEXUAL_STYLE_CONTRACT, ''] : []),
             'READING TO REWRITE:',
             initial,
           ].join('\n');
```
