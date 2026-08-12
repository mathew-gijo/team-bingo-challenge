# PRD: Team Bingo Challenge — Spring ✕ Alma Celebration
*BMAD Phase 2 — Product Manager · v2 (updated with confirmed requirements, 2026-08-10)*

## Overview
A single-page web app for a live in-person celebration mixer (~120 people) across the product design and marketing orgs of Spring Health and Alma. Playable on phones, printable for paper play. No backend, no accounts.

## Confirmed Requirements (from stakeholder)
- **Format**: phones + printable fallback (chosen 2026-08-10).
- **Setting**: live in-person mixer.
- **Group size**: ~120 players.
- **Prompt source**: the "Company Celebration: Bingo Card" Google Doc — exactly 25 prompts (13 work/product, 2 cross-company, 10 fun/personal). This is the canonical list; the app must use it verbatim.

## Game Rules (from the prompt doc)
1. **5×5 card, no FREE square** — the 25 prompts fill the grid exactly; each card shuffles their positions so neighbors' cards differ.
2. **Cross-side rule**: prompts that mention Spring or Alma must be matched by someone from the *other* side of the product than the player. All other prompts: anyone in the room qualifies. The app labels these squares and asks the player which side they're on at start.
3. **Documentation rule**: to claim a square the player records *who* AND *the specific detail* that qualifies them (e.g. "Maya — 14 subscriptions").
4. **Win condition** (updated 2026-08-12 by stakeholder): first player to complete **one row across + one column down** (a criss-cross) wins. Supersedes the doc's "two rows" rule and the earlier "first bingo" choice.

## Functional Requirements
- **FR1 Onboarding**: player enters name + picks their side (Spring / Alma); gets a shuffled card.
- **FR2 Square claiming**: tap square → record name + qualifying detail; both required. Duplicate-person warning (one person per card, override allowed). Cross-side squares display a badge reminding the player who qualifies.
- **FR3 Progress + win**: row-completion indicator; celebration at ONE row ("1 down, 1 to go!") and full-screen win at TWO rows.
- **FR4 Persistence**: localStorage; refresh-safe; "New Card" re-deals with confirmation.
- **FR5 Print mode**: N printable cards (1–150), one per page, shuffled per card, with instructions block and name/side/date lines; B&W legible.
- **FR6 Rules panel**: in-app copy of the doc's instructions.

## Non-Functional Requirements
- Single HTML file, zero dependencies, offline once loaded (venue wifi is unreliable).
- Card fully visible without horizontal scroll at 375px.
- Time-to-card under 10 seconds.

## Open Items (pending market research)
- Features borrowed from Jam Bingo & competitors worth adding client-side (QR join, host screen, sound, etc.).
