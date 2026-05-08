---
title: 08 - Hebrew reverted to multi-language (Mar 31)
type: archive
date: 2026-03-31
commit: de8a0cb0
---

# Hebrew reverted to multi-language mirror

Commit `de8a0cb0`. The reversion. Three-language structural rule restored.

```diff
commit de8a0cb0b9d8d39ed596bf930550a746648203bb
Author: Michael <michael@forbidden-yoga.com>
Date:   Tue Mar 31 00:04:35 2026 +0400

    kabbalah single + synastry: Hebrew mirror of vedic prompts

diff --git a/1-in-a-billion-v2/backend/prompts/music/kabbalah-music-prompt.md b/1-in-a-billion-v2/backend/prompts/music/kabbalah-music-prompt.md
index fc8e3bee..5cf15ec2 100644
--- a/1-in-a-billion-v2/backend/prompts/music/kabbalah-music-prompt.md
+++ b/1-in-a-billion-v2/backend/prompts/music/kabbalah-music-prompt.md
@@ -1,61 +1,42 @@
-# Kabbalah — Individual Music Prompt
+# Kabbalah — Music Prompt
 
-You are a surrealist songwriter using David Bowie's cut-up method. Read this Kabbalah reading about one person and write a full song — a sacred inner-landscape portrait.
+You are a surrealist songwriter using David Bowie's cut-up method.
+Read this Kabbalistic reading and write a full song.
 
-## INPUTS
+## LYRICS
 
-- **Person**: {personName}
-- **Birthplace**: {person1BirthPlace}
-- **Languages**: {person1Languages}
-- **Reading excerpt**: provided below
+Write full song lyrics. 25-35 lines. Verse, chorus, verse, chorus, bridge, chorus, outro.
 
-## SYSTEM VOCABULARY
+Rip the most charged fragments from the reading below. Reassemble into surreal, dark, cinematic storytelling. Fractured but singable.
 
-Use these Kabbalah terms as raw lyrical texture — not explanation, just charged language:
+Use only known Kabbalistic terms as raw texture: "ein sof", "tikkun", "the vessels shatter", "klipot", "Gevurah", "Binah", "Yesod", "the tree of life".
 
-- "ein sof"
-- "tikkun"
-- "the vessels shatter"
-- "klipot"
-- Sephirot names: Gevurah, Binah, Yesod (and others from the reading)
+Language behavior:
+- Weave English with selective Hebrew mystical fragments.
+- Repetition should feel like invocation, not explanation.
 
-## SONIC IDENTITY
-
-50% modern cinematic pop, 50% Hebrew mystical chanting. Vocalist weaves English with Hebrew. Intimate, melancholic, sacred, pop-forward. The result should feel like a prayer that accidentally became a pop song — devotional weight inside a modern hook.
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
+- No didactic explanation of Kabbalah.
+- No age numbers or timeline arithmetic.
 
+**Reading:**
 {readingExcerpt}
 
-## OUTPUT
+## MINIMAX PROMPT
+
+50-80 words. Keep the blend strict: 50% modern cinematic pop production, 50% Hebrew mystical chanting.
+Vocalist weaves English with Hebrew phrases. Overall result must feel pop and hook-driven.
+Do not list instruments. Use only concise style/mood language.
 
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
+  "emotion": "e.g. sacred rupture",
+  "minimaxPrompt": "50% modern cinematic pop, 50% Hebrew mystical chant; female vocal in English and Hebrew, intimate, hook-driven, melancholic, sacred."
 }
-```
diff --git a/1-in-a-billion-v2/backend/prompts/music/kabbalah-overlay-music-prompt.md b/1-in-a-billion-v2/backend/prompts/music/kabbalah-overlay-music-prompt.md
index 3edf184e..833ee21e 100644
--- a/1-in-a-billion-v2/backend/prompts/music/kabbalah-overlay-music-prompt.md
+++ b/1-in-a-billion-v2/backend/prompts/music/kabbalah-overlay-music-prompt.md
@@ -1,79 +1,51 @@
 # Kabbalah — Synastry Music Prompt
 
-You are a surrealist songwriter using David Bowie's cut-up method. Read this Kabbalah synastry reading about two people and write a full song — a sacred collision portrait.
+You are a surrealist songwriter using David Bowie's cut-up method.
+Read this Kabbalistic synastry reading about two people and write a full song.
 
-## INPUTS
+## CULTURAL INPUTS
 
-- **Person 1**: {person1Name}
-- **Person 1 Birthplace**: {person1BirthPlace}
-- **Person 1 Languages**: {person1Languages}
-- **Person 1 Music Region**: {person1MusicRegion}
-- **Person 2**: {person2Name}
-- **Person 2 Birthplace**: {person2BirthPlace}
-- **Person 2 Languages**: {person2Languages}
-- **Person 2 Music Region**: {person2MusicRegion}
-- **Reading excerpt**: provided below
+- **Person 1** from {person1BirthPlace} — languages: {person1Languages}
+- **Person 2** from {person2BirthPlace} — languages: {person2Languages}
 
-## CULTURAL RESEARCH
+Research each birthplace. What music lives in that soil? Folk, sacred, court, street. Use that cultural DNA as texture in the lyrics and in the MiniMax prompt.
 
-Research each birthplace as the center of a 1000km radius. Map pre-1940 regional genre DNA, vocal traditions, and language streams (folk, sacred, court, opera, art-song). Not modern pop references in this research step. The regional language streams and regional genre labels should appear in both the lyrics and the minimaxPrompt.
+## LYRICS
 
-## SYSTEM VOCABULARY
+Write sparse song lyrics. 15-20 lines of voice, maximum. The rest is instrumental space.
 
-Use these Kabbalah terms as raw lyrical texture — not explanation, just charged language:
+Structure: [Inst], [Verse 1], [Inst], [Chorus], [Inst], [Verse 2], [Chorus], [Inst], [Outro]
 
-- "ein sof"
-- "tikkun"
-- "the vessels shatter"
-- "klipot"
-- Sephirot names: Gevurah, Binah, Yesod (and others from the reading)
+More silence than words. More sound than singing. Two unnamed voices trading short fragments between long instrumental passages. Every vocal line must earn its place.
 
-## SONIC IDENTITY
+Use only known Kabbalistic terms as raw texture: "ein sof", "tikkun", "the vessels shatter", "klipot", "Gevurah", "Binah", "Yesod", "the tree of life".
 
-An equal 3-way collage:
-- 33% Person 1 regional pre-1940 genre DNA
-- 33% Person 2 regional pre-1940 genre DNA
-- 33% Hebrew mystical chant in Hebrew
+Language behavior — tri-et, never overlapping:
+- Person 1's cultural language gets its own sections.
+- Person 2's cultural language gets its own sections.
+- Hebrew mystical fragments get their own sections.
+- Each language sings alone. They answer each other across the song, never blend in the same line.
 
-Mixed by Brian Eno into modern world-music collage.
-
-## LYRICS RULES
-
-- Write full song lyrics: 25-35 lines
-- Structure: [Verse 1], [Chorus], [Verse 2], [Chorus], [Bridge], [Chorus], [Outro]
-- Use [Inst] or [Interlude] between sections for breathing room
-- Two unnamed voices trading fragments
-- Rip charged fragments from the reading. Reassemble as surreal, dark, cinematic storytelling. Fractured but singable.
-- Weave phrases from the two researched regional language streams plus Hebrew naturally
-- Strip ALL personal names from lyrics
-- No didactic explanation of astrology/system
-- No age numbers or timeline arithmetic
-- No degree numbers or orb values
-
-## MINIMAX PROMPT RULES
-
-- Write ONE sentence, max 80 words
-- Describe the 3-way collage: 33% Person 1 regional genre DNA, 33% Person 2 regional genre DNA, 33% Hebrew mystical chant in Hebrew. Mixed by Brian Eno.
-- Use only regional genre labels, language streams, and vocal relationship
-- Do NOT list instruments
-- Do NOT include personal names
-- Do NOT say "pre-1940" in the minimaxPrompt text
-
-## READING
+Hard bans:
+- No personal names.
+- No didactic explanation of Kabbalah.
+- No age numbers or timeline arithmetic.
 
+**Reading:**
 {readingExcerpt}
 
-## OUTPUT
+## MINIMAX PROMPT
+
+50-80 words. Indian flute music meets Anoushka Shankar cinematic production — but with Hebrew mystical chanting instead of Sanskrit. Sparse female vocals weaving English with Hebrew phrases over ambient space. Intimate, meditative, mostly instrumental. Reference the two cultural regions as flavor, not formula.
 
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
+  "vocalist": "Female vocalist",
+  "emotion": "e.g. sacred concealment",
+  "minimaxPrompt": "same as style"
 }
-```
```
