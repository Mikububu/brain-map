---
title: "06-mar-31-remove-cutup"
type: archive
date: 2026-03-31
commit: b149faa6
---

# gene keys: remove rip/reassemble instruction

Commit `b149faa6` (2026-03-31). Full diff filtered to Gene Keys files only.

```diff
commit b149faa61760c2d87e75609a7c1f1db7ba8bffc5
Author: Michael <michael@forbidden-yoga.com>
Date:   Tue Mar 31 00:20:20 2026 +0400

    gene keys: remove rip/reassemble instruction

diff --git a/1-in-a-billion-v2/backend/prompts/music/gene-keys-music-prompt.md b/1-in-a-billion-v2/backend/prompts/music/gene-keys-music-prompt.md
index 59d39f58..c01bf58f 100644
--- a/1-in-a-billion-v2/backend/prompts/music/gene-keys-music-prompt.md
+++ b/1-in-a-billion-v2/backend/prompts/music/gene-keys-music-prompt.md
@@ -7,7 +7,7 @@ Read this Gene Keys reading and write a full song.
 
 Write full song lyrics. 25-35 lines. Verse, chorus, verse, chorus, bridge, chorus, outro.
 
-Rip the most charged fragments from the reading below. Reassemble into surreal, dark, cinematic storytelling. Fractured but singable. The song arc should mirror shadow → gift → siddhi.
+The song arc should mirror shadow → gift → siddhi.
 
 No system language. No Gene Keys terminology. Only the raw human transformation underneath.
 
```
