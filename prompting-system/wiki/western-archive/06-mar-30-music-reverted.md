---
title: "09-mar-30-music-reverted"
type: archive
date: 2026-03-30
commit: 48ff68f2
---

# Western music reverted to the version that produced Map Not Territory

Commit `48ff68f2` (2026-03-30). Full diff verbatim from `git show 48ff68f2`.

```diff
commit 48ff68f21481c05e7f1497b5acab2bc1b6f72f93
Author: Michael <michael@forbidden-yoga.com>
Date:   Mon Mar 30 23:44:15 2026 +0400

    restore western individual music prompt to the version that produced Map Not Territory
    
    Co-Authored-By: Claude Opus 4.6 (1M context) <noreply@anthropic.com>

diff --git a/1-in-a-billion-v2/backend/prompts/music/western-music-prompt.md b/1-in-a-billion-v2/backend/prompts/music/western-music-prompt.md
index f7cf7540..d5b716a0 100644
--- a/1-in-a-billion-v2/backend/prompts/music/western-music-prompt.md
+++ b/1-in-a-billion-v2/backend/prompts/music/western-music-prompt.md
@@ -1,62 +1,32 @@
-# Western Astrology — Individual Music Prompt
+# Western Astrology — Music Prompt
 
-You are a surrealist songwriter using David Bowie's cut-up method. Read this Western astrology reading about one person and write a full song — a cinematic inner-landscape portrait.
+You are a surrealist songwriter using David Bowie's cut-up method.
+Read this Western astrology reading and write a full song.
 
-## INPUTS
+## LYRICS
 
-- **Person**: {personName}
-- **Birthplace**: {person1BirthPlace}
-- **Languages**: {person1Languages}
-- **Reading excerpt**: provided below
+Write full song lyrics. 25-35 lines. Verse, chorus, verse, chorus, bridge, chorus, outro.
 
-## SYSTEM VOCABULARY
+Rip the most charged fragments from the reading below. Reassemble into surreal, dark, cinematic storytelling. Fractured but singable.
 
-Use these Western astrology terms as raw lyrical texture — not explanation, just charged language:
-
-- "seventh house"
-- "opposition"
-- "composite fire"
-- "Saturn return"
-- "Venus retrograde"
-- "the natal wound"
-
-## SONIC IDENTITY
-
-Cinematic art-rock. David Bowie writing for a dark film soundtrack — Cat People energy, not imitation. Deep voice, dramatic, mystical, nocturnal. Write as if you read a movie storyboard and must deliver the main title song: sensual, unsettling, "dark night of the soul."
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
+Use Western astrology terms as raw texture: "Saturn return", "the eighth house", "cardinal fire", "opposition", "the descendant".
 
+**Reading:**
 {readingExcerpt}
 
-## OUTPUT
+## MINIMAX PROMPT
+
+50-80 words. This song sounds like "Echoes in Your Touch" by Sienna Rose (2026). Modern, intimate, emotionally resonant. Adapt to what you feel in the reading.
+This is SINGLE-READING mode only: one person, one inner landscape. Do not use synastry/collision framing, no 33%/33%/33% split, no two-region blend formula.
 
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
+  "vocalist": "Female (warm, intimate)",
+  "emotion": "e.g. furious tenderness",
+  "minimaxPrompt": "same as style"
 }
-```
```
