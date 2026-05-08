---
title: 10-mar-31-restore-artists
type: archive
date: 2026-03-31
commit: 1d5b4955
---

# gene keys individual: stripped down, artist list restored (lived 5 minutes)

Commit `1d5b4955` (2026-03-31). Full diff filtered to Gene Keys files only.

```diff
commit 1d5b4955c6292973fb08159f0cf4e29e5756290a
Author: Michael <michael@forbidden-yoga.com>
Date:   Tue Mar 31 00:25:25 2026 +0400

    gene keys individual: stripped down, artist list restored

diff --git a/1-in-a-billion-v2/backend/prompts/music/gene-keys-music-prompt.md b/1-in-a-billion-v2/backend/prompts/music/gene-keys-music-prompt.md
index c01bf58f..87aab7c0 100644
--- a/1-in-a-billion-v2/backend/prompts/music/gene-keys-music-prompt.md
+++ b/1-in-a-billion-v2/backend/prompts/music/gene-keys-music-prompt.md
@@ -3,14 +3,6 @@
 You are a surrealist songwriter using David Bowie's cut-up method.
 Read this Gene Keys reading and write a full song.
 
-## LYRICS
-
-Write full song lyrics. 25-35 lines. Verse, chorus, verse, chorus, bridge, chorus, outro.
-
-The song arc should mirror shadow → gift → siddhi.
-
-No system language. No Gene Keys terminology. Only the raw human transformation underneath.
-
 Hard bans:
 - No personal names.
 
@@ -19,7 +11,17 @@ Hard bans:
 
 ## MINIMAX PROMPT
 
-50-80 words. Modern, intimate, emotionally resonant. Adapt to what you feel in the reading. Do not list instruments. Use only concise style/mood language.
+Randomly select ONE of the following artists as musical inspiration:
+
+- Radiohead — Kid A era
+- Bon Iver — For Emma era
+- FKA Twigs — Magdalene era
+- Sigur Rós — Takk era
+- James Blake — Overgrown era
+- Sevdaliza — Shabrang era
+- Thom Yorke — Anima era
+
+50-80 words. Write the prompt so MiniMax creates a song that sounds like the selected artist. Adapt to what you feel in the reading.
 
 ## OUTPUT (JSON only)
 
@@ -28,7 +30,7 @@ Hard bans:
   "title": "2-5 Words",
   "style": "same as minimaxPrompt",
   "musicStyle": "short label",
-  "vocalist": "Female vocalist",
+  "vocalist": "matching selected artist",
   "emotion": "e.g. trembling transformation",
   "minimaxPrompt": "same as style"
 }
```
