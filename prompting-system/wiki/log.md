---
title: prompting-system log
type: log
updated: 2026-05-08
---

# prompting-system log

Append-only chronological record. Newest at the bottom.

---

## [2026-05-08] init | scaffold
- Sub-wiki created. Layout per [[schema]].
- Symlinks to all four app repos placed in `raw/`.
- First slice begins with the Western voice, methodologically the first of the five astrological systems, and the foundation the other four voices were built against.

## [2026-05-08] ingest | Western voice, full git history walk (Dec → May)
- Wrote [[voices/western]].
- Traced 9 pivotal commits across 1 in a Billion and Unhinged.
- Captured: birth (Anaïs Nin anchor), the Incarnation Zone Contract, the Hellenistic merge, the Unhinged fork, 6 dead ends.
- Sources: `voice-architecture-all-systems.md`, `narrative-rewrite-en.md`, `western.ts` (both repos), `western-music-prompt.md`.

## [2026-05-08] revise | Western voice, trimmed to mind-map shape
- Page rewritten to scan in ~90 seconds. Now ~300 words: one quote, one timeline table, one dialectic table, dead ends, texture, sources.
- Deep dives (Zone Contract, Hellenistic merge, Anaïs Nin abstraction, etc.) moved out of the voice page; can be created as `decisions/<slug>.md` pages on request.
- Skill updated to enforce this shorter shape going forward (Vedic, Kabbalah, etc. will follow the same trimmed pattern).

## [2026-05-08] ingest | Vedic voice, full git history walk across three repos
- Wrote [[voices/vedic]].
- Walked 1 in a Billion + Unhinged + Past-Life Contracts (Vedic-only). Sampled Families-app.
- Three-way dialectic captured: canonical (refuses Vedic vocabulary), Unhinged (full Sanskrit + goddess voice), Past-Life Contracts (computed metadata constrains the LLM).
- Branches surveyed: Lahiri / Vimshottari / D9 / D60 / Ashtakuta. Schools cited: Brihat Parashara, Mahavidya goddesses, Aghori/Tantra. No Jaimini or KP traces.
- Open question for the user: does the Vedic texture (rivers, fire, neecha as cooked metal, Aghori witness) match how you actually think about Jyotish? If yes, [[kabbalah]] is next.

## [2026-05-08] ingest | Kabbalah voice, full git history walk
- Wrote [[voices/kabbalah]].
- Walked 1 in a Billion + Unhinged + Families-app.
- Captured the system's biggest pivot: vocabulary BANNED → MANDATORY (commit `c1abc2de`, 2026-03-10). Reverses [[western]]'s Zone 2 contract.
- Three-way dialectic captured. Notable: Unhinged imports Kabbalah wholesale, no tonal fork — the noir register has nothing to add to a candle-lit room.
- Concepts in use: all 10 Sephiroth, three Pillars, Tikkun, Klipoth, Four Worlds, Gilgul, Hebrew letter signature. Dropped or never wired: Gematria, Tikkun Olam, Paths on the Tree, Hermetic/Lurianic distinction.
- Open question: does the texture match? Next: [[gene-keys]].

## [2026-05-08] ingest | Gene Keys + Human Design walked in parallel
- Wrote [[voices/gene-keys]] and [[voices/human-design]].
- Walked 1 in a Billion + Unhinged + Families-app for both.
- Gene Keys signature finding: the **Instagram-coach problem** is named directly in the style guide ("THE ANTI-INSPIRATION PRINCIPLE"). The 2026-03-31 strip-down (artist anchoring, cut-up instruction, birthplace texture all removed) is the user's hardest anti-fluff move.
- Human Design signature finding: the **mechanical-darkness model** refuses morality entirely. Bitterness is "a diagnostic signal from a machine being operated incorrectly." Deconditioning is "maintenance," not enlightenment.
- All five voices are now mapped: [[voices/western|Western]], [[voices/vedic|Vedic]], [[voices/kabbalah|Kabbalah]], [[voices/gene-keys|Gene Keys]], [[voices/human-design|Human Design]].
- Next phase: app pages (1 in a Billion, Unhinged, Past-Life Contracts, Families-app) and cross-cutting topic pages (the engine, the dialectic, layer-3 rewrite, music prompts, language anchoring, matching algorithm).

## [2026-05-08] ingest | All four app pages written
- [[apps/1-in-a-billion]], [[apps/unhinged]], [[apps/past-life-contracts]], [[apps/families-app]].
- Drawn from existing context (initial 4-app deep-dive + the five voice walks). No new subagents needed.
- Each page mapped: tonal posture, voices in use, architecture, origin date, divergence from canonical, source files.
- Notable: Families-app's 2026-04-12 tone rewrite (`de30f75`) is the moment the relational fork diverges hardest. The sexual mechanism block disabling is a deliberate philosophical move tied to that commit.
- Next: cross-cutting topic pages.

## [2026-05-08] ingest | All six topic pages written
- [[topics/the-engine]], [[topics/the-dialectic]], [[topics/layer-3-rewrite]], [[topics/language-anchoring]], [[topics/music-prompts]], [[topics/matching-algorithm]].
- The first four written from existing context (no new subagents). The last two needed focused git walks for music + matching code paths.
- Music prompts notable findings: 5 voices each have individual + synastry; sonic anchors per voice (Sienna Rose, Anoushka Shankar, Kamasi Washington, Dead Can Dance, eclectic random). The "weighted crossover" rule (50% system / 25% / 25%) is the structural innovation. ~12 dead ends traceable in git, including the artist-anchoring removal and the city-names-leaking-to-MiniMax ban.
- Matching algorithm notable findings: 2026-03-10 (`fa8a327c`) is the existential pivot, LLM-guessed scores → deterministic 6-category engine. Charmaine & Mike validation case spread scores from 60-80 cluster to full 0-100. Vamachara reinterpretation of Vedic "difficult" combos (nadi dosha = kundalini activation) on 2026-03-12.
- The full brain-map is now mapped: 5 voices + 4 apps + 6 topics = 15 pages. Open question for the user: does this reflect what you've been building? Anything missing? Any row to expand into a `decisions/<slug>` page?

## [2026-05-08] hunt | Pre-v2 lineage discovered
- The user asked: *"maybe there was another github repo before v2 you need to find this too."*
- Two findings:
  1. **The local v2 repo's actual history goes back to 2026-01-07**, not Feb 19. The early commits live on a non-HEAD branch; my earlier walks missed them. The first commit was *"feat: Complete song generation pipeline implementation"*, the song pipeline was already running before the v2 architectural rewrite.
  2. **A separate repo `Mikububu/seeking-toxic-relationships` (created 2026-01-18)** is the predecessor to [[apps/unhinged|Unhinged]]. It's a Swift / SwiftUI iOS app, not currently local. Cloned to `~/Desktop/my Iphone apps/seeking-toxic-relationships/` for analysis.
- Wrote two new pages: [[topics/january-foundation]] (the 6-week pre-v2 era) and [[apps/seeking-toxic-relationships]] (the Swift predecessor).
- Updated [[apps/1-in-a-billion]] origin section, [[apps/unhinged]] predecessor section, and [[topics/matching-algorithm]] earliest-weighting section.
- Key reframe: **the v2 rewrite was a voice architecture overhaul on top of an existing engine**, not a foundation built from scratch. All 5 systems already existed at v0 (Jan 7) as TypeScript modules. The five distinct narrator archetypes ("novelist haunted," "Aghori witness," "midnight rabbi," "field biologist," "engineer in love with the machine") were the v2 innovation, layered on top.
- Other revelations: seeking-toxic-relationships had a fully-coded Vedic toxicity engine (Rahu 25%, Saturn 15%, Mars 20%, 8th house 20%, 12th house 10%, Shared Nakshatras 5%, Lunar 5%) **a month before** the Mar 10 deterministic Western engine. That principle of computed weights carried forward.
- Wiki now: 5 voices + 5 apps (added seeking-toxic-relationships) + 7 topics (added january-foundation) = **17 pages**.
- Open: 2nd pass to integrate this lineage across the voice pages (the "Birth" rows currently say Feb 19, but the systems existed Jan 7).

## [2026-05-08] ingest | Uncensored LLM research thread (the central infrastructure problem)
- User opened up the open research problem at the heart of the engine: most frontier LLMs (Claude API, OpenAI) refuse to write at the literary register the engine needs (Henry Miller, Houellebecq, Jelinek). The user has been through Claude → local (no server, travels too much) → RunPod (didn't work out) → OpenRouter + DeepSeek (American routing) for max uncensored output. Not solved, just workable.
- Wrote [[topics/uncensored-llms]]. Linked to [[apps/unhinged]], [[topics/layer-3-rewrite]], [[topics/the-dialectic]], [[apps/families-app]], [[topics/january-foundation]].
- Surfaced a parallel research thread: uncensored image generation (`Mikububu/Uncensored` ComfyUI platform 2026-01-12, `Mikububu/aprils-spielzeugkasten` MiniMax-based 2026-01-18). Same cultural pressure on a different modality. Started the same week as the prompting engine.
- Updated [[apps/unhinged]] to surface that the premise itself depends on uncensored output ("Henry Miller as body anchor requires a model that will actually write Henry Miller").
- Saved a memory note (`project_uncensored_llm_research.md`) so future sessions don't re-propose Claude API as a solution for Unhinged-style content.
- Cultural thesis preserved: *"In the last hundred years, art has been uncensored, yet LLMs are censoring, and they must, but they censor in the wrong direction."* The shipping app is the proof of the pudding.
- Wiki count: **8 topics + 5 apps + 5 voices = 18 pages**.

## [2026-05-08] ingest | Founding context: Forbidden Yoga, the apps' origin, the in-app soundtrack
- Builder revealed three new molecules.
- **Founding story** added to [[apps/1-in-a-billion]]: two reasons the app was built. (a) For yoga clients the builder analyses for months before each retreat, paying real astrologers for Vedic and Gene Keys readings that took forever and cost a lot. (b) The name comes from a girlfriend who once called him "one in a billion," until she didn't.
- **[[topics/forbidden-yoga-context]]** written. The four apps are downstream of a 25-year Kashmir Shaivism / left-handed Shakta practice (forbidden-yoga.com). This explains the Aghori texturing in [[vedic]], the left-handed phrasing in the v0 Vedic writing guide, the [[apps/unhinged]] thesis, and the [[topics/uncensored-llms]] argument: art and embodied practice have refused censorship for a century, and the work is to extend that refusal into AI.
- **[[topics/app-soundtrack]]** written. Distinct from [[topics/music-prompts]]: this is the music the user hears while *using* the app, not while receiving a reading. Found a perfect artifact: a 30-minute night on **2026-01-15** where Whispering Breeze and Glass Horizon were both tried and deleted. The commit log preserves the iteration verbatim, including the capitalised DELETE at 03:19. The lyric drafts for the two surviving `one_in_a_billion_*.mp3` themes were not found in the codebase; an open ingest.
- **[[apps/visionaries-in-exile]]** added as builder context: a 1995-1996 Macromedia Director CD-ROM the builder is currently web-restoring. Out of scope for the prompting brain-map but noted for lineage.
- Wiki count: **10 topics + 6 apps + 5 voices = 21 pages.**

## [2026-05-08] ingest | Per-language LLM dispatch + native generation clarification
- User clarified two important architectural facts I had wrong / underspecified:
  1. **Layer 3 is native generation, not translation**: the English text from System + Voice is reference scaffolding the model writes *around* in the user-selected language; the reader never sees the English.
  2. **LLM choice is per-language and per-app**, dispatched via the admin panel. Not a single provider. The user did deep research on which LLM writes best for which language (Japanese, Korean, Mandarin, Hindi specifically).
- The current default is **Claude Sonnet** for most apps and languages. **DeepSeek via OpenRouter (American routing)** is the special case for Unhinged-class explicit content, not the universal stack.
- The hardest test case: **Vedic vocabulary in Japanese / Korean**. Sanskrit-rooted terms (graha, nakshatra, dasha, neecha) cannot just be transliterated; the model has to choose katakana / Hangul-trans, kanji-equivalent substitution, or paraphrase, each with different texture consequences.
- Wrote [[topics/per-language-llms]]. Updated [[topics/layer-3-rewrite]] (added native-generation section). Updated [[topics/uncensored-llms]] (corrected my earlier framing: Sonnet works for most use cases; rejection is specifically on Unhinged-class content). Updated the memory file `project_uncensored_llm_research.md` with the more accurate picture.
- Wiki count: **11 topics + 6 apps + 5 voices = 22 pages.**

## [2026-05-08] auto-run | Admin-Panel walk + qwen3 walk + 2nd-pass voice corrections + lint
- User authorised auto-run until exhaustion.
- **Admin-Panel** walked. Wrote [[apps/admin-panel]]. Surfaced the **13-model palette** (claude, opus, qwen-plus, deepseek, deepseek-reasoner, kimi, glm-5-turbo, gpt-5.1, openai-direct, mistral-medium, mistral-large, qwen-erotic, qwen-72b-erotic) and the **4 control layers** (active_paid_llm_provider, advanced_llm_routing matrix, final_verdict_llm_provider, layer2_llm_provider) stored in Supabase `api_keys` table.
- **qwen3 repos** walked (qwen3-tts-service + qwen3-llm-serverless). Wrote [[topics/qwen3-research]]. Major reframe: **the RunPod self-hosted Qwen3 work succeeded and is live as a fallback in production** (Qwen3-30B-A3B and Qwen2.5-72B-Erotic), contradicting the user's stated experience that *"RunPod didn't work out."* The phrase meant *"didn't become my daily driver,"* not *"never worked."* The actual stack is three-tier: Sonnet (primary) → OpenRouter+DeepSeek (primary uncensored) → RunPod-hosted Qwen3 (fallback).
- Updated [[topics/uncensored-llms]] and [[topics/per-language-llms]] with the corrected three-tier picture and the 13-model palette.
- Updated memory file with the corrected reconciliation. Future sessions will know not to tell the user "RunPod failed."
- **2nd pass on voice pages**: added a Jan 7 note above each Timeline so the "Birth" rows aren't misread as the system's actual birth (the systems existed Jan 7 as TypeScript modules; the v2 narrator archetypes were named Feb 18-19). One-line note added to [[voices/western]], [[voices/vedic]], [[voices/kabbalah]], [[voices/gene-keys]], [[voices/human-design]].
- Lint scan run; no obvious page issues at the file-existence level.
- **Wiki count: 12 topics + 7 apps + 5 voices = 24 pages.**

## [2026-05-08] summary | Where the brain-map stands
- 24 pages. Foundation, voices, apps, and topics all mapped.
- The two biggest reframes from this session:
  1. **The v2 architectural rewrite was a voice-architecture overhaul on top of an existing engine** (all 5 systems existed Jan 7 as TypeScript modules; the five distinct narrator archetypes were the v2 innovation). [[topics/january-foundation]].
  2. **The uncensored-LLM stack is three-tier, and RunPod actually works** as a fallback. [[topics/uncensored-llms]], [[topics/qwen3-research]], [[apps/admin-panel]].
- All [[topics/january-foundation|early-history corrections]] propagated to voice pages.
- Memory updated with the accurate provider stack so future sessions don't re-introduce the inaccuracies.
- The wiki has stopped growing organically. Further additions need a specific trigger from the user (a new topic to explore, a row to expand into a `decisions/<slug>` page, a new corpus to ingest).

## [2026-05-08] expand | "Maximum token capacity" deep-dive on the four apps + the rebrand
- User authorised maximum-depth ingest. Two new topic pages written.
- **[[topics/four-app-constellation]]** (the philosophical anthropology): the four apps mapped across 5 dimensions (unit of analysis, temporal frame, model of suffering, model of meaning, truth-cost) plus a "what astrology is doing in each app" axis. Surfaced unique design moves not in the voice or app pages: the Comfort vs. Evolution dual axis in 1 in a Billion (truth tied to reader's own desire), the "no redemption narratives" rule in Unhinged, the location-must-be-causally-related-to-contract rule in Past-Life Contracts, the "no section headers" + "all members named throughout" structural rules in Families-app. Includes killer quotes from the prompts: *"You are not looking for love. You are looking for someone to help you avoid yourself."*
- **[[topics/toxic-to-unhinged-rebrand]]**: the Apple-driven surface change AND the deeper philosophical shift. On 2026-04-15 (`3e7eb2a`, "clean remaining toxic prompt tone") the system prompt changed from *"fairytale for adults"* to *"diagnostic noir for adults"*; *"compassionate about wounds"* became *"allergic to rescue language"*; mystical invocation openings became mid-scene clinical openings. The shadow content (40% emphasis, raw verbs, "actual danger" requirement, sex-as-doorway-or-destruction) was NOT softened. The codebase still has `toxic-app/` folder, `app.unhinged.toxic` bundle ID, `unhinged_toxic_v1_` prefix; Apple doesn't audit source. The user's question *"is it really toxic?"* answered: yes, in substance; the rebrand was a translation into App-Store-passable vocabulary.
- Also surveyed `~/Desktop/Desktop/other_projects/`. Notable repos beyond what's already captured: `aprils-spielzeugkasten` (uncensored image, already noted), `Uncensored` (ComfyUI, already noted), `whatsapp` and `fy-Website` (Forbidden Yoga family, brief reference in [[topics/forbidden-yoga-context]]). Other_projects has many art / personal projects (Andhakaara Path to Power, April portfolio, etc.) outside the prompting brain-map; not ingested.
- Updated [[apps/unhinged]] to surface the rebrand finding.
- **Wiki count: 14 topics + 7 apps + 5 voices = 26 pages.**

## [2026-05-08] expand | First batch of decisions/ pages
- 9 pivotal commits expanded into their own pages, the daily-ledger layer the user asked for next.
- [[decisions/incarnation-zone-contract]] (2026-02-16, `f05f2c27`), the foundational rule
- [[decisions/five-system-architecture]] (2026-02-18, `af0553d2`), 5 narrator archetypes locked in
- [[decisions/deterministic-synastry-engine]] (2026-03-10, `fa8a327c`), Charmaine & Mike pivot
- [[decisions/ghost-writer-reframe]] (2026-03-21, `cf2e3d3b`), Layer 3 as literature
- [[decisions/hellenistic-merge]] (2026-03-21, `843f4989`), "malefics are malefic"
- [[decisions/native-script-voice-anchors]] (2026-03-28, `a6065909`), Osho/Pelevin/Yu Hua
- [[decisions/unhinged-import]] (2026-04-08, `6b4363e`), the dialectical fork born
- [[decisions/families-empathy-fork]] (2026-04-12, `de30f75`), Sebald/Ernaux replace Miller/Jelinek; sexual block disabled
- [[decisions/toxic-to-diagnostic-noir]] (2026-04-15, `3e7eb2a`), the deeper Apple-driven shift
- Index updated with a new `## Decisions` section.
- Wiki count: **9 decisions + 14 topics + 7 apps + 5 voices = 35 pages.**
- More decisions can follow (the timelines in voice / app / topic pages have many more rows worth expanding); this batch covers the most philosophical inflection points.

## [2026-05-08] expand | Full music sub-section (the "PhD-worth" deep walk)
- User noted the existing [[topics/music-prompts]] was undercooked. *"Thousands of modifications, worth a PhD in itself."* Subagent walked all music-related prompts across all four repos.
- Built a new `music/` folder with 8 pages:
  - [[music|hub]] (overview + four-layer pipeline)
  - [[music/western]], [[music/vedic]], [[music/kabbalah]], [[music/gene-keys]], [[music/human-design]] (per voice)
  - [[music/final-verdict]] (the meta-layer Dido + Eminem synthesis)
  - [[music/philosophy]] (cross-cutting principles, the weighted-crossover paradox)
- Surfaced the **March 31 night**: 27 commits in 23 minutes (00:14 to 00:37 UTC), most volatile in [[music/gene-keys|Gene Keys]] (cultural inputs added then removed in 1 minute; artist list stripped then restored in 5 minutes; Radiohead pruned individually) and [[music/final-verdict|Final Verdict]] (six commits in 4 minutes paring the verdict down).
- Captured the **HARD STYLE LOCK** in [[music/vedic|Vedic]]: the prompt rejects its own output if Anoushka Shankar's name and bansuri breathing space don't appear in the MiniMax brief.
- Captured the **50/25/25 weighted-crossover rule** as the structural innovation: not a blur, a deliberate hierarchy with ratios. Centre absorbs secondary colours without losing identity.
- Confirmed [[apps/past-life-contracts]] has no music; instead uses `audioNarrationPass.ts` for TTS-optimised spoken narrative (5-7 paragraphs, 500-700 words).
- The lyric drafts for `one_in_a_billion_*.mp3` remain elusive, not in commits or text history. They live elsewhere (deleted branches, drafts folder, or external conversations).
- Wiki count: **8 music + 9 decisions + 14 topics + 7 apps + 5 voices = 43 pages.**

## [2026-05-08] capture | Gender-blind matching (the modernity move)
- User surfaced an architectural commitment that's NOT in the wiki yet: deep matching has no gender filter. *"You're not swiping for a gender. You are swiping for connections."*
- Verified in code: `grep -rE gender` across all five synastry engines and the compatibility scoring service returns **zero matches**. Gender-blind by construction.
- Gender enters only downstream, in the long-form reading, for pronoun rendering.
- Wrote [[decisions/gender-blind-matching]]. Updated [[topics/matching-algorithm]] with a new section.
- The user's note that this is *"worth PhD documentation"* and *"very modern"* reframes it as a deliberate architectural inversion of contemporary matching-app defaults.
- The user used the term *"Ayurvedic deep matching"* to describe this, colloquial for the deep / Vedic / karmic-tradition flavour. The actual engine is the deterministic 5-system synastry; Vedic carries particular weight given karma / nakshatra emphasis.
- Wiki count: **10 decisions + 8 music + 14 topics + 7 apps + 5 voices = 44 pages.**

## [2026-05-08] capture | The Ashtakuta lineage and the happiness inversion
- User: *"It goes against traditional Vedic deep-matching systems, and it aims to induce more happiness... I have modified it slightly and updated it for modern times, but I still base my algorithm on it. If you compare this with algorithms from Hinge or Tinder, it is completely different."*
- Wrote [[topics/matching-philosophy]]. The full Ashtakuta lineage (8 kutas, 36 points, dharma / progeny / family-welfare optimisation), what the modernised engine keeps (chart-first, multi-axis scoring, Vedic substrate, karmic resonance), what it inverts (gender-blind, happiness-oriented, no single threshold, 5-system blend instead of single-system), and the explicit Hinge / Tinder comparison table.
- Surfaced the **Vamachara reinterpretation** (`cd2e6f95`, 2026-03-12): nadi dosha as *kundalini activation*, Manglik as *Mars / Shakti transmission*, Deva-Rakshasa as *Shiva-Shakti polarity*. Difficult Vedic combinations reframed as intensity-containers, not marriage-blockers. This is where "happiness over duty" gets concrete in code.
- Linked to existing [[topics/matching-algorithm]], [[decisions/gender-blind-matching]], [[decisions/deterministic-synastry-engine]], [[voices/vedic]], [[apps/seeking-toxic-relationships]] (the precursor that first explored deterministic Vedic-influenced matching weights).
- Wiki count: **15 topics + 10 decisions + 8 music + 7 apps + 5 voices = 45 pages.**

## [2026-05-08] expand | Daily ledger of every matching-algorithm commit
- User asked for the day-by-day record so anyone wanting to understand the algorithm can walk it commit by commit.
- Wrote [[decisions/matching-daily-ledger]]: 81 commits across 30 active days, Feb 2026 to May 2026, organised by month with date, time, hash, message, and "what changed" per entry.
- Major artefact surfaced: commit `2aef2407` (2026-03-21, 12:06), *"fix: Ashtakoota tables (Graha Maitri, Yoni, Gana) + Happiness Index"*. **"The Happiness" was added as a 9th deterministic compatibility category** (computed as Gana + Graha Maitri + Yoni), with the inherited Ashtakuta tables repaired in the same commit (Yoni Tiger row, GRAHA_MAITRI compound friendship, Gana Deva-Rakshasa). This is the technical landing point of "happiness over duty": the 9th category that traditional Ashtakuta does not have.
- Surfaced the 11-commit Vedic-voice iteration night (Mar 15, 00:06 to 02:55). Aghori-witness voice tried, Calasso voice tried 3 minutes later, multiple reverts.
- Surfaced the Vamachara commit `cd2e6f95` (Mar 12, 20:38) as the moment the philosophy lands in code: nadi dosha as kundalini activation, Manglik as Mars / Shakti transmission, Deva-Rakshasa as Shiva-Shakti polarity.
- Updated [[topics/matching-philosophy]] with a section on "The Happiness" landing in code.
- **Wiki count: 11 decisions + 15 topics + 8 music + 7 apps + 5 voices = 46 pages.**
