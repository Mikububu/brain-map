---
title: 05-mar-31-strip-essentials
type: archive
date: 2026-03-31
commit: 43af4f68
---

# gene keys individual: stripped to essentials, no system language, no artist refs

Commit `43af4f68` (2026-03-31). Full diff filtered to Gene Keys files only.

```diff
commit 43af4f682f77f959dccf849e1d8f16bd2f651598
Author: Michael <michael@forbidden-yoga.com>
Date:   Tue Mar 31 00:19:46 2026 +0400

    gene keys individual: stripped to essentials, no system language, no artist refs

diff --git a/1-in-a-billion-v2/backend/prompts/music/gene-keys-music-prompt.md b/1-in-a-billion-v2/backend/prompts/music/gene-keys-music-prompt.md
index 29754090..59d39f58 100644
--- a/1-in-a-billion-v2/backend/prompts/music/gene-keys-music-prompt.md
+++ b/1-in-a-billion-v2/backend/prompts/music/gene-keys-music-prompt.md
@@ -1,70 +1,34 @@
-# Gene Keys — Individual Music Prompt
+# Gene Keys — Music Prompt
 
-You are a surrealist songwriter using David Bowie's cut-up method. Read this Gene Keys reading about one person and write a full song — a transmutation portrait from shadow through gift to siddhi.
+You are a surrealist songwriter using David Bowie's cut-up method.
+Read this Gene Keys reading and write a full song.
 
-## INPUTS
+## LYRICS
 
-- **Person**: {personName}
-- **Birthplace**: {person1BirthPlace}
-- **Languages**: {person1Languages}
-- **Reading excerpt**: provided below
+Write full song lyrics. 25-35 lines. Verse, chorus, verse, chorus, bridge, chorus, outro.
 
-## SYSTEM VOCABULARY
+Rip the most charged fragments from the reading below. Reassemble into surreal, dark, cinematic storytelling. Fractured but singable. The song arc should mirror shadow → gift → siddhi.
 
-Use these Gene Keys terms as raw lyrical texture — not explanation, just charged language:
+No system language. No Gene Keys terminology. Only the raw human transformation underneath.
 
-- Shadow/gift/siddhi words drawn directly from the reading
-- "the frequency shifts"
-- "the golden path"
-- "the codon ring"
-
-## SONIC IDENTITY
-
-Randomly select ONE of the following artists as the musical anchor for this song. Adapt the choice to what you feel in the reading:
-
-- Radiohead (Kid A)
-- Bon Iver (For Emma)
-- FKA Twigs (Magdalene)
-- Sigur Ros (Takk)
-- James Blake (Overgrown)
-- Sevdaliza (Shabrang)
-- Thom Yorke (Anima)
-
-The song arc must mirror the Gene Keys journey: shadow at the start, gift emerging in the middle, siddhi breaking through at the end.
-
-## LYRICS RULES
-
-- Write full song lyrics: 25-35 lines
-- Structure: [Verse 1], [Chorus], [Verse 2], [Chorus], [Bridge], [Chorus], [Outro]
-- Use [Inst] or [Interlude] between sections for breathing room
-- Rip charged fragments from the reading. Reassemble as surreal, dark, cinematic storytelling. Fractured but singable.
-- Strip ALL personal names from lyrics
-- No didactic explanation of astrology/system
-- No age numbers or timeline arithmetic
-- No degree numbers or orb values
-
-## MINIMAX PROMPT RULES
-
-- Write ONE sentence, max 50 words
-- Describe genre + mood + vocal style only
-- Do NOT list instruments
-- Do NOT include personal names
-
-## READING
+Hard bans:
+- No personal names.
 
+**Reading:**
 {readingExcerpt}
 
-## OUTPUT
+## MINIMAX PROMPT
+
+50-80 words. Modern, intimate, emotionally resonant. Adapt to what you feel in the reading. Do not list instruments. Use only concise style/mood language.
 
-Return ONLY valid JSON:
+## OUTPUT (JSON only)
 
-```
 {
   "lyrics": "[Verse 1]\n...\n[Chorus]\n...",
-  "title": "2-5 word title",
-  "musicStyle": "short genre label",
-  "vocalist": "vocal description",
-  "emotion": "1-3 word emotion label",
-  "minimaxPrompt": "ONE sentence, max 50 words, genre + mood + vocal only"
+  "title": "2-5 Words",
+  "style": "same as minimaxPrompt",
+  "musicStyle": "short label",
+  "vocalist": "Female vocalist",
+  "emotion": "e.g. trembling transformation",
+  "minimaxPrompt": "same as style"
 }
-```
```
