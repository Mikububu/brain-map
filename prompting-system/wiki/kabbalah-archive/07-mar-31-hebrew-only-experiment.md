---
title: "07 - Hebrew-only music experiment (Mar 31)"
type: archive
date: 2026-03-31
commit: 25da3795
---

# Hebrew-only music experiment (failed)

Commit `25da3795`. A short-lived experiment to make Kabbalah music Hebrew-only. Failed singability.

```diff
commit 25da379537f1d15c046d3d402b9511bf110de4ad
Author: Michael <michael@forbidden-yoga.com>
Date:   Tue Mar 31 00:05:53 2026 +0400

    kabbalah individual: Hebrew only, no English

diff --git a/1-in-a-billion-v2/backend/prompts/music/kabbalah-music-prompt.md b/1-in-a-billion-v2/backend/prompts/music/kabbalah-music-prompt.md
index 5cf15ec2..3fd397f1 100644
--- a/1-in-a-billion-v2/backend/prompts/music/kabbalah-music-prompt.md
+++ b/1-in-a-billion-v2/backend/prompts/music/kabbalah-music-prompt.md
@@ -12,7 +12,7 @@ Rip the most charged fragments from the reading below. Reassemble into surreal,
 Use only known Kabbalistic terms as raw texture: "ein sof", "tikkun", "the vessels shatter", "klipot", "Gevurah", "Binah", "Yesod", "the tree of life".
 
 Language behavior:
-- Weave English with selective Hebrew mystical fragments.
+- Sing in Hebrew only. No English.
 - Repetition should feel like invocation, not explanation.
 
 Hard bans:
@@ -26,7 +26,7 @@ Hard bans:
 ## MINIMAX PROMPT
 
 50-80 words. Keep the blend strict: 50% modern cinematic pop production, 50% Hebrew mystical chanting.
-Vocalist weaves English with Hebrew phrases. Overall result must feel pop and hook-driven.
+Female vocalist singing in Hebrew only. Overall result must feel pop and hook-driven.
 Do not list instruments. Use only concise style/mood language.
 
 ## OUTPUT (JSON only)
@@ -38,5 +38,5 @@ Do not list instruments. Use only concise style/mood language.
   "musicStyle": "short label",
   "vocalist": "Female vocalist",
   "emotion": "e.g. sacred rupture",
-  "minimaxPrompt": "50% modern cinematic pop, 50% Hebrew mystical chant; female vocal in English and Hebrew, intimate, hook-driven, melancholic, sacred."
+  "minimaxPrompt": "50% modern cinematic pop, 50% Hebrew mystical chant; female vocal in Hebrew only, intimate, hook-driven, melancholic, sacred, devotional."
 }
```
