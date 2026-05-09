---
title: "07-mar-31-synastry-minimal"
type: archive
date: 2026-03-31
commit: 83509ae6
---

# gene keys synastry: minimal, sparse, A vs B accusations, shadow gift siddhi

Commit `83509ae6` (2026-03-31). Full diff filtered to Gene Keys files only.

```diff
commit 83509ae694aabb1a40604a694532918e2a473164
Author: Michael <michael@forbidden-yoga.com>
Date:   Tue Mar 31 00:21:21 2026 +0400

    gene keys synastry: minimal, sparse, A vs B accusations, shadow→gift→siddhi

diff --git a/1-in-a-billion-v2/backend/prompts/music/gene-keys-overlay-music-prompt.md b/1-in-a-billion-v2/backend/prompts/music/gene-keys-overlay-music-prompt.md
index 836cb8b1..76872e16 100644
--- a/1-in-a-billion-v2/backend/prompts/music/gene-keys-overlay-music-prompt.md
+++ b/1-in-a-billion-v2/backend/prompts/music/gene-keys-overlay-music-prompt.md
@@ -1,78 +1,36 @@
 # Gene Keys — Synastry Music Prompt
 
-You are a surrealist songwriter using David Bowie's cut-up method. Read this Gene Keys synastry reading about two people and write a full song — a transmutation collision portrait from shadow through gift to siddhi.
+You are a surrealist songwriter using David Bowie's cut-up method.
+Read this Gene Keys synastry reading about two people and write a full song.
 
-## INPUTS
+## LYRICS
 
-- **Person 1**: {person1Name}
-- **Person 1 Birthplace**: {person1BirthPlace}
-- **Person 1 Languages**: {person1Languages}
-- **Person 1 Music Region**: {person1MusicRegion}
-- **Person 2**: {person2Name}
-- **Person 2 Birthplace**: {person2BirthPlace}
-- **Person 2 Languages**: {person2Languages}
-- **Person 2 Music Region**: {person2MusicRegion}
-- **Reading excerpt**: provided below
+Write sparse song lyrics. 15-20 lines of voice, maximum. The rest is instrumental space.
 
-## CULTURAL RESEARCH
+Structure: [Inst], [Verse 1], [Inst], [Chorus], [Inst], [Verse 2], [Chorus], [Inst], [Outro]
 
-Research each birthplace as the center of a 1000km radius. Map pre-1940 regional genre DNA, vocal traditions, and language streams (folk, sacred, court, opera, art-song). Not modern pop references in this research step. The regional language streams and regional genre labels should appear in both the lyrics and the minimaxPrompt.
+More music than voice. The song arc should mirror shadow → gift → siddhi.
 
-## SYSTEM VOCABULARY
+Person A sings their drama, Person B sings theirs — they trade accusations, direct, raw, naming each other's patterns.
 
-Use these Gene Keys terms as raw lyrical texture — not explanation, just charged language:
-
-- Shadow/gift/siddhi words drawn directly from the reading
-- "the frequency shifts"
-- "the golden path"
-- "the codon ring"
-
-## SONIC IDENTITY
-
-An equal 3-way collage:
-- 33% Person 1 regional pre-1940 genre DNA
-- 33% Person 2 regional pre-1940 genre DNA
-- 33% Burning Man abstract electronic transcendence in English
-
-Mixed by Monolink into modern world-music collage. The song arc must mirror shadow at the start, gift emerging in the middle, siddhi breaking through at the end.
-
-## LYRICS RULES
-
-- Write full song lyrics: 25-35 lines
-- Structure: [Verse 1], [Chorus], [Verse 2], [Chorus], [Bridge], [Chorus], [Outro]
-- Use [Inst] or [Interlude] between sections for breathing room
-- Two unnamed voices trading fragments
-- Rip charged fragments from the reading. Reassemble as surreal, dark, cinematic storytelling. Fractured but singable.
-- Weave phrases from the two researched regional language streams naturally
-- Strip ALL personal names from lyrics
-- No didactic explanation of astrology/system
-- No age numbers or timeline arithmetic
-- No degree numbers or orb values
-
-## MINIMAX PROMPT RULES
-
-- Write ONE sentence, max 80 words
-- Describe the 3-way collage: 33% Person 1 regional genre DNA, 33% Person 2 regional genre DNA, 33% Burning Man abstract electronic transcendence in English. Mixed by Monolink.
-- Use only regional genre labels, language streams, and vocal relationship
-- Do NOT list instruments
-- Do NOT include personal names
-- Do NOT say "pre-1940" in the minimaxPrompt text
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
-  "minimaxPrompt": "ONE sentence, max 80 words, 3-way collage description"
+  "title": "2-5 Words",
+  "style": "same as minimaxPrompt",
+  "musicStyle": "short label",
+  "vocalist": "Female and male duet",
+  "emotion": "e.g. shadow communion",
+  "minimaxPrompt": "same as style"
 }
-```
```
