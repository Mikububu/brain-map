---
title: "09-mar-31-remove-cultural"
type: archive
date: 2026-03-31
commit: 774a2212
---

# gene keys synastry: remove cultural inputs (lived 1 minute)

Commit `774a2212` (2026-03-31). Full diff filtered to Gene Keys files only.

```diff
commit 774a22127050dc9514863b902a1dc3858a54feb6
Author: Michael <michael@forbidden-yoga.com>
Date:   Tue Mar 31 00:23:16 2026 +0400

    gene keys synastry: remove cultural inputs

diff --git a/1-in-a-billion-v2/backend/prompts/music/gene-keys-overlay-music-prompt.md b/1-in-a-billion-v2/backend/prompts/music/gene-keys-overlay-music-prompt.md
index 2ca78f47..76872e16 100644
--- a/1-in-a-billion-v2/backend/prompts/music/gene-keys-overlay-music-prompt.md
+++ b/1-in-a-billion-v2/backend/prompts/music/gene-keys-overlay-music-prompt.md
@@ -3,13 +3,6 @@
 You are a surrealist songwriter using David Bowie's cut-up method.
 Read this Gene Keys synastry reading about two people and write a full song.
 
-## CULTURAL INPUTS
-
-- **Person 1** from {person1BirthPlace} — languages: {person1Languages}
-- **Person 2** from {person2BirthPlace} — languages: {person2Languages}
-
-Research each birthplace. What music lives in that soil? Folk, sacred, court, street. Use that cultural DNA as texture in the lyrics and in the MiniMax prompt.
-
 ## LYRICS
 
 Write sparse song lyrics. 15-20 lines of voice, maximum. The rest is instrumental space.
```
