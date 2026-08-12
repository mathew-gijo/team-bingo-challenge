# Stories: Team Bingo Challenge
*BMAD Phase 4 — Scrum Master*

## Story 1 — Welcome & card dealing
As a player, I enter my name and get a unique 5x5 card (24 random prompts + FREE center) so my card differs from my neighbor's.
**AC**: name required; prompts drawn without replacement; FREE always center; "New Card" re-deals with confirmation when progress exists.

## Story 2 — Prompt pool
As an organizer, I want 60+ inclusive prompts spanning work stories, craft/tools, get-to-know-you, and cross-org mixing, editable in one array.
**AC**: ≥60 prompts; ≥8 explicitly cross-org ("someone from the other org"); no alcohol/ability/family assumptions.

## Story 3 — Filling squares
As a player, I tap a square, type the colleague's name, and see the square stamped.
**AC**: name saved and shown in square; duplicate name across squares triggers a warning with override; tapping a stamped square lets me edit/clear it.

## Story 4 — Bingo detection & celebration
As a player, I get an unmissable celebration the moment I complete any row/column/diagonal.
**AC**: all 12 lines detected; FREE counts; overlay shows "BINGO!" + player name; dismissible; fires only on first bingo.

## Story 5 — Persistence
As a player, my card and progress survive a refresh.
**AC**: state restored from localStorage; "New Card" clears it; graceful fallback when storage is blocked.

## Story 6 — Print mode for facilitators
As a facilitator, I can print N randomized paper cards, one per page, with rules on each.
**AC**: N selectable 1–100; each card unique; B&W legible; name/date line on each card.

## Story 7 — Rules panel
As a player, I can read how to play without asking.
**AC**: collapsible panel covering win condition, one-person-one-square, and "have a real conversation" rule.
