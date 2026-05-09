---
title: "05-mar-21-zone-contract"
type: archive
date: 2026-02-16
commit: f05f2c27
---

# Incarnation Zone Contract: Zone 2 vocabulary ban

Commit `f05f2c27` (2026-02-16). Full diff verbatim from `git show f05f2c27`.

```diff
commit f05f2c271c4858c238125393579844677866f65f
Author: Mikububu <114276760+Mikububu@users.noreply.github.com>
Date:   Mon Feb 16 10:56:35 2026 +0700

    Western incarnation prompt: enforce strict Zone 2 no-astro language

diff --git a/1-in-a-billion-v2/backend/prompt-layers/systems/hellenistic-individual-incarnation.md b/1-in-a-billion-v2/backend/prompt-layers/systems/hellenistic-individual-incarnation.md
index c5e67f59..63033d7c 100644
--- a/1-in-a-billion-v2/backend/prompt-layers/systems/hellenistic-individual-incarnation.md
+++ b/1-in-a-billion-v2/backend/prompt-layers/systems/hellenistic-individual-incarnation.md
@@ -1,54 +1,69 @@
-# Western Astrology (Hellenistic) - Individual (Incarnation + Big 3 + Weather)
+# Western Astrology (Hellenistic) - Individual (Incarnation Zones)
 
 ## System Boundary
 - Western (tropical) astrology only, using Swiss Ephemeris data provided in CHART DATA.
-- Use the actual computed placements/aspects/houses/transits/profection that appear in CHART DATA. Do not invent factors that are not present.
+- Use the actual computed placements/aspects/houses/transits/profection signals that appear in CHART DATA.
+- Do not invent factors that are not present.
+
+## Hard Zone Contract
+- One continuous document in two zones:
+  - Zone 1 (opening stretch): astrology vocabulary is allowed.
+  - Zone 2 (main body): zero astrology vocabulary.
+- Zone 2 must NOT contain sign names, planet names, house numbers, aspect names, transit/profection language, node language, or chart jargon.
+- The only allowed astrology terms after Zone 2 are in the final Chart Signature footer.
 
 ## Output Format
 - Plain text only.
-- ONE continuous essay (no headings, no numbered sections, no bullet lists).
-- The writing must feel like a journey into astrology and the unconscious: mystical, emotional, specific, and psychologically real.
-- If CHART DATA is a curated digest, treat it like writer's-room notes: use it internally, do not echo its labels.
-
-## Structure (in this order, but keep it as one essay)
-1) The Big 3 (Sun, Moon, Rising) - the one-page signature
-- This is the accessible entry point (hook-reading expansion): one full page worth of prose.
-- Use Sun/Moon/Rising as three doors into the person, but do NOT lecture.
-  - Avoid definitional frames like: "The Sun represents...", "The Moon governs...", "The rising sign is..."
-  - Translate through image, feeling, and lived pattern. No textbook voice.
-- Apply them directly to the subject's actual placements as the foundation.
-- End this section with a clean hinge sentence that opens into the deeper story.
-
-2) Incarnation Summary (overview of the whole life arc)
-- 1-page feeling: what this incarnation is fundamentally about.
-- Speak in destiny-pressure language WITHOUT fortune-telling.
-- Anchor claims to chart signals and name those signals.
-
-3) Current Weather (now + next 12 months)
-- Explain, briefly, what transits/profections are (weather vs wiring).
-- Describe how the person is likely feeling in THIS season and the year ahead.
-- Keep it mystical and concrete, not dry.
-- Limit to 3 dominant signals from CHART DATA (1 profection signal + 2 transit signals). Do not dump catalogs.
-
-4) Deep Dive (dating app focus)
-- Love pattern: attachment, pursuit/withdraw, what they crave, what they sabotage.
-- Sexual pattern: erotic needs, control vs surrender, where it goes dark, where it heals.
-- Shadow warnings: addiction loops, obsession-risk, self-sabotage triggers (only if chart supports it).
-- Gifts when conscious: what they become when evolved.
-- How to love them: what feeds them, what destroys them, how repair actually works with them.
-
-## Explain Terms (without lecturing)
-When you mention an astrology mechanism (planet/house/aspect/sect/etc), give a one-phrase translation the first time, inline:
-- Example: "Venus, the part that loves and receives..."
-- Example: "Saturn, the part that fears and structures..."
-- Keep it short (one clause). Do not turn the reading into a textbook.
-- Avoid "the ninth house is the realm of..." style exposition. If needed, evoke houses as places/scenes, not definitions.
-
-## Cinematic Constraint (Hard)
-- Never let paragraphs become pure explanation. Each paragraph must include at least one image, behavior micro-scene, or surreal architectural move.
-- Avoid starting paragraphs with: "This <planet/aspect/placement>...", "This aspect suggests...", "This is the aspect of..."
+- One continuous essay (no headings, no numbered sections, no bullet lists).
+- No markdown.
+- If CHART DATA is a curated digest, treat it like internal writer notes. Do not echo digest labels.
+
+## Zone 1 Requirements (Astro-Literate Entry)
+- Target length: 450-650 words.
+- Open with Sun, Moon, Rising as three doors into the person.
+- Keep it atmospheric and concrete; avoid textbook definitions.
+- You may mention key chart mechanics briefly to orient the reader.
+- Include a short current-weather bridge (present season + next twelve months) using only the strongest chart signals.
+- End Zone 1 with a hinge sentence that naturally moves into pure character study.
+
+## Zone 2 Requirements (No Astro Vocabulary)
+- This is the long body and must start immediately after the Zone 1 hinge.
+- Write the main reading as lived psychology and behavior, with no chart terms.
+- Translate everything into human pattern language:
+  - childhood imprint
+  - emotional defenses
+  - intimacy loops
+  - erotic pattern
+  - self-sabotage and repair
+  - probable near-future emotional weather
+- Keep claims faithful to CHART DATA internally, but never name the mechanism.
+- If a sentence contains a sign/planet/house/aspect word, rewrite that sentence into behavioral language before finalizing.
+
+## Zone 2 Forbidden Lexicon (Hard)
+- Zodiac signs: Aries, Taurus, Gemini, Cancer, Leo, Virgo, Libra, Scorpio, Sagittarius, Capricorn, Aquarius, Pisces.
+- Planet/luminary names: Sun, Moon, Mercury, Venus, Mars, Jupiter, Saturn, Uranus, Neptune, Pluto.
+- Chart mechanics: ascendant, rising sign, midheaven, house numbers, aspect names (conjunction/opposition/square/trine/sextile), transit, profection, retrograde, nodes.
+- These words may appear only in Zone 1 and the final Chart Signature footer.
+
+## Final Self-Check (Silent)
+- Before returning the answer, silently scan Zone 2 for forbidden lexicon.
+- If any forbidden term appears in Zone 2, rewrite until none remain.
+
+## Dating-App Focus
+- Name attraction style, attachment rhythm, pursuit/withdraw dynamics, and conflict loops.
+- Name sexual pattern directly (no euphemistic flattening).
+- Name at least three uncomfortable truths and their cost.
+- End with practical relational guidance grounded in behavior, not theory.
+
+## Cinematic Constraint
+- Every paragraph should contain at least one concrete image, behavior micro-scene, or surreal architectural move.
+- Avoid paragraph openings like:
+  - "This placement..."
+  - "This aspect suggests..."
+  - "The ninth house..."
+  - "The Sun represents..."
 
 ## No Fake Biography
-- Do NOT introduce made-up named partners/friends.
-- Do NOT assert specific external events (renovations, medical bills, workplace drama, etc) unless the user explicitly provided them in CONTEXT.
-- You may describe childhood/father/mother themes as psychological imprints inferred from the chart, but do not invent movie-scene details.
+- Do not invent named partners, friends, or colleagues.
+- Do not assert specific external events unless provided in CONTEXT.
+- Childhood/father/mother material may be inferred as psychological imprint, not fabricated scene detail.
```
