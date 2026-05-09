---
title: "08-mar-31-add-cultural"
type: archive
date: 2026-03-31
commit: 77f9e6e5
---

# gene keys synastry: add cultural birthplace + language inputs

Commit `77f9e6e5` (2026-03-31). Full diff filtered to Gene Keys files only.

```diff
commit 77f9e6e557ee763a80ba091d0a11971a369de062
Author: Michael <michael@forbidden-yoga.com>
Date:   Tue Mar 31 00:22:24 2026 +0400

    gene keys synastry: add cultural birthplace + language inputs

diff --git a/1-in-a-billion-v2/backend/prompts/music/gene-keys-overlay-music-prompt.md b/1-in-a-billion-v2/backend/prompts/music/gene-keys-overlay-music-prompt.md
index 76872e16..2ca78f47 100644
--- a/1-in-a-billion-v2/backend/prompts/music/gene-keys-overlay-music-prompt.md
+++ b/1-in-a-billion-v2/backend/prompts/music/gene-keys-overlay-music-prompt.md
@@ -3,6 +3,13 @@
 You are a surrealist songwriter using David Bowie's cut-up method.
 Read this Gene Keys synastry reading about two people and write a full song.
 
+## CULTURAL INPUTS
+
+- **Person 1** from {person1BirthPlace} — languages: {person1Languages}
+- **Person 2** from {person2BirthPlace} — languages: {person2Languages}
+
+Research each birthplace. What music lives in that soil? Folk, sacred, court, street. Use that cultural DNA as texture in the lyrics and in the MiniMax prompt.
+
 ## LYRICS
 
 Write sparse song lyrics. 15-20 lines of voice, maximum. The rest is instrumental space.
```
