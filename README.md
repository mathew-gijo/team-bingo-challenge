# Spring ✕ Alma Celebration Bingo

A human-bingo networking game for the Spring ✕ Alma celebration mixer (~120 people, product design + marketing). One self-contained file — no backend, no accounts, works offline once loaded.

## Files
- `index.html` — the entire game (player app + host leaderboard + print mode)
- `docs/` — BMAD planning artifacts (brief, PRD, architecture, stories, market research)

## The rules (built in)
- 5×5 card, all 25 prompts from the "Company Celebration: Bingo Card" doc, shuffled per player.
- **OTHER SIDE** squares must be matched by someone from the other side of the product (Spring ↔ Alma). SPRING/ALMA squares need a person from that team. Anyone qualifies for the rest.
- Claiming a square requires **who + the specific detail** that qualifies them.
- One person per card, max (the app warns on duplicates).
- **First to complete one row across + one column down (a criss-cross) wins.** Full card = 🏅 Overachiever Award.

## Run of show
1. **Before the event**: put `index.html` on any static host (or company intranet), make a QR code for the URL, and put it on a slide. Optionally print backup paper cards: open the app → Facilitator → set count → "Print cards".
2. **Kickoff (2 min)**: show the QR, tell people to enter their name + side. The "How to play" panel covers the rest.
3. **During**: players mingle; the app toasts when the first line (row or column) completes and shows a full-screen timestamped finish screen at the row + column criss-cross.
4. **Winners**: open the app on the host laptop → Facilitator → "Host leaderboard 📊" (or add `#host` to the URL) and project it. When a finisher shows their phone, add their name — the Winners' Circle displays them **in order of submission** with 🥇🥈🥉. Full-card finishers go in the separate Overachiever section.
5. Progress is saved on each phone (survives refresh/lock). "New Card" re-deals.

## Editing prompts
All prompts live in one `PROMPTS` array at the top of the `<script>` in `index.html`, each with a `tag`: `"cross"` (other side), `"spring"`, `"alma"`, or `null` (anyone). The win rule (row + column) lives in `finishMove()`/`completedLines()`.

## Known tradeoff
There's no live auto-updating leaderboard across phones — that requires a backend, which would break the offline-first design (see `docs/market-research.md`). The host-desk flow above is the proven fallback used at large events. A small Firebase/Supabase channel can be added later if wanted.
