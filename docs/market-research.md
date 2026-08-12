# Market Research: Digital Human Bingo Apps
*BMAD supplemental research — 2026-08-10. Full agent report.*

(See PRD for how findings map to requirements.)

## Jam Bingo (thejamsocial.com) — category leader
- Organizer creates game (~2 min, account required); attendees join via one QR code, play in mobile browser, no download/account.
- Same prompts for everyone, shuffled per player.
- Verification: players scan each other's personal QR (or type a short code) — squares only complete via real mutual connection; doubles as contact exchange.
- Placement finishing: game doesn't stop at first winner; each finisher sees 1st/2nd/3rd… so hosts award "first N finishers." Also tracks "most unique connections."
- Live leaderboard + host analytics (backend-driven). Claims standard event wifi is sufficient. Pricing sales-gated (annual access).

## Competitors
- **Bingo Baker** — $24.95 lifetime card generator; honor-system daubing; built for called-number bingo, not mingling.
- **MyFreeBingoCards** — printable workhorse; free ≤30 players, ~10¢/card; caller-centric, no mingle features.
- **Bingo Party (playbingo.party)** — free, no registration, real human-bingo focus; collaborative card building + shared live progress; unproven at 120 concurrent.
- **QuizBreaker** — async remote-team quizzes; not a live-mixer fit.
- **Brightful** — hosted meeting games, ~100 player ceiling; screen-focused.
- **Slides With Friends / Kahoot family** — host-screen + phone responders; keeps attention on a screen, not on people. Wrong shape for a walk-around mixer.
- **Goosechase** — photo-verified scavenger hunts; heavier setup/moderation.

## Ranked features for a 120-person mixer (backend needed?)
1. Zero-friction join: QR → browser card, no account (no backend)
2. Same prompts, shuffled per player (no)
3. Mutual/documented verification of matches (mostly no)
4. Placement finish, not sudden death (display: no; authoritative order: host desk or backend)
5. Live leaderboard / host screen (**yes — only true backend feature**)
6. Custom prompts tuned to the orgs (no)
7. Printable fallback from same prompt set (no)
8. Progress persistence (no — localStorage)
9. Connection recap after game (mostly no)
10. Host analytics/export (yes)

## Failure modes to design against
- Venue wifi dead zones → offline-first, tiny payload, cache everything.
- Honor-system gaming → require who + qualifying detail (or mutual codes).
- Sudden-death winner kills the room → placement finishing.
- Prompts too hard/too niche → calibrate mostly high-match-probability prompts.
- Friend clustering → cross-org prompts + unique-connections scoring.
- QR scanning friction → always offer typed fallback.
- Onboarding confusion → one-glance join screen, 10-second tutorial.

## Verdict
No-backend single-file build is viable and defensible: covers ranked items 1–4 and 6–9 client-side. Live leaderboard is the only sacrifice; mitigate with a host-desk finish flow (finisher shows completion screen; host records placement on a projected slide).
