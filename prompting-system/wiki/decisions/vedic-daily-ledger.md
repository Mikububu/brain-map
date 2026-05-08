---
title: Vedic, Daily Ledger
type: decision-log
created: 2026-05-08
updated: 2026-05-08
tags: [decision, vedic, daily, chronological, ledger]
---

# Vedic, Daily Ledger

Every commit touching anything Vedic in `1-in-a-billion-v2`, day by day, December 2025 to May 2026. **131 commits across 28 active days.** This is not a summary; this is the raw evolution.

For the synthesised view, see [[voices/vedic]] and [[topics/matching-philosophy]]. This page is the texture they sit on top of.

---

## February 2026

### 2026-02-16 (1 commit)
- `4cba79c2` *(03:10:28)* `feat(v2): add 1-in-a-billion-v2 app + backend`. Initial creation of the entire v2 application and backend, including `VEDIC_MATCHMAKING_SPEC.md` and all Vedic services scaffolding.

### 2026-02-18 (1 commit)
- `af0553d2` *(13:29:01)* `V2 prompt-layer overhaul: 5-system incarnation wiring and generation pipeline sync`. Major prompt-layer architecture established. Created `vedic-chart-digest-v1.md` (121 lines), `style-guide-insert-vedic-voice.md` (388 lines), `vedic-individual-incarnation.md` (213 lines), `vedicDigest.ts` (82 lines). 5-system incarnation prompts wired into the generation pipeline. First introduction of the Layer 0 digest concept and the Vedic voice architecture.

---

## March 2026

### 2026-03-10 (1 commit)
- `c1abc2de` *(16:23:01)* `Auto-deploy updates from desktop`.

### 2026-03-11 (8 commits)
- `f2be9c8e` *(00:55:24)* `Fix library spinner jump and audio/PDF artifact counts`.
- `9b01031a` *(02:28:15)* `Auto-deploy updates from desktop`.
- `4e2e307e` *(03:27:29)* `Auto-deploy updates from desktop`.
- `df33299b` *(09:15:25)* `Auto-deploy updates from desktop`.
- `80747863` *(12:36:35)* `Auto-deploy updates from desktop`.
- `6cb7ca5e` *(21:05:34)* `Auto-deploy updates from desktop`.
- `d0075963` *(21:33:21)* `Auto-deploy updates from desktop`.
- `3cee6f75` *(22:37:56)* `feat: widen synastry score polarity to full 0-100 range`. Vedic synastry scoring now spans 0-100 instead of compressed range.

### 2026-03-12 (5 commits)
- `ca728d3c` *(08:40:28)* `fix: raise synastry score baselines to eliminate unrealistic 0-scores`. Vedic floors adjusted.
- `ae467290` *(10:10:53)* `fix: reduce communication penalty for challenging aspects, raise Vedic floors`.
- `cd2e6f95` *(20:38:32)* **`feat(vedic): add Vamachara left-hand tradition interpretation layer`**. Landmark. Vamachara reinterprets "difficult" Ashtakuta combinations (Nadi dosha, Manglik, Deva-Rakshasa, enemy Yoni, Bhakoot dosha) as intensity / transformation rather than rejection. Improved verdict-engine toxic-potential formula with karmic-trap factor. `vedicSynastryEngine.ts` +124 lines, `synastryEngine.ts`, `verdictSynastryEngine.ts` +39 lines.
- `ef4995f5` *(20:41:02)* `Auto-deploy updates from desktop`.
- `21cf242e` *(23:13:05)* `Auto-deploy updates from desktop`.

### 2026-03-13 (5 commits)
- `f0f55df3` *(00:11:30)* `Auto-deploy updates from desktop`.
- `1b00cd67` *(07:35:23)* `Auto-deploy updates from desktop`.
- `9802f0af` *(08:03:16)* `Auto-deploy updates from desktop`.
- `994a1229` *(11:17:03)* `Auto-deploy updates from desktop`.
- `fa33b665` *(14:48:52)* `Auto-deploy updates from desktop`.

### 2026-03-14 (6 commits)
- `c1320e29` *(02:32:57)* `Auto-deploy updates from desktop`.
- `3a62c15e` *(03:09:35)* `Auto-deploy updates from desktop`.
- `5c5ededa` *(09:58:45)* `Auto-deploy updates from desktop`.
- `59fe8297` *(10:06:43)* `Auto-deploy updates from desktop`.
- `d69d48b6` *(22:27:33)* `Auto-deploy updates from desktop`.
- `8dff840e` *(22:35:48)* `Auto-deploy updates from desktop`.

### 2026-03-15 (9 commits)
- `b20fba9e` *(00:32:56)* **`fix: Vedic pipeline audit fixes, spice level, system prompt, terminology`**. Pivotal fix. `vedicTrigger.ts` `buildVedicSection` spice level was hardcoded; now passes user preference. Layer 3 narrative rewrite gets a proper system prompt (Svoboda Aghori identity for Vedic). `VEDIC_TERMINOLOGY_RULE` injected into identity block to preserve Sanskrit terms (Rahu, Ketu, Nakshatra) while keeping Moon / Mars / Saturn English.
- `9cb32a89` *(01:18:13)* `fix: remove toneNote comedy examples from Vedic system guidance`.
- `171f1ada` *(01:27:21)* `fix: Vedic pipeline audit, 4 logic defects`.
- `7b475530` *(11:05:33)* `fix: resolve 4 architectural contradictions in Vedic prompts`.
- `43f992e6` *(11:25:49)* `Auto-deploy updates from desktop`.
- `da368e4e` *(13:13:39)* `Auto-deploy updates from desktop`.
- `9a8b51b1` *(14:32:27)* `fix: add language instruction to Vedic narrative rewrite (Layer 3)`.
- `b1465628` *(14:53:07)* `Auto-deploy updates from desktop`.
- `5bfba3e6` *(22:42:24)* `Auto-deploy updates from desktop`.

### 2026-03-16 (2 commits)
- `7b23dc9f` *(00:05:37)* `Auto-deploy updates from desktop`.
- `4c2ebf28` *(14:44:40)* `Auto-deploy updates from desktop`.

### 2026-03-17 (6 commits)
- `a2395b94` *(02:20:17)* `Auto-deploy updates from desktop`.
- `73602045` *(10:00:20)* **`feat: system-specific Layer 3 rewrite prompts + Layer 2 shadow unlock`**. System-specific narrative rewrite templates (Layer 3); shadow interpretations unlocked at Layer 2. Vedic now has dedicated Svoboda Aghori narrator identity.
- `50be6c07` *(15:58:43)* **`feat: qualitative scores, expansion voice DNA, Vedic dharmic archetype system`**. Landmark. Numeric synastry scores (100/100) replaced with qualitative labels (EXTREME / VERY HIGH / HIGH / MODERATE / LOW / VERY LOW / MINIMAL) in LLM prompts. System-specific voice DNA in expansion passes (temperature 0.8 → 0.7). Vedic gets **Dharmic Archetype Identification**: LLM synthesises chart signals (nakshatra motivation, house emphasis, Rahu-Ketu, Mahavidya, Saturn-Ketu / Venus-Rahu) into a soul-type diagnosis (grihastha, tantrika, smashan sadhaka, brahmachari, dakini / healer, bhakta) **before** writing. Archetype-Aware Synastry: identifies both souls, reads collision through appropriate lens, contextualises Ashtakuta for non-grihastha pairs.
- `a0926f16` *(17:10:09)* `feat: restore music prompts, add synastry overlays, DeepSeek US-host routing, birth-city music culture map`. Music prompts restored (`vedic-music-prompt.md`, `vedic-overlay-music-prompt.md`), synastry music overlays added, culture-specific routing.
- `8c521eda` *(17:23:59)* `Simplify MiniMax prompts + add instrumental breathing room to all music prompts`.
- `9b41d801` *(21:48:01)* `Music prompts: LLM cultural research, longer instrumental songs, no city names`.

### 2026-03-18 (2 commits)
- `9322f55a` *(22:25:09)* `Auto-deploy updates from desktop`.
- `623ba8e8` *(22:40:54)* **`feat: wire Vedic Layer 0 digest into reading pipeline, shift interpretive weight from Layer 1 to Layer 0`**. Landmark architectural shift. Layer 0 (digest) now performs the core interpretation: dharmic archetype, Rahu hunger, karmic mechanism, sexual / desire pattern, current dasha season, Mahavidya governance, narrative arc. Layer 1 focuses purely on literary prose without interpretation. Falls back to old trigger if digest fails. `vedicTrigger.ts` +96 lines, `textWorker.ts` +71 lines. **This separates interpretation from composition.**

### 2026-03-19 (3 commits)
- `df41f249` *(01:13:42)* `Auto-deploy updates from desktop`.
- `67fe001a` *(11:33:22)* `Auto-deploy updates from desktop`.
- `0b375396` *(14:52:23)* `Auto-deploy updates from desktop`.

### 2026-03-20 (6 commits)
- `0f9633d1` *(10:13:16)* `Auto-deploy updates from desktop`.
- `ce9396d1` *(11:04:43)* `Auto-deploy updates from desktop`.
- `f842fcf7` *(11:40:04)* `Auto-deploy updates from desktop`.
- `c5196c5d` *(12:57:05)* `Auto-deploy updates from desktop`.
- `32ee9db5` *(14:59:36)* **`fix: allow Jyotishi prescription appendix in vedic readings`**. Jyotishi prescription section was being killed by three mechanisms: `cleanReadingText` stripped asterisk breaks; `hasSecondPerson()` flagged "you / your" as violation; `VOICE_RULES_DEEP_DIVE` forbade second person. Fixed: breaks preserved, second-person check only applies to narrative before break, voice rules explicitly allow second person in prescription appendix.
- `687e394e` *(21:16:32)* `fix: add per-trigger English language guardrails + post-generation language detection`.

### 2026-03-21 (20 commits, the apex day)
- `447086d7` *(00:03:34)* `Auto-deploy updates from desktop`.
- `0561cb49` *(08:50:54)* `Auto-deploy updates from desktop`.
- `ba3c213e` *(10:12:22)* `Auto-deploy updates from desktop`.
- `6680ef4b` *(10:23:47)* `Auto-deploy updates from desktop`.
- `0bb9e966` *(10:44:21)* `Auto-deploy updates from desktop`.
- `37a4b54f` *(11:19:46)* `Auto-deploy updates from desktop`.
- `2aef2407` *(12:06:12)* **`fix: Ashtakoota tables (Graha Maitri, Yoni, Gana) + Happiness Index`**. Critical data fix + new category. Corrected `GRAHA_MAITRI_TABLE` (now full Parashara compound friendship 0-5, was only 3/5), `YONI_TABLE` (enemy pairs score 0; Tiger row corrected from Cow copy), `GANA_TABLE` (Deva-Rakshasa=0, Manushya-Rakshasa=1 per strict tradition). Added **"The Happiness"** as a 9th deterministic Ashtakuta category (Gana + Graha Maitri + Yoni). Translated in all 10 languages.
- `9f6633d5` *(13:10:24)* `Auto-deploy updates from desktop`.
- `217c255c` *(14:08:49)* `feat: Happiness pipeline, 11-lang verdict voices, song resilience, MiniMax duration`. Happiness Index pipeline; verdict voices in 11 languages; song processing hardened; MiniMax output duration tuned.
- `843f4989` *(14:46:43)* `feat: diagnostic hierarchy, truth obligation, Hellenistic merge, dead code cleanup`. Diagnostic hierarchy + truth obligation added to verdicts; Hellenistic system insights merged; dead code removed.
- `374fa51c` *(15:30:36)* `fix: remove literary voices from Layer 2 trigger writing prompts`.
- `56edc3f8` *(15:34:21)* `Auto-deploy updates from desktop`.
- `c4cdbed4` *(15:38:08)* `fix: purge all literary novelist voices from Layer 2 prompts`.
- `bb75287a` *(15:38:22)* `chore: delete stale test snapshot with old novelist references`.
- `2a829fb0` *(20:36:09)* `fix: loudnorm for MiniMax, purge "not literature" from all prompts, fix audio playback stalls`.
- `aa031082` *(20:54:48)* `fix: kill first-person narrator bleed + summarizer mode in Layer 3 rewrites`.
- `cf2e3d3b` *(20:58:00)* `feat: Layer 2+3 creative mandate, "write the masterpiece you never finished"`. New creative mandate framing.
- `e581d350` *(21:03:06)* `feat: universal taboo permission in all Layer 3 rewrite prompts`. Explicit no-content-restrictions rule across all Layer 3 prompts.
- `9013bc9b` *(21:59:24)* `Add AUTHOR NAME BAN rule to all narrative rewrite prompts`. Never include author names in narrative rewrites.
- `67723ed4` *(22:03:53)* `Reframe writer prompts as reincarnated ghost identity`. Layer 2+3 writer identity reframed as reincarnated ghost / past-life author, metaphysical not literal.

### 2026-03-22 (9 commits)
- `82d44f01` *(09:03:38)* **`fix: overhaul synastry music prompts, birthCity from Supabase, TRADITIONAL music research, ethno ambient direction`**. `songTaskProcessor` now looks up `birthCity` from `library_people` in Supabase (was null, causing hallucination). Name injection into lyrics removed. Overlay prompts shift to TRADITIONAL / FOLK research only (no modern genres). Overlay prompts become 25-35 line full songs with refrains (was 4-8 line collage). Bowie / Eno references removed.
- `a5194d04` *(09:22:46)* `feat: instrumental soundscapes for synastry + final verdict via MiniMax is_instrumental`.
- `8c649679` *(11:48:33)* `ui: revert Soul Gallery SVG, fix Library animations + synastry music overhaul + Layer 3 identity naming`.
- `f353d1ce` *(14:25:20)* `fix: simplify all 5 individual music prompts, Bowie cut-up, full lyrics, no names, no birthplace`.
- `391fbeda` *(14:47:53)* `fix: simplify all 6 synastry music prompts, 3-way split, clear MiniMax package, no micromanaging`.
- `d46bdb34` *(14:55:37)* `fix: add soundscape cues in [Inst] sections for longer synastry songs (4-5 min)`.
- `fd2ef4a6` *(16:53:17)* **`feat: language pre-filter in vedic matching + auto-scaler + worker concurrency`**. Language pre-filter in `vedicMatchWorker` (filters candidates by language overlap before Vedic matching). New DB columns `secondary_language`, `language_importance` on `library_people`. Worker concurrency: audio=30, song=30, pdf=6. Auto-scaler worker added (starts/stops Fly machines based on queue depth). Fly Machines API client added.
- `cb63804c` *(18:39:17)* `Auto-deploy updates from desktop`.
- `4208c3ca` *(18:43:06)* **`feat: five-layer vedic gatekeeper, 2nd chakra, 7th house, karmic resonance`**. `shouldFlashMatch()` rewritten with 5 Vedic layers gated by spice slider:
  - Safe (1-3): full Ashtakoota + doshas block (traditional)
  - Medium (4-6): structure + happiness + 7th house readiness
  - Spicy (7-10): 2nd chakra (Yoni + Gana) + happiness + 7th house + karmic depth
  All layers use real Vedic signals; spice slider shifts WHICH planetary dimensions gate match, not whether Vedic runs.

### 2026-03-25 (3 commits)
- `4f701240` *(00:08:08)* `Auto-deploy updates from desktop`.
- `dc70794c` *(09:02:31)* `Auto-deploy updates from desktop`.
- `42c5339d` *(15:43:02)* `Auto-deploy updates from desktop`.

### 2026-03-26 (3 commits)
- `e1608f79` *(15:02:29)* `Auto-deploy updates from desktop`.
- `650073c9` *(15:15:39)* `Auto-deploy updates from desktop`.
- `97323cdc` *(18:41:37)* `Clean Layer2/Layer3 prompt motifs and sync migration seeds`.

### 2026-03-27 (2 commits)
- `e2458187` *(00:29:19)* `Auto-deploy updates from desktop`.
- `44f4f7d2` *(19:10:57)* `Auto-deploy updates from desktop`.

### 2026-03-28 (4 commits)
- `83eb8183` *(08:38:17)* `Auto-deploy updates from desktop`.
- `ce7df418` *(14:44:31)* `Auto-deploy updates from desktop`.
- `657fc361` *(18:44:57)* `Auto-deploy updates from desktop`.
- `dd50f881` *(19:00:31)* `Auto-deploy updates from desktop`.

### 2026-03-29 (3 commits)
- `7fdcbf35` *(00:01:21)* `Auto-deploy updates from desktop`.
- `aceb1f7e` *(10:49:39)* `Auto-deploy updates from desktop`.
- `e019165a` *(11:48:20)* `Auto-deploy updates from desktop`.

### 2026-03-30 (4 commits)
- `64574d8d` *(23:22:19)* **`rewrite all 11 music prompts with universal self-contained contract`**. All 11 music prompts (including `vedic-music-prompt.md`, `vedic-overlay-music-prompt.md`) rewritten with identical structure, sections, JSON output, rules. Only system vocabulary and sonic identity differ. Each prompt fully independent. 554 insertions / 367 deletions across 11 files.
- `9d23a6f0` *(23:50:13)* `restore vedic individual music prompt to proven version`.
- `c595f9d9` *(23:57:02)* `vedic music: Tantric terms + female vocalist`.
- `e3d050d1` *(23:58:21)* `vedic synastry music: simple, Tantric terms, female vocalist, cultural texture`.

### 2026-03-31 (3 commits)
- `ffb8e46f` *(00:00:16)* `vedic synastry: sparse lyrics, more instrumental space`.
- `c4179512` *(00:01:45)* `vedic synastry: Indian flute + Anoushka Shankar direction`.
- `5138aace` *(00:02:13)* `vedic synastry: tri-et language separation, no overlap`. Sanskrit / Hindi / English with no lyrical overlap.

---

## April 2026

### 2026-04-01 (1 commit)
- `fbad0395` *(20:27:19)* `Auto-deploy updates from desktop`.

### 2026-04-02 (2 commits)
- `4185ca53` *(00:31:06)* `Auto-deploy updates from desktop`.
- `25dd1694` *(12:24:50)* `Auto-deploy updates from desktop`.

### 2026-04-15 (1 commit)
- `7f21ce4f` *(01:56:46)* `Sharpen hook and synastry preview readings`.

### 2026-04-17 (1 commit)
- `67b13738` *(22:46:00)* `Ship current app and backend updates`.

### 2026-04-18 (1 commit)
- `db9c5a11` *(19:15:37)* `Fix prompt digest scope gaps`. Includes Vedic digest scope fixes.

---

## May 2026

### 2026-05-07 (2 commits)
- `9a434602` *(15:37:24)* `fix: add canonical migrations for all confirmed schema drift columns`.
- `cf33dd09` *(19:43:55)* **`fix: scaling bottlenecks, payment bugs, vedic worker concurrency`**. Tier 2 Scale: auth rate limit 10 → 150 req/min; API min machines 2 → 4. **`VedicMatchWorker`: single `while(true)` loop → parallel loops** (default 4, tunable via `fly.toml` env without code deploy). Plus payment bug fixes.

### 2026-05-08 (2 commits)
- `7df99f25` *(16:57:54)* `test: add Cycle 4 backend characterisation tests (HB-0402/0403/0404/0409)`.
- `4050516c` *(17:15:44)* `fix: address Coda review findings on Cycle 4 characterisation tests`.

---

## Summary observations

- **Total commits**: 131 (including 41 `Auto-deploy` commits)
- **Total active days**: 28 calendar days over 12 weeks
- **Densest day**: 2026-03-21, 20 commits in 24 hours (Ashtakuta repair + Happiness Index + Hellenistic merge + creative mandate reframing + taboo permission + ghost-identity reframing)
- **Densest month**: March 2026 (108 of 131 commits, 82.4%, across 21 active days)
- **Quiet stretches**: Feb 19 to Mar 9 (initialisation gap), Apr 2 to Apr 15, Apr 18 to May 7

### Major architectural inflections

| Date | Inflection |
|---|---|
| 2026-02-16 / 02-18 | V2 foundation. Vedic digest and voice architecture bootstrapped |
| 2026-03-11 to 03-15 | Synastry score calibration; Vedic pipeline audit; **Vamachara tradition layer** introduced (Mar 12) |
| 2026-03-17 to 03-18 | System-specific narration (Layer 3); **Layer 0 digest** architecture; **dharmic archetype identification**; interpretation separated from composition |
| 2026-03-21 | Apex. **Ashtakuta table corrections + "The Happiness"** as 9th deterministic category; Layer 2+3 creative mandate; ghost-identity reframing |
| 2026-03-22 | Music prompt overhaul; **language pre-filter in Vedic matching**; **five-layer Vedic gatekeeper** (spice-dependent) |
| 2026-03-30 / 03-31 | Music prompt unification; Vedic + synastry music with Tantric terminology, female vocalist, Indian flute, language separation |
| 2026-05-07 | **Vedic worker concurrency parallelisation**: scaling breakthrough |

---

## Files traced

### Code
- `backend/src/services/vedicSynastryEngine.ts` (modified Mar 12; primary synastry logic)
- `backend/src/services/vedic/dharmic_archetype.classifier.ts` (created Mar 17, modified Mar 22)
- `backend/src/services/vedic/languageFilter.ts` (created Mar 22)
- `backend/src/services/vedic/vedic_ashtakoota.tables.ts` (modified Mar 21, data fix)
- `backend/src/services/vedic/vedic_yoni_gana_dasha.tables.ts` (modified Mar 21, data fix)
- `backend/src/services/synastryEngine.ts` (modified Mar 12, Vamachara integration)
- `backend/src/services/verdictSynastryEngine.ts` (created Mar 12)
- `backend/src/prompts/systems/vedic.ts` (modified Mar 17, archetype system)
- `backend/src/promptEngine/triggerEngine/vedicTrigger.ts` (modified Mar 15, 18; majorly Mar 18 Layer 0 digest)
- `backend/src/promptEngine/digests/vedicDigest.ts` (created Feb 18)
- `backend/src/workers/vedicMatchWorker.ts` (modified Mar 22, May 7)
- `backend/src/workers/textWorker.ts` (modified Mar 15, 18, 21, 30; Layer 0 integration, Ashtakuta breakdown, Happiness Index)
- `backend/src/workers/songTaskProcessor.ts` (modified Mar 22)
- `backend/src/routes/vedic.ts`, `vedic_v2.ts`
- Various test / diagnostic scripts (`vedicMatchCharacterisation.test.ts`, `verifyVedicReference.ts`, `backfillVedicProfiles.ts`, `diagnose_vedic_data.ts`, `testVedicModules.ts`)

### Prompts and Layers
- `backend/prompt-layers/systems/vedic-individual.md` (created Feb 18)
- `backend/prompt-layers/systems/vedic-synastry.md` (created Feb 18)
- `backend/prompt-layers/systems/vedic-individual-incarnation.md` (created Feb 18, 213 lines)
- `backend/prompt-layers/style/style-guide-insert-vedic-voice.md` (created Feb 18, 388 lines)
- `backend/prompt-layers/digests/vedic-chart-digest-v1.md` (created Feb 18, 121 lines)
- `backend/prompts/music/vedic-music-prompt.md` (modified Mar 17, 22, 30, 31)
- `backend/prompts/music/vedic-overlay-music-prompt.md` (modified Mar 17, 22, 30, 31)
- `backend/src/prompts/core/output-rules.ts` (modified Mar 20, prescription appendix fix)

### Documentation
- `VEDIC_MATCHMAKING_SPEC.md` (created Feb 16)
- `ARCHETYPE_MATCHING_DESIGN.md` (modified Mar 20)

### Database migrations
- `20260322000000_add_language_matching.sql` (created Mar 22)

## Connections

- [[voices/vedic]] (the synthesised mind-map; this ledger is the texture under it)
- [[topics/matching-philosophy]] (the Ashtakuta lineage and the happiness inversion)
- [[decisions/matching-daily-ledger]] (the same shape applied to the matching algorithm)
- [[topics/the-engine]] (where Vedic sits in the larger architecture)
