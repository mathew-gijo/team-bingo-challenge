# Architecture: Team Bingo Challenge
*BMAD Phase 3 — Architect*

## Decision Summary
**One self-contained `index.html`** — inline CSS and vanilla JS, no build step, no dependencies, no backend.

### Why
- NFR1 demands zero-friction distribution: the facilitator can email the file, drop it on any static host, or AirDrop it.
- The domain is small (shuffle, grid state, line detection); a framework adds nothing but weight.
- Offline-by-default satisfies conference-wifi reality.

## Module Layout (within the single file)
| Module | Responsibility |
|---|---|
| `PROMPTS` | Flat array of 64 prompt strings, grouped by category comment. The one place organizers edit. |
| `dealCard()` | Fisher–Yates shuffle, take 24, insert FREE at index 12. |
| `state` | `{ playerName, squares: [{prompt, filledBy}], hasBingo }`, mirrored to `localStorage` on every mutation. |
| `checkBingo()` | Test 12 lines (5 rows, 5 cols, 2 diagonals) against filled squares. |
| `render()` | Full re-render of the 5x5 grid from state (small DOM; simplicity over diffing). |
| Print mode | Generates N independent cards into a print-only container; `@media print` stylesheet paginates one card per page. |

## Key Choices
- **Randomness**: `crypto.getRandomValues`-backed shuffle — not for security, just good distribution so nearby players get visibly different cards.
- **State shape**: squares keyed by grid index 0–24; index 12 is always FREE.
- **Duplicate-name check**: case-insensitive trim compare across `filledBy`; warn via confirm(), allow override (FR3).
- **Persistence key**: `teamBingo.v1` — versioned so future schema changes can invalidate cleanly.
- **Bingo UX**: full-screen overlay + CSS confetti (pure CSS animation, no library).

## Risks
- localStorage unavailable in private browsing on some browsers → wrap in try/catch, degrade to in-memory.
- Long prompts on small screens → clamp font-size, allow squares to grow vertically.
