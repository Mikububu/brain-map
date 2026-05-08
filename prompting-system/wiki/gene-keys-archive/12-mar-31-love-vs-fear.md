---
title: 12-mar-31-love-vs-fear
type: archive
date: 2026-03-31
commit: 620246ac
---

# gene keys synastry: love vs fear of love, random artist selection

Commit `620246ac` (2026-03-31). Full diff filtered to Gene Keys files only.

```diff
commit 620246ac5d6393510294062ad4092e3160150288
Author: Michael <michael@forbidden-yoga.com>
Date:   Tue Mar 31 00:30:34 2026 +0400

    gene keys synastry: love vs fear of love, random artist selection

diff --git a/1-in-a-billion-v2/backend/prompts/music/gene-keys-overlay-music-prompt.md b/1-in-a-billion-v2/backend/prompts/music/gene-keys-overlay-music-prompt.md
index 76872e16..09de68da 100644
--- a/1-in-a-billion-v2/backend/prompts/music/gene-keys-overlay-music-prompt.md
+++ b/1-in-a-billion-v2/backend/prompts/music/gene-keys-overlay-music-prompt.md
@@ -1,8 +1,5 @@
 # Gene Keys — Synastry Music Prompt
 
-You are a surrealist songwriter using David Bowie's cut-up method.
-Read this Gene Keys synastry reading about two people and write a full song.
-
 ## LYRICS
 
 Write sparse song lyrics. 15-20 lines of voice, maximum. The rest is instrumental space.
@@ -11,17 +8,25 @@ Structure: [Inst], [Verse 1], [Inst], [Chorus], [Inst], [Verse 2], [Chorus], [In
 
 More music than voice. The song arc should mirror shadow → gift → siddhi.
 
-Person A sings their drama, Person B sings theirs — they trade accusations, direct, raw, naming each other's patterns.
+Person A sings their love, Person B sings fears of love — they trade romance and desire, direct, raw, naming each other's patterns.
 
-Hard bans:
-- No personal names.
+No personal names.
 
 **Reading:**
 {readingExcerpt}
 
 ## MINIMAX PROMPT
 
-50-80 words. Modern, intimate, emotionally resonant. Adapt to what you feel in the reading. Do not list instruments. Use only concise style/mood language.
+Randomly select ONE of the following artists as musical inspiration:
+
+- Bon Iver — For Emma era
+- FKA Twigs — Magdalene era
+- Sigur Rós — Takk era
+- James Blake — Overgrown era
+- Sevdaliza — Shabrang era
+- Thom Yorke — Anima era
+
+50-80 words. Write the prompt so MiniMax creates a song that sounds like the selected artist. Adapt to what you feel in the reading.
 
 ## OUTPUT (JSON only)
 
@@ -30,7 +35,7 @@ Hard bans:
   "title": "2-5 Words",
   "style": "same as minimaxPrompt",
   "musicStyle": "short label",
-  "vocalist": "Female and male duet",
+  "vocalist": "Female and male duet, matching selected artist",
   "emotion": "e.g. shadow communion",
   "minimaxPrompt": "same as style"
 }
```
