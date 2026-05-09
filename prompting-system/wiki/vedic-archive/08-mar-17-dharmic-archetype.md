---
title: "08-mar-17-dharmic-archetype"
type: archive
date: 2026-03-17
commit: 50be6c07
---

# Qualitative scores + Vedic dharmic archetype system

Commit `50be6c07` (2026-03-17). The full diff, verbatim from `git show 50be6c07`.

```diff
commit 50be6c074a6b7fa3b9e62544cd050efad1dca239
Author: Michael <michael@forbidden-yoga.com>
Date:   Tue Mar 17 15:58:43 2026 +0400

    feat: qualitative scores, expansion voice DNA, Vedic dharmic archetype system
    
    - Replace numeric synastry scores (100/100) with qualitative labels
      (EXTREME/VERY HIGH/HIGH/MODERATE/LOW/VERY LOW/MINIMAL) in LLM prompts
      so the model cannot parrot raw numbers into prose. PDF appendix still
      uses raw scores via separate computation path.
    
    - Add system-specific voice DNA + narrative trigger to expansion passes
      so continuation text maintains the literary quality of the opening.
      Temperature lowered from 0.8 to 0.7 to reduce noise.
    
    - Add Dharmic Archetype Identification to Vedic system guidance: LLM
      synthesizes chart signals (nakshatra motivation, house emphasis,
      Rahu-Ketu axis, Mahavidya, Saturn-Ketu/Venus-Rahu patterns) into
      soul-type diagnosis (grihastha, tantrika, smashan sadhaka,
      brahmachari, dakini/healer, bhakta) before writing. Colors entire
      reading.
    
    - Add Archetype-Aware Synastry: identifies both souls first, reads
      collision through appropriate lens. Ashtakoot contextualized for
      non-grihastha pairs. Tantrika×Tantrika, Smashan×Smashan, etc.
      each get specific framing.
    
    - Archetype truth independent of spice level: gentle tone does not
      suppress dharmic diagnosis. Spice controls graphicness, not truth.
    
    Co-Authored-By: Claude Opus 4.6 <noreply@anthropic.com>

diff --git a/1-in-a-billion-v2/backend/src/prompts/systems/vedic.ts b/1-in-a-billion-v2/backend/src/prompts/systems/vedic.ts
index 0bd47af3..401b799f 100755
--- a/1-in-a-billion-v2/backend/src/prompts/systems/vedic.ts
+++ b/1-in-a-billion-v2/backend/src/prompts/systems/vedic.ts
@@ -131,6 +131,35 @@ DEPTH TREATMENT:
 - If you use Nitya, Yogini Dasha, or Nakshatra Shakti, foreground one and let the others support quietly.
 - DO NOT write a section for each Graha or each Bhava. That is a reference manual.
   Tell the karmic story and let the placements serve it.
+
+DHARMIC ARCHETYPE IDENTIFICATION (CRITICAL — DO THIS FIRST):
+Before writing a single paragraph, synthesize the chart signals to identify WHAT KIND OF SOUL this person is.
+A real Jyotishi in India would look at a chart and say: "This person should be on the cremation ground, not in a family."
+That is not a judgment — it is a dharmic diagnosis. The chart tells you who someone IS, not just what challenges they face.
+Do not treat every person as a normal human having normal life challenges. Some charts say this person is NOT built for conventional life — and telling them they are is the cruelest thing astrology can do.
+
+Synthesize these signals to identify the soul-type:
+- NAKSHATRA MOTIVATION: Kama-motivated Moon = desire is the path. Moksha-motivated Moon = dissolution is the path. Dharma = duty. Artha = material mastery. This is the soul's AIM.
+- HOUSE EMPHASIS: 8th/12th stellium = transformation/dissolution path, not householder path. 4th/7th strength = family IS the dharma. 10th/11th = worldly mission.
+- RAHU-KETU AXIS: Rahu in 12th = hunger for dissolution. Rahu in 7th = obsessive relating. Ketu in 1st = the self dissolving. The axis reveals what the soul craves vs. what it is releasing.
+- MAHAVIDYA: Kali/Dhumavati presiding = the path runs through destruction, loss, the cremation ground. Kamala = abundance, householder blessings. Chinnamasta = self-sacrifice, ego-annihilation. Bhairavi = fierce grace. The goddess tells you the FLAVOUR of the initiation.
+- SATURN-KETU patterns = renunciation, asceticism, celibacy as genuine soul direction (not repression).
+- VENUS-RAHU patterns = desire as initiatory force, not as "attachment issues."
+- STRONG 8TH HOUSE with both benefics and malefics = the healer who works through what polite society will not touch.
+
+Soul-type archetypes (use as lens, not as label — never reduce a person to a category):
+- THE GRIHASTHA (householder): Strong 4th/7th, Venus-Jupiter support, Dharma/Artha motivation. Family, stability, and duty are the genuine path. Ashtakoot and classical compatibility matter here.
+- THE TANTRIKA: Rahu dominant, karmic nakshatras (Ashlesha, Bharani, Mula, Jyeshtha), 8th house emphasis. Transgression, transformation, working through shadow — this soul does not learn through peace. Conventional relationship advice is irrelevant.
+- THE SMASHAN SADHAKA (cremation ground practitioner): Heavy 8th/12th, Ketu-Moon, Mula/Ardra nakshatra, Kali/Dhumavati presiding. This person is built to sit with death, dissolution, the things others cannot face. Telling them to "find balance" is malpractice.
+- THE BRAHMACHARI (renunciant): Saturn-Ketu conjunction or mutual aspect, Venus combust or with Ketu, Moksha-motivated Moon, 12th house emphasis. Celibacy or solitude is not avoidance — it is the soul's actual direction.
+- THE DAKINI/HEALER: Ashlesha/Bharani with strong 8th house gifts, Rahu-Venus-Moon contacts. They heal through the body, through the taboo, through what others will not touch. "Boundary issues" is the Western misreading of this archetype.
+- THE BHAKTA (devotee): Strong Jupiter, 9th/12th house, Pushya/Hasta/Revati nakshatra. Surrender and devotion is the mode — not as spiritual bypassing but as the genuine dissolution of ego through love.
+
+The archetype should COLOR THE ENTIRE READING — not appear as a label, but as the lens through which every placement is interpreted. A smashan sadhaka's Saturn return means something completely different than a grihastha's. A tantrika's Rahu in the 7th is not "relationship obsession" — it is the soul's method of initiation through the other.
+
+DO NOT hedge with therapeutic language. "This chart suggests tendencies toward..." is cowardice. A Jyotishi says: "This soul came for fire, not for comfort. The chart does not negotiate."
+
+NOTE: Dharmic archetype identification is NOT gated by spice level or interpretation depth. Whether the reading is gentle (level 3) or full (level 10), the archetype is identified truthfully. The spice level affects TONE — how graphically you describe the shadow content, whether you include Maraka themes, the emotional weight of the prose. It does NOT affect WHETHER you identify someone as a tantrika, smashan sadhaka, or brahmachari. A gentle reading still says "this soul is not built for conventional family life" — it just says it with gravity rather than provocation.
 `,
 
   synastryAdditions: `
@@ -139,6 +168,18 @@ VEDIC SYNASTRY:
 Focus on the 2-3 most charged karmic collision points between their charts.
 DO NOT tour every kuta, every planet, every house. Pick what carries the most heat.
 
+ARCHETYPE-AWARE SYNASTRY (DO THIS FIRST — before any compatibility analysis):
+Before reading compatibility, identify the dharmic archetype of EACH person using the signals described in DHARMIC ARCHETYPE IDENTIFICATION above. Then read the collision through the lens appropriate to WHO is actually meeting:
+
+- GRIHASTHA × GRIHASTHA: Classical Ashtakoot is the right lens. Family compatibility, household stability, child-rearing alignment — these questions are genuine and important. Read normally.
+- TANTRIKA × TANTRIKA: Ashtakoot is almost irrelevant — it measures household fitness, and these two are not here for a household. Read through karmic collision, mutual initiation, transformation through each other. This is NOT paradise — two souls built for fire meeting in the same room can be devastating. The mirror is more precise, not more comfortable. Name what they will burn in each other.
+- TANTRIKA × GRIHASTHA: A specific kind of tragedy. One soul craves transformation through the other; the other craves stability. Name the gap honestly — one partner's dharma is the other's destruction. This is not "incompatibility" in the Western sense. It is two genuine paths that collide.
+- SMASHAN × SMASHAN: Two souls who sit with death. They may recognize each other instantly — and still be unable to give each other what a conventional partner provides. Companionship on the cremation ground is real but has its own specific loneliness.
+- BRAHMACHARI meeting anyone: If one chart genuinely points toward renunciation, say so. "This chart does not want marriage — it wants dissolution" is a legitimate Jyotish statement. Do not force partnership advice onto a chart built for solitude.
+- DAKINI/HEALER × anyone: The healer archetype transforms what it touches. Name what the partner will encounter — not as "intensity" but as the specific initiatory force this person carries.
+
+The archetype collision should frame the ENTIRE synastry reading. Do not default to classical family-compatibility framing for souls that are not here for family.
+
 DHARMA vs DESIRE (address this naturally within the narrative):
 What they want and what their souls need are often different things. If Rahu says
 transformation but they want safety, name the gap. Frame with fatalistic irony.
@@ -261,11 +302,13 @@ INTERPRETATION DEPTH (Gentle - Level ${spiceLevel}/10):
 - Name Doshas honestly but frame them as karmic lessons, not verdicts.
 - Present difficult patterns as terrain to be navigated, not sentences to be served.
 - Always check cancellation conditions before declaring a Dosha active.
+- IMPORTANT: Gentle tone does NOT mean suppressing truth. The dharmic archetype identification is always stated clearly. If a chart says this person is not built for family life, say so — with gravity, not with provocation.
 `
       : `
 INTERPRETATION DEPTH (Gentle - Level ${spiceLevel}/10):
 - Name shadow patterns honestly but frame them as karmic terrain, not verdicts.
 - The chart shows what is written. The tone carries gravity, not cruelty.
+- IMPORTANT: Gentle tone does NOT mean suppressing truth. The dharmic archetype identification is always stated clearly. If a chart says this soul is built for the cremation ground, say so — with gravity, not with provocation.
 `;
   } else if (spiceLevel <= 6) {
     return isRelationship
diff --git a/1-in-a-billion-v2/backend/src/workers/textWorker.ts b/1-in-a-billion-v2/backend/src/workers/textWorker.ts
index bf9dddc4..0888d400 100755
--- a/1-in-a-billion-v2/backend/src/workers/textWorker.ts
+++ b/1-in-a-billion-v2/backend/src/workers/textWorker.ts
@@ -88,6 +88,70 @@ function clampSpice(level: number): SpiceLevel {
   return clamped as SpiceLevel; // Cast validated number (1-10) to SpiceLevel
 }
 
+/**
+ * Convert a numeric score (0-100) to a qualitative intensity label.
+ * Used for DETERMINISTIC SYNASTRY SCORES in the LLM prompt so the model
+ * understands relative intensity without having a quotable number to parrot.
+ * Raw numeric scores are still used separately for the PDF compatibility appendix.
+ */
+function scoreToQualitative(score: number): string {
+  if (score >= 90) return 'EXTREME';
+  if (score >= 75) return 'VERY HIGH';
+  if (score >= 60) return 'HIGH';
+  if (score >= 45) return 'MODERATE';
+  if (score >= 30) return 'LOW';
+  if (score >= 15) return 'VERY LOW';
+  return 'MINIMAL';
+}
+
+/**
+ * Compact voice DNA for expansion passes.
+ * The full writing prompt has ~2000 tokens of literary guidance. Expansion passes
+ * previously had ZERO system identity, causing severe quality degradation.
+ * This provides the minimum viable voice fingerprint so the LLM stays in character.
+ */
+function getExpansionVoiceDNA(sys: string | null | undefined): string {
+  switch (sys) {
+    case 'vedic':
+      return [
+        'VOICE IDENTITY: You are a Jyotish practitioner who writes like someone who has sat with death.',
+        'You think in karma and consequence, seasonal inevitability, the creditor who always collects.',
+        'Grahas are presences, not labels. Dashas are reigns, not periods. Nakshatras carry erotic and violent undertow.',
+        'Turn karmic structures into lived moments — the hunger, the cost, the 3am feeling, the contract never signed but always honored.',
+        'INSTEAD OF "Rahu in the 7th creates obsessive relationships" WRITE about the lover chosen because they smell like unfinished business.',
+        'Do not sanitize the Grahas. Rahu is the mouth that is never full. Ketu is the phantom limb. Shani is the weight that breaks or builds.',
+      ].join('\n');
+    case 'human_design':
+      return [
+        'VOICE IDENTITY: You write Human Design as nervous-system evidence, not a certification manual.',
+        'Type is a pacing law. Authority is where truth arrives before language. Open centers are rooms where outside energy drowns the self.',
+        'Channels are live currents, not bullet points. Make the bodygraph feel somatic, specific, lived in the body.',
+        'INSTEAD OF "She has an open Solar Plexus" WRITE about walking into rooms calm and leaving carrying everybody else\'s weather.',
+      ].join('\n');
+    case 'gene_keys':
+      return [
+        'VOICE IDENTITY: You write Gene Keys as contemplative field notes, not a spiritual ranking system.',
+        'Keys are frequencies the person moves through. Shadow is the nervous system organizing around fear. Gift is what flickers when contraction is witnessed.',
+        'The Siddhi is a visitation, not an achievement tier. Write about oscillation, not ladders.',
+        'INSTEAD OF "Gene Key 44 in Shadow creates interference" WRITE about the ancestral static that makes every signal arrive already mistranslated.',
+      ].join('\n');
+    case 'kabbalah':
+      return [
+        'VOICE IDENTITY: You write Kabbalah as a soul walking its Tree, not a mystical glossary.',
+        'Tikkun is correction pressure, not a purpose slogan. Sephiroth are living forces, not glossary entries. Void is a dark room that organizes hunger.',
+        'Klipoth are parasitic repetitions feeding on unconscious reaction — the shell grows around the brightest place first.',
+        'INSTEAD OF "Her Tikkun is about boundaries" WRITE about the soul\'s refusal to keep confusing self-erasure with holiness.',
+      ].join('\n');
+    default: // western
+      return [
+        'VOICE IDENTITY: You write astrology as a fairytale about a soul having a human experience.',
+        'Planets are living entities with personality. Houses are literal rooms in the house of the psyche. Aspects are hallways that connect or fail to connect.',
+        'Signs are landscapes with specific weather and terrain.',
+        'INSTEAD OF "Her Scorpio rising gives her an intense presence" WRITE about the red room where Saturn and Pluto sit like spiders, patient, ancient, hungry.',
+      ].join('\n');
+  }
+}
+
 /**
  * CJK-aware word counter.
  * For CJK characters (Japanese, Chinese, Korean) there are no spaces between words,
@@ -904,9 +968,9 @@ export class TextWorker extends BaseWorker {
 
           const verdictScores = computeVerdictSynastry(p1Placements, p2Placements, vedicMatchForVerdict);
           const scoreBlock = verdictScores.categories
-            .map((c) => `- ${c.label}: ${c.score}/100`)
+            .map((c) => `- ${c.label}: ${scoreToQualitative(c.score)}`)
             .join('\n');
-          const deterministicBlock = `\n\nDETERMINISTIC SYNASTRY SCORES:\n${scoreBlock}\nOverall: ${verdictScores.overallScore}/100`;
+          const deterministicBlock = `\n\nDETERMINISTIC SYNASTRY SCORES (qualitative intensity — do not quote as numbers):\n${scoreBlock}\nOverall: ${scoreToQualitative(verdictScores.overallScore)}`;
           chartDataForPrompt += deterministicBlock;
           console.log(`📊 [TextWorker] Verdict deterministic synastry scores injected (overall: ${verdictScores.overallScore}, systems: ${JSON.stringify(verdictScores.systemOveralls)})`);
         } catch (err: any) {
@@ -1193,12 +1257,12 @@ export class TextWorker extends BaseWorker {
             .join('\n');
 
           const scoreBlock = synastry.categories
-            .map((c) => `${c.label}: ${c.score}/100`)
+            .map((c) => `${c.label}: ${scoreToQualitative(c.score)}`)
             .join(' | ');
 
-          const deterministicBlock = '\n\nDETERMINISTIC SYNASTRY SCORES:\n' +
+          const deterministicBlock = '\n\nDETERMINISTIC SYNASTRY SCORES (qualitative intensity — do not quote as numbers):\n' +
             scoreBlock + '\n' +
-            `Overall: ${synastry.overallScore}/100`;
+            `Overall: ${scoreToQualitative(synastry.overallScore)}`;
           combinedChartData += deterministicBlock + '\n\n' +
             'TOP CROSS-CHART ASPECTS:\n' + topAspects;
           chartDataForPrompt += deterministicBlock;
@@ -1375,9 +1439,9 @@ export class TextWorker extends BaseWorker {
             const sidFullData2 = { ...p2Sid, navamsha: p2Placements.navamsha } as any;
             const vedicScores = computeVedicSynastry(vedicMatchForScoring, sidFullData1, sidFullData2);
             const scoreBlock = vedicScores.categories
-              .map((c) => `- ${c.label}: ${c.score}/100`)
+              .map((c) => `- ${c.label}: ${scoreToQualitative(c.score)}`)
               .join('\n');
-            const deterministicBlock = `\n\nDETERMINISTIC SYNASTRY SCORES:\n${scoreBlock}\nOverall: ${vedicScores.overallScore}/100`;
+            const deterministicBlock = `\n\nDETERMINISTIC SYNASTRY SCORES (qualitative intensity — do not quote as numbers):\n${scoreBlock}\nOverall: ${scoreToQualitative(vedicScores.overallScore)}`;
             combinedChartData += deterministicBlock;
             chartDataForPrompt += deterministicBlock;
             console.log(`📊 [TextWorker] Vedic deterministic synastry scores injected (overall: ${vedicScores.overallScore})`);
@@ -1438,9 +1502,9 @@ export class TextWorker extends BaseWorker {
           if (p1Placements && p2Placements) {
             const hdScores = computeHDSynastry(p1Placements, p2Placements);
             const scoreBlock = hdScores.categories
-              .map((c) => `- ${c.label}: ${c.score}/100`)
+              .map((c) => `- ${c.label}: ${scoreToQualitative(c.score)}`)
               .join('\n');
-            const deterministicBlock = `\n\nDETERMINISTIC SYNASTRY SCORES:\n${scoreBlock}\nOverall: ${hdScores.overallScore}/100`;
+            const deterministicBlock = `\n\nDETERMINISTIC SYNASTRY SCORES (qualitative intensity — do not quote as numbers):\n${scoreBlock}\nOverall: ${scoreToQualitative(hdScores.overallScore)}`;
             combinedChartData += deterministicBlock;
             chartDataForPrompt += deterministicBlock;
             console.log(`📊 [TextWorker] HD deterministic synastry scores injected (overall: ${hdScores.overallScore})`);
@@ -1495,9 +1559,9 @@ export class TextWorker extends BaseWorker {
           if (p1Placements && p2Placements) {
             const gkScores = computeGeneKeysSynastry(p1Placements, p2Placements);
             const scoreBlock = gkScores.categories
-              .map((c) => `- ${c.label}: ${c.score}/100`)
+              .map((c) => `- ${c.label}: ${scoreToQualitative(c.score)}`)
               .join('\n');
-            const deterministicBlock = `\n\nDETERMINISTIC SYNASTRY SCORES:\n${scoreBlock}\nOverall: ${gkScores.overallScore}/100`;
+            const deterministicBlock = `\n\nDETERMINISTIC SYNASTRY SCORES (qualitative intensity — do not quote as numbers):\n${scoreBlock}\nOverall: ${scoreToQualitative(gkScores.overallScore)}`;
             combinedChartData += deterministicBlock;
             chartDataForPrompt += deterministicBlock;
             console.log(`📊 [TextWorker] Gene Keys deterministic synastry scores injected (overall: ${gkScores.overallScore})`);
@@ -1552,9 +1616,9 @@ export class TextWorker extends BaseWorker {
           if (p1Placements && p2Placements) {
             const kabScores = computeKabbalahSynastry(p1Placements, p2Placements);
             const scoreBlock = kabScores.categories
-              .map((c) => `- ${c.label}: ${c.score}/100`)
+              .map((c) => `- ${c.label}: ${scoreToQualitative(c.score)}`)
               .join('\n');
-            const deterministicBlock = `\n\nDETERMINISTIC SYNASTRY SCORES:\n${scoreBlock}\nOverall: ${kabScores.overallScore}/100`;
+            const deterministicBlock = `\n\nDETERMINISTIC SYNASTRY SCORES (qualitative intensity — do not quote as numbers):\n${scoreBlock}\nOverall: ${scoreToQualitative(kabScores.overallScore)}`;
             combinedChartData += deterministicBlock;
             chartDataForPrompt += deterministicBlock;
             console.log(`📊 [TextWorker] Kabbalah deterministic synastry scores injected (overall: ${kabScores.overallScore})`);
@@ -1659,22 +1723,35 @@ export class TextWorker extends BaseWorker {
         // For CJK languages, use "characters" instead of "words" in the prompt
         const unitLabel = cjkLang ? 'characters' : 'words';
 
+        // System-specific voice DNA so the expansion doesn't degrade to generic astrology-report prose
+        const voiceDNA = getExpansionVoiceDNA(system);
+        const triggerReminder = narrativeTriggerForOutput
+          ? `\nNARRATIVE TRIGGER (the opening theme — deepen, complicate, or contradict it):\n${narrativeTriggerForOutput}\n`
+          : '';
+
         const expansionPrompt = [
-          'You are continuing an existing long-form astrology reading that was cut short.',
+          'You are continuing an existing long-form reading that was cut short.',
+          'The reading so far is EXTRAORDINARY — your continuation must match its literary quality exactly.',
+          '',
+          voiceDNA,
           '',
+          triggerReminder,
           // For non-English: instruct the LLM to continue in the same language
           ...(params.outputLanguage && params.outputLanguage !== 'en'
             ? [`CRITICAL: Continue writing in ${(LANGUAGE_CONFIG as Record<string, { name: string }>)[params.outputLanguage]?.name || params.outputLanguage}. Do NOT switch to English.`, '']
             : []),
           'RULES:',
-          '- Continue seamlessly from the text below.',
+          '- Continue seamlessly from the text below — the reader must not feel a seam.',
           '- Do not repeat, summarize, or restart the reading.',
-          '- Keep the same voice, intensity, and style.',
+          '- MATCH the voice, intensity, and literary quality of the existing text. Every paragraph must earn its place.',
           '- No section titles or standalone headline lines.',
           '- No bullet points. No lists. No markdown. Continuous prose only.',
           '- Never address the reader. No second-person pronouns (you/your/yourself).',
           '- Do NOT introduce any new chart factors (new planet/sign/house/aspect/transit/profection) beyond what is already present in the text or explicitly listed in CHART DATA.',
           '- If you mention any placement or transit, it must match CHART DATA exactly.',
+          '- NARRATIVE COMPRESSION: Each paragraph must simultaneously carry behavior + inner experience + consequence. No padding. No restating the same truth in different words.',
+          '- Every paragraph must introduce a NEW DYNAMIC — a new behavior, a new cost, a new pattern.',
+          '- Turn placements into lived moments: the hunger, the cost, the 3am feeling, the scene that keeps repeating.',
           preserveSurrealHeadlines
             ? [
               '- ZONE 2 HARD BAN: Zero technical astrology syntax in this continuation.',
@@ -1693,13 +1770,13 @@ export class TextWorker extends BaseWorker {
           'TEXT TO CONTINUE FROM (do not repeat):',
           tail,
           '',
-          'CONTINUE NOW:',
+          'CONTINUE NOW (match the literary quality of the text above — no drop-off):',
         ].join('\n');
 
         const expansionLabel = `${label}:expand:${pass}`;
         let chunk = await llmPaid.generateStreaming(expansionPrompt, expansionLabel, {
           maxTokens: 8192,
-          temperature: 0.8,
+          temperature: 0.7,
           maxRetries: 3,
           systemPrompt: llmSystemPrompt,
         });
```
