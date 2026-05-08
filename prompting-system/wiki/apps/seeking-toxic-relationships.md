---
title: Seeking Toxic Relationships
type: app
status: abandoned
created: 2026-05-08
updated: 2026-05-08
tags: [app, predecessor, swift, vedic, abandoned]
---

# Seeking Toxic Relationships

The Swift iOS predecessor to [[apps/unhinged|Unhinged]]. Active **2026-01-19** to **2026-02-12**. Abandoned for **56 days**, then rebuilt as Unhinged on a different stack.

## What it was

An iOS-native dating app prototype in **Swift + SwiftUI**. Vedic astrology used to surface volatile, obsessive relationship patterns through a Tinder-style swipe interface. Stack: SwiftUI, local MockMatchService, no backend.

## Concept

Deliberately isolated and amplified *unstable* relational dynamics rather than optimising for compatibility. Match scores emphasised Rahu obsession, Saturn endurance, Mars aggression, and 8th / 12th house overlays.

The design doc was explicit: *"must read and consume all relevant Markdown files from the One in a Billion folder as read-only input."* The app *"must not contain its own competing doctrine."* From day one, Seeking Toxic was conceived as a **parasite on [[apps/1-in-a-billion]]'s engine**, not an independent product.

## Architecture

- **Native iOS**: Swift + SwiftUI. `OnboardingView` (405 lines), `SwipeView` (300 lines), Models (User, Match, SynastryDetails)
- **Aesthetic**: neobrutalist (#000000 black, #FF453A iOS red, rounded typography, "visual aggression 0.7")
- **No real ephemeris**: `MockMatchService` generated random toxicity scores 6.0-10.0 with branching descriptions
- A **"new-arch" monorepo** (React Native + Node.js backend) was committed at launch but never built. Cross-platform pivot waiting to happen.

## The Vedic toxicity engine

The synastry engine (in the unbuilt new-arch) coded an explicit weighting:

| Factor | Weight |
|---|---|
| Rahu Influence | 25% |
| Saturn Endurance | 15% |
| Mars Aggression | 20% |
| 8th House Intensity | 20% |
| 12th House Loss | 10% |
| Shared Nakshatras | 5% |
| Lunar Compatibility | 5% |

Plus a separate "Explosive Combinations" axis. This is **the earliest deterministic synastry weighting in the user's body of work**, predating [[topics/matching-algorithm|the 1-in-a-Billion deterministic engine]] (`fa8a327c`, 2026-03-10) by a month.

## Timeline (4 commits)

| Date | Move | What changed |
|---|---|---|
| 2026-01-19 | Initial commit (`64213df`) | Swift UI scaffolded; new-arch monorepo committed (unbuilt); MockMatchService + design_config.md |
| 2026-02-12 | V2 migration checkpoint (`4f9e1ca`) | 131 files / 34K lines. Full React Native rewrite drafted. Swift abandoned. MIGRATION_DECISIONS.md codifies the pivot |
| 2026-02-12 | First-match alerts consent (`c65ea32`) | matchNotifications.ts added; HomeScreen + SettingsScreen wired for opt-in alerts |
| 2026-02-12 | GitHub Actions CI for v2 (`43d2564`) | `v2-ci.yml`; cross-platform build automation |

## The abandonment

Commits stopped on **2026-02-12**. Nothing further. The V2 React Native rewrite was never deployed (no build, no tests, no rollout). The work was frozen mid-implementation.

On **2026-04-08** (56 days later), [[apps/unhinged|Unhinged]] was created under a new GitHub repo (`unhinged-toxic`) with a fresh `chore: initial import` commit. A clean rebuild rather than a continuation.

## What survived into Unhinged

- The **Vedic-as-toxic-matching philosophy** (Rahu, Saturn, Mars, 8th / 12th house logic)
- The **neobrutalist design language** (black background, red primary, rounded typography)
- The **"toxicity scoring" terminology** (0-10 intensity scale)
- The narrative-driven **fit cards / watchouts** framework
- The **first-move suggestions** as intimate, prompt-like guidance

## What was abandoned

- The **Swift / SwiftUI iOS codebase entirely**
- The local MockMatchService and in-app chart calculation
- The "new-arch" monorepo structure (Unhinged adopted a flatter architecture)
- The free-swipe-limit subscription model (Unhinged shifted to reading-based subscriptions)
- The multi-screen onboarding flow (compacted in Unhinged)

## What this teaches

Seeking Toxic was never meant to be independent. From the design doc onward, it was a **toxicity-amplifying lens on 1-in-a-Billion's reading engine**. The Swift codebase was a UI prototype that explored the matching axis (Vedic patterns specifically) before merging that axis back into the canonical engine via Unhinged in April.

The 56-day gap is the user clearing the deck before rebuilding the same idea on the right substrate.

## Sources

- `~/Desktop/my Iphone apps/seeking-toxic-relationships/` (cloned 2026-05-08)
- `Models/AppState.swift`, `Services/MockMatchService.swift`, `Views/OnboardingView.swift`, `Views/SwipeView.swift`
- `new-arch/packages/shared/astrology/src/synastryEngine.ts`
- `design_config.md`, `SEEKING TOXIC RELATIONSHIPS .rtf`
- `MIGRATION_DECISIONS.md` (via `git show 4f9e1ca:MIGRATION_DECISIONS.md`)

GitHub: `Mikububu/seeking-toxic-relationships`. Commits: `64213df` · `4f9e1ca` · `c65ea32` · `43d2564`.
