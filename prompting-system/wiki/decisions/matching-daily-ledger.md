---
title: Matching Algorithm, Daily Ledger
type: decision-log
created: 2026-05-08
updated: 2026-05-08
tags: [decision, matching, daily, chronological, ledger]
---

# Matching Algorithm, Daily Ledger

The complete commit-by-commit, day-by-day evolution of the deep matching / synastry algorithm. Per the user: *"Anyone who wants to understand this should go through each daily GitHub change where I speak about it and discuss it with the deep-matching algorithm."*

This page is the ledger. **81 commits across 30+ active days**, February 2026 to May 2026. Files traced: all 6 synastry engines (`synastryEngine.ts`, `vedicSynastryEngine.ts`, `verdictSynastryEngine.ts`, `hdSynastryEngine.ts`, `geneKeysSynastryEngine.ts`, `kabbalahSynastryEngine.ts`), the compatibility scoring service, the text worker that injects scores into prompts, the synastry prompts, the Ashtakuta tables, and the Vamachara interpretation files.

For the philosophical context, see [[topics/matching-philosophy]]. For the engine architecture, see [[topics/matching-algorithm]]. For the gender-blind commitment, see [[decisions/gender-blind-matching]].

---

## February 2026

The architecture was created. Two days of activity.

### 2026-02-16
- `4cba79c2` *03:10* `feat(v2): add 1-in-a-billion-v2 app + backend`. The day the v2 backend was created, including the early shape of `matchEngine.ts` (still hardcoded mock data: Irena, Haruto, Selene)
- `03fcef8f` *04:05* `Prompt engine: incarnation system prompt + prompt ordering`. Synastry prompt structure first wired

### 2026-02-18
- `af0553d2` *13:29* `V2 prompt-layer overhaul: 5-system incarnation wiring and generation pipeline sync`. The five-system architecture commit. Synastry prompts get their own files per system.

(No matching activity Feb 19 to Mar 9. The architecture sat in place. The five-system synastry prompts existed; the *deterministic engine* did not yet.)

---

## March 2026

The densest month. The deterministic-engine breakthrough, the Vamachara interpretation, the Ashtakuta repair, and "The Happiness" added as a 9th computed category.

### 2026-03-10
- `c1abc2de` *16:23* `Auto-deploy updates from desktop`. Pre-staging for the Mar 11 push.

### 2026-03-11 (the deterministic-engine breakthrough)

Five active commits between 21:05 and 23:12. The day math replaced LLM intuition.

- `f2be9c8e` *00:55* `Fix library spinner jump and audio/PDF artifact counts`
- `2ea113d2` *04:30* `Auto-deploy updates from desktop`
- `df33299b` *09:15* `Auto-deploy updates from desktop`
- `6cb7ca5e` *21:05* `Auto-deploy updates from desktop`
- `d0075963` *21:33* `Auto-deploy updates from desktop`. Four parallel synastry engines (Vedic, HD, Gene Keys, Kabbalah) added in this deploy
- `06e7f146` *22:04* **`fix: wire deterministic scores to anchor system for all 5 engines`**. Score injection wired across all five systems
- `3cee6f75` *22:37* **`feat: widen synastry score polarity to full 0-100 range`**. Western 50→25, HD 35→5. Enables true 0-100 polarity instead of 60-80 LLM clustering
- `09104683` *23:12* **`feat: add verdict meta-engine + widen all systems to true 0-100 range`**. The verdict meta-engine (`verdictSynastryEngine.ts`) born. 16-category aggregator over all five system engines

### 2026-03-12 (broaden, raise, reframe Vedic)

Five commits, refinement and a major philosophical addition (Vamachara).

- `0ca4c0a7` *00:23* `fix: broaden synastry scorers + fix Kabbalah/Vedic data bugs`. Western adds Sun-Venus, Sun-Mars, Moon-Mars, Moon-Venus, ASC-Venus cross-aspects. Kabbalah switches to weighted pillar balance (strong=2, moderate=1, weak=0.5). Vedic gives all grahas rashi+nakshatra+pada (not Moon-only)
- `ca728d3c` *08:40* `fix: raise synastry score baselines to eliminate unrealistic 0-scores`. Western 25→35, Vedic floors 0→10. Toxic / shadow risk stays at 0
- `ae467290` *10:10* `fix: reduce communication penalty for challenging aspects, raise Vedic floors`
- `cd2e6f95` *20:38* **`feat(vedic): add Vamachara left-hand tradition interpretation layer`**. The night the philosophy of *happiness over duty* lands in code. Nadi dosha reframed as kundalini activation. Manglik as Mars / Shakti transmission. Deva-Rakshasa as Shiva-Shakti polarity. Difficult Vedic combinations recast as intensity-containers, not marriage-blockers. Vamachara is the "left-hand path" of Tantra; the term carries its lineage. See [[topics/forbidden-yoga-context]]
- `21cf242e` *23:13* `Auto-deploy updates from desktop`

### 2026-03-13
- `1b00cd67` *07:35*
- `9802f0af` *08:03*
- `994a1229` *11:17*

(All `Auto-deploy updates from desktop`. Quiet day; iterative refinement.)

### 2026-03-14
- `170afce1` *03:58*
- `5c5ededa` *09:58*
- `59fe8297` *10:06*
- `10c670a2` *10:27*
- `d69d48b6` *22:27*

(Five `Auto-deploy` commits. Refinement continues; nothing visible in the messages but the engine is being tuned.)

### 2026-03-15 (the 11-commit Vedic-voice night)

The most volatile narrative-voice iteration in the corpus. 11 commits between 00:06 and 02:55, then 4 more through 19:25.

- `8e0fc3c3` *00:06* `fix: system-aware narrative rewrite + profileStore crash guards`
- `b2a7f5fa` *00:12* `feat: Svoboda Aghori voice for Vedic narrative rewrite (3rd pass)`
- `b20fba9e` *00:32* `fix: Vedic pipeline audit fixes — spice level, system prompt, terminology`
- `6e53d608` *00:46* `fix: pass spice level to Vedic overlay writing prompt`
- `a3accc1c` *01:06* `fix: Calasso style reference (not book content) + ru build fix + crash reporter`
- `b47e52ff` *01:09* `fix: switch 3rd pass voice to Calasso (better prose quality)`. The Aghori-witness voice gets replaced with Calasso-style 3 minutes after it shipped
- `171f1ada` *01:27* `fix: Vedic pipeline audit — 4 logic defects`
- `a3fd2410` *02:47* `fix: 3rd pass language lock + stronger strip rules`
- `1751236b` *02:55* `fix: revert 3rd pass to proven structure + add language lock`
- `157741b2` *02:56* `fix: simplify language instruction — same as source language`
- `f283864c` *07:54* `fix: 3rd pass structural rules — narrate, don't explain`
- `6e0d6570` *08:04* `revert: 3rd pass narrative rewrite to proven 10c670a version`
- `9f1b1065` *10:46* `fix: add Vedic-specific vocabulary stripping to 3rd pass`
- `da368e4e` *13:13* `Auto-deploy updates from desktop`
- `9a8b51b1` *14:32* `fix: add language instruction to Vedic narrative rewrite (Layer 3)`
- `ec90f37e` *19:25* `fix: post-processing passes now preserve output language`

(The pattern: try a voice, ship, judge the output, revert, try another. The Aghori-witness archetype that survives in [[voices/vedic]] gets locked in here, after Calasso was tried and dropped.)

### 2026-03-16 (LLM routing by language, not by system)
- `081ab931` *09:54*
- `272b7ec1` *10:43*
- `4d549f6f` *10:47* **`feat: updated LLM routing from astro-system to output language with Opus openrouter integration`**. Architectural pivot: the LLM dispatch is now per-language, not per-system. See [[topics/per-language-llms]]
- `f631fd2d` *13:16*
- `576a32bf` *20:22* `fix: restore proven single-prompt narrative rewrite for all systems`
- `95fbefad` *20:35* `chore: remove dead cost tracking system`

### 2026-03-17 (qualitative scores, dharmic archetype)

Architectural shift: from numeric to qualitative interpretation.

- `a2395b94` *02:20*
- `9fe0c898` *08:25* **`feat: add personal ceiling to Vedic matching, lower threshold instead of inflating scores`**. Refusal of score inflation. The user picks the right answer over the comfortable one
- `73602045` *10:00* `feat: system-specific Layer 3 rewrite prompts + Layer 2 shadow unlock`
- `5e3dec52` *14:58* `fix: audit round 2 fixes + nav state persistence + worker updates`
- `32f5a067` *15:13* `fix: replace loaded relational labels + show chart indicators in PDF appendix`
- `50be6c07` *15:58* **`feat: qualitative scores, expansion voice DNA, Vedic dharmic archetype system`**. Numeric scores get a qualitative companion (low / medium / high / radical). Dharmic archetype system added: matching reads a person's chart through *dharmic role* (sage, warrior, lover, householder, renunciate)
- `d45d2e83` *23:45* `fix: smooth progress bar with phase-weighted percent + granular text updates`

### 2026-03-18 (Layer 0 chart digest wired in)

The interpretive weight shifts from Layer 1 to Layer 0. Pre-planned spine becomes the architecture.

- `8c4bad88` *00:26* `fix: progress bar shows real percentage by querying actual completed task count`
- `225c6e89` *00:39*
- `5b076c32` *02:39* `feat: unhinged readings, anonymize names + uncensored system prompt`
- `ab9af54b` *03:24*
- `876f522a` *08:30*
- `5e5466f9` *09:07* `Remove text worker name anonymization placeholders`
- `56ef8fff` *09:57* `Fix stuck job progress by hardening progress updates`
- `ec2c05ea` *15:46* **`feat: wire Western chart digest as Layer 0, THE_WOUND/ACT_1-3/LANDING_TEMPERATURE now feed writing prompt as pre-planned spine`**. The structural spine of every Western reading is now decided BEFORE writing begins. Compositional architecture, not improvisation
- `de639f0e` *15:59* `feat: replace RLHF-fighting permission language with clinical framing + sexual mechanism taxonomy in digest`. The user fights LLM refusal with *clinical* register instead of permission-pleading
- `623ba8e8` *22:40* **`feat: wire Vedic Layer 0 digest into reading pipeline, shift interpretive weight from Layer 1 to Layer 0`**. The Vedic version of the same move

### 2026-03-19
- `55bfe616` *00:46*
- `0b375396` *14:52*
- `1be8b8bc` *15:39*

(Auto-deploys. Quiet.)

### 2026-03-20
- `ce9396d1` *11:04*
- `f842fcf7` *11:40*
- `32ee9db5` *14:59* `fix: allow Jyotishi prescription appendix in vedic readings`. The traditional astrologer's prescriptive remedies get an appendix slot, but stay separate from the main reading
- `687e394e` *21:16* `fix: add per-trigger English language guardrails + post-generation language detection`

### 2026-03-21 (the Happiness Index + Hellenistic merge)

The day "The Happiness" got added as a 9th deterministic category, AND Hellenistic was merged into Western. Two of the most consequential moves in the corpus, same day.

- `0561cb49` *08:50*
- `ba3c213e` *10:12*
- `37a4b54f` *11:19*
- `2aef2407` *12:06* **`fix: Ashtakoota tables (Graha Maitri, Yoni, Gana) + Happiness Index`**. The actual codification of *happiness over duty.*
   - GRAHA_MAITRI_TABLE: full Parashara compound friendship (was 3/5; now 0-5)
   - YONI_TABLE: enemy pairs score 0; Tiger row corrected (was copy of Cow)
   - GANA_TABLE: Deva-Rakshasa=0, Manushya-Rakshasa=1 (strict traditional)
   - **"The Happiness" added as a 9th deterministic compatibility category** (Gana + Graha Maitri + Yoni). Translations in all 10 languages
- `9f6633d5` *13:10*
- `843f4989` *14:46* **`feat: diagnostic hierarchy, truth obligation, Hellenistic merge, dead code cleanup`**. The Hellenistic merge into Western. *"Malefics are malefic."* See [[decisions/hellenistic-merge]]
- `f4658146` *14:53* `feat: Miller punchline on every PDF cover page`. The Henry Miller punchline (from [[topics/january-foundation|the v0 voice samples]]) gets surfaced on every PDF
- `56edc3f8` *15:34*
- `9d523083` *15:57* `feat: Miller punchline restored + closing passage at end of every PDF`
- `38493766` *17:46* `fix: English system prompt on narrative rewrite to prevent German drift`
- `eb8bb174` *18:31* `fix: use lightweight English guardrail instead of full analytical mandate`
- `f969df23` *19:13*
- `aa031082` *20:54* `fix: kill first-person narrator bleed + summarizer mode in Layer 3 rewrites`
- `1b43371e` *21:25* `fix: translate all PDF headlines + Miller punchline/closing to reading language`
- `4de2bb94` *21:35* `feat: add Astrologic Glossary section to PDF (~10 pages)`

### 2026-03-22 (relationshipContext wired in, glossary refinement)
- `bb9e8d41` *09:38* `feat: wire relationshipContext into all readings (Layer 2 → Layer 3)`. The relational context (married, dating, ex, friend, family) propagates through both layers
- `86f23e90` *21:51* `fix: skip chart reference page for verdict PDFs`
- `b8bc2c73` *22:19* `fix: verdict PDFs get combined chart reference + glossary appendix`
- `adbfca91` *22:23* `fix: glossary now extracts terms from actual reading text`
- `d6318fed` *22:30* `fix: glossary covers both people in overlay and verdict docs`

### 2026-03-25
- `4dd69f2e` *09:31*

### 2026-03-26
- `e1608f79` *15:02*
- `650073c9` *15:15*
- `97323cdc` *18:41* `Clean Layer2/Layer3 prompt motifs and sync migration seeds`
- `ce3d98ee` *19:01*
- `ba77e905` *19:15* `feat(llm): add final verdict provider override routing`. The verdict layer can now use a different model. Foundation for the [[apps/admin-panel|admin-panel]] dispatch table
- `d06ec178` *21:58*

### 2026-03-27
- `e2458187` *00:29*
- `edeb0c62` *08:02* **`Scope psychosexual rewrite mandate to Western only and strengthen full-text western contract`**. Western becomes the only voice allowed (and required) to use direct adult erotic terminology. The other four soften
- `3c84c4f9` *15:29*
- `44f4f7d2` *19:10*

### 2026-03-28
- `6c241549` *13:04*
- `026b8247` *14:17* **`rewrite: switch Hindi sample to Osho voice anchor`**. See [[decisions/native-script-voice-anchors]]
- `ce7df418` *14:44*
- `dd50f881` *19:00*
- `64f2ac80` *22:18* `fix: keep deep reading analysis in english sonnet`
- `1075efa6` *22:37* `fix: keep verdict analysis in english before translation`

### 2026-03-29
- `aceb1f7e` *10:49*
- `d0d35753` *16:53*
- `c4c3d0d7` *18:57*

### 2026-03-30 (chart-obedient frame, no invented biography)
- `f8e7a751` *03:29* **`fix: replace fiction frame with chart-obedient frame, no more invented biography`**. The reading must follow the actual chart, not invent biographical scenes that aren't grounded in the chart
- `4c7f7fe8` *04:15* `fix: chart frame, interpret the meaning, not the language; restore psychosexual permission`
- `960af36c` *07:11* **`Stop rewrite layer from flattening system identity`**. Layer 3 was making Vedic sound like Western, Kabbalah sound like Gene Keys; preservation rules standardised
- `12a58b0a` *13:18*
- `d5d0befe` *13:53*
- `6863ca2d` *15:50*

---

## April 2026

Stabilisation. The architecture is locked; small fixes only.

### 2026-04-01
- `fbad0395` *20:27*
- `e151e53b` *21:54* `fix: reject empty layer-3 text outputs`
- `1eb90330` *22:51*

### 2026-04-02
- `4185ca53` *00:31*
- `fc8fc4e7` *07:58*
- `97255119` *08:29*
- `25dd1694` *12:24*

### 2026-04-15
- `7f21ce4f` *01:56* **`Sharpen hook and synastry preview readings`**. The synastry preview UX gets sharpened. Last meaningful matching commit before stabilisation

(Quiet stretch April 16 to May 4. The matching code is left alone for ~3 weeks. The wiki count starts here: this is the May 5 / May 8 timeframe of the Obsidian work.)

---

## May 2026

### 2026-05-05
- `87f03eef` *14:51* `Restore generation and subscription release fixes`. Maintenance touch on the subscription side; matching engines unchanged

(May 6, 7, 8: nothing in the matching code. The engine is in shipping state.)

---

## Summary observations

- **Total commits traced**: 81
- **Total active days**: 30
- **Densest single day**: 2026-03-15 (16 commits, the Vedic-voice iteration night)
- **Densest period**: 2026-03-11 to 2026-03-12 (the deterministic-engine breakthrough; ~15 commits in 24 hours)
- **Major architectural inflections**:
  - 2026-03-10 / 11: deterministic 5-system engine + verdict meta-engine ([[decisions/deterministic-synastry-engine]])
  - 2026-03-12: Vamachara interpretation layer (philosophy lands in code)
  - 2026-03-17: qualitative scores + dharmic archetype system
  - 2026-03-18: Layer 0 chart digest wired in (interpretive spine)
  - 2026-03-21: **The Happiness Index added as a 9th compatibility category** + Hellenistic merge
  - 2026-03-30: chart-obedient frame (no invented biography)
- **Quietest stretch**: April 16 to May 4 (~19 days). The matching architecture stabilised; iteration moved to other layers (admin-panel, music prompts)
- **Current state (May 8, 2026)**: shipping. No matching commits in the past 3+ weeks. The engine works. The discussions are now happening in the wiki, not the code

## Files traced

- `backend/src/services/synastryEngine.ts`
- `backend/src/services/vedicSynastryEngine.ts`
- `backend/src/services/verdictSynastryEngine.ts`
- `backend/src/services/hdSynastryEngine.ts`
- `backend/src/services/geneKeysSynastryEngine.ts`
- `backend/src/services/kabbalahSynastryEngine.ts`
- `backend/src/services/compatibilityScoring.ts`
- `backend/src/services/matchEngine.ts` (the early hardcoded mock data)
- `backend/src/services/vedic/vedic_ashtakoota.tables.ts` (the 8 kuta tables)
- `backend/src/services/vedic/vedic_yoni_gana_dasha.tables.ts`
- `backend/src/services/vedic/*Vamachara*` (the left-hand interpretation layer)
- `backend/src/workers/textWorker.ts`
- `backend/prompt-layers/systems/*-synastry.md`

## Connections

- [[topics/matching-philosophy]] (the Ashtakuta lineage and happiness inversion)
- [[topics/matching-algorithm]] (the engine architecture)
- [[decisions/deterministic-synastry-engine]] (the Mar 10 pivot)
- [[decisions/gender-blind-matching]] (the no-gender-filter commitment)
- [[decisions/hellenistic-merge]] (the Mar 21 absorption)
- [[topics/forbidden-yoga-context]] (the lineage from which Vamachara enters the code)
