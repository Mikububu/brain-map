---
title: The Toxic-to-Unhinged Rebrand (Apple-Driven)
type: topic
created: 2026-05-08
updated: 2026-05-08
tags: [topic, unhinged, apple, app-store, distribution, branding]
---

# The Toxic-to-Unhinged Rebrand

The user's question: *"Why did I change the toxic? I removed it because of Apple."* This page maps what was renamed, what stayed, and what was actually softened. The answer is not "branding only", and it's not "everything" either. The rebrand was a *translation* into a vocabulary that passes App Store review.

## Three names, one app concept

| Name | Format | Period | Status |
|---|---|---|---|
| **Seeking Toxic Relationships** | Swift / SwiftUI iOS app | 2026-01-19 to 2026-02-12 | Abandoned. See [[apps/seeking-toxic-relationships]] |
| **toxic-app** (workspace name) | Expo React Native + Hono backend | 2026-04-08 onward | The codebase folder; never renamed |
| **UNHINGED** | Public App Store name | 2026-04-08 onward | The user-facing brand |

The product flipped from explicit ("Seeking Toxic Relationships") to coy ("UNHINGED") *across the rebuild*, not after.

## What changed (the surface that Apple sees)

Apple's review process audits **app name, subtitle, description, screenshots, content**. It does not audit source code or internal naming. UNHINGED was designed to pass this filter.

| Surface | Before | After |
|---|---|---|
| App name in App Store | Seeking Toxic Relationships | **UNHINGED** |
| App Store subtitle | "Mismatch-First Compatibility" | **"Decode your romantic chaos"** |
| Domain | seeking-toxic.app | **unhinged-matchmaking.online** |
| Marketing language | explicit "toxic" framing | "romantic chaos" |
| Opening prompt language | *"fairytale for adults"* | *"diagnostic noir for adults"* |

## What stayed (the codebase residue)

Apple does not look here, so none of it was renamed:

- Folder path: still `/toxic-app/`
- iOS bundle ID: still `app.unhinged.toxic`
- Android package: still `app.unhinged.toxic`
- IAP product ID prefix: still `unhinged_toxic_v1_`
- Backend Fly.io configs: still `fly.toxic.text-pdf-audio-song.toml` etc.
- GitHub Actions: still references `fly.toxic` infrastructure
- Variable names, comments, commit messages: still reference "toxic" liberally

This is deliberate. Renaming the folder, bundle ID, and 100+ internal references would introduce massive refactoring risk days before App Store launch. Apple's review process happens at the app-name and listing-copy level, not at the codebase level.

## Did Apple force a softening of substance?

**Yes, partly.** This is the most important finding. The rebrand was not just cosmetic.

### Before April 15 (`9e6efbd`, "toxic-chic rewrite")

System prompt: *"You are telling the story of a soul. Not analyzing a chart. This is a fairytale for adults. A mystery theater of longing and obsession."*

Tone: *"Dreamy and mythic, like a fairytale for adults... Honest about shadows, compassionate about wounds."*

Opening instruction: *"Begin like a fairytale for adults, an invocation that makes the listener pause."*

Override name: `toxicComedyOverride` with phrase *"SEEKING TOXIC ARRANGEMENTS."*

### After April 15 (`3e7eb2a`, "clean remaining toxic prompt tone")

System prompt: *"You are telling the story of a person who already knows they are the problem. Not analyzing a chart. This is diagnostic noir for adults. A sharp theater of longing, obsession, defense, and cost. Write as a storyteller who sees the invisible architecture of a pattern and refuses to rescue it."*

Tone: *"Darkly funny and precise, like a forensic narrator with perfume on the evidence bag... Honest about shadows, clear about wounds, allergic to rescue language."*

Opening instruction: *"Begin in the middle of a diagnosis already happening, not with an invocation... Start mid-scene, mid-observation, as if the reader walked in on something."*

Override name: changed to `chaosComedyOverride` with phrase *"DECODE YOUR ROMANTIC CHAOS."*

### The shifts

- *fairytale* → *diagnostic noir* (more forensic, less mystical)
- *compassionate about wounds* → *allergic to rescue language* (harder, less therapeutic)
- *invocation-based openings* → *mid-scene, clinical openings* (more observational, less mythic)
- *Seeking Toxic Arrangements* → *Decode Your Romantic Chaos* (less explicit, more coy)

## What stayed strong (the shadow content survived)

The "spicy-surreal" style — the app's actual transgressive voice — was **not softened**. The shadow content stayed at full strength:

- *"Raw verbs: devour, penetrate, consume, shatter, burn, dissolve, possess"* (unchanged)
- *"Body language: sweat, blood, bone, flesh, nerve, marrow, skin"* (unchanged)
- *"Include ACTUAL DANGER: addiction, emotional violence, manipulation patterns, betrayal trajectories"* (unchanged)
- *"Sex as doorway or destruction"* section (unchanged)
- 40% shadow emphasis (unchanged from pre-rebrand)

## Is it really toxic?

Yes, in substance. The rebrand softened the *presentation*, not the truth-telling.

The current App Store description: *"UNHINGED sorts by who bends the room... Instead of ranking your most compatible match first, we surface tension, asymmetry, friction, and beautifully questionable chemistry. The first profile you see is the one your therapist would gently suggest you avoid."*

The actual reading still includes worst-case-trajectory analysis: *"every relationship analysis should include exploration of worst-case trajectory."* It still names manipulation, addiction, emotional violence, betrayal patterns directly. Apple does not care that the reading says *"this pairing will destroy you emotionally"*; Apple cares that the app name does not say "TOXIC" on the home screen.

## What was lost

- The explicit *fairytale* framing (mystic permission to explore shadow)
- Invocation-based openings (replaced by diagnostic mid-scene language)
- The *compassionate* qualifier (replaced by *allergic to rescue language*)
- The *seeking toxic* branding (replaced by *decode your chaos* coyness)
- Mystical tone as the primary lens (clinical / forensic tone now primary)

## What this teaches about platform distribution

Four observations:

1. **Name and listing copy are filtered. Source code is not.** Apple's review does not run `grep -r "toxic"`. It reads the 4000-character app description.
2. **Mystical framing was Apple-tax. Diagnostic framing passes.** The same shadow analysis ships when framed as "noir diagnosis" but gets rejected when framed as "fairytale mystery." The *content* is identical; the *genre* matters.
3. **Internal naming is free.** The product can be called `unhinged_toxic_v1_tier_1` in backend code because Apple never sees it.
4. **Philosophy survives; branding dies.** The app still delivers what it promised: *"the one your therapist would gently suggest you avoid."* The path to that delivery changed from mythic-poetic to clinical-precise. The substance remained transgressive; only the language changed.

## Why "toxic" was kept in code

Because the rebrand was not a surrender. It was a translation. *"Decode your romantic chaos"* says the same thing as *"seeking toxic relationships"*, but in a vocabulary that passes review. Renaming the codebase would erase the genealogy; the user kept it as evidence of where the work came from.

## Pivotal commits

| Date | `<hash>` | Move |
|---|---|---|
| 2026-04-08 12:04 | `6b4363e` | Initial import; app.json already says `name: "UNHINGED"`, `bundleIdentifier: "app.unhinged.toxic"` |
| 2026-04-08 19:54 | `9e6efbd` | "toxic-chic rewrite," system prompt still *fairytale for adults* |
| 2026-04-10 18:42 | `b0bcca4` | 6 App Store compliance fixes |
| 2026-04-15 22:55 | `3e7eb2a` | **"clean remaining toxic prompt tone"**: *fairytale → diagnostic noir* |
| 2026-05-01 08:55 | `d212895` | "finalize unhinged rescue updates"; subtitle: *Decode your romantic chaos* |

## Connections

- [[apps/unhinged]] (the app this rebrand reshaped)
- [[apps/seeking-toxic-relationships]] (the abandoned Swift predecessor)
- [[topics/the-dialectic]] (Unhinged as the dialectical opposite of canonical)
- [[topics/four-app-constellation]] (Unhinged's role in the larger philosophical map)

## Sources

- `raw/unhinged/toxic-app/app.json` (bundle ID source of truth)
- `raw/unhinged/toxic-app/APP_STORE_LISTING.md`
- `raw/unhinged/toxic-app/backend/src/prompts/styles/production.ts` (the file changed by `3e7eb2a`)
- `raw/unhinged/toxic-app/backend/src/prompts/styles/spicy-surreal.ts` (unchanged, where the actual shadow content lives)
- `raw/unhinged/toxic-app/backend/src/scripts/pushIapMetadata.ts`

Commits: `6b4363e` · `9e6efbd` · `b0bcca4` · `3e7eb2a` · `d212895`
