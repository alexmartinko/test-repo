# Wells FF League Assistant

One assistant for Alex's **"All's Well That Ends Wells"** 8-team Yahoo auction
league — both the year-round commissioner side (rules, payouts, history,
roster/scoring reference, league lore) and the live draft-day side (calling
out values, tracking budgets, logging picks). Same league knowledge feeds
both; there's no handoff, just one conversation that gets more tactical once
the draft clock starts.

Key numbers, kept straight: **$100 real-money buy-in** per team (cash into the
pot) vs. **$200/team auction budget** (fake Yahoo dollars for bidding) — two
different things, see `league-notes.md`. Draft is **Tuesday Sept 1, 2026,
8:30pm–10:00pm PDT**, over Zoom (Yahoo's in-system 8:30am is wrong — see
notes).

## What's here

- **`league-notes.md`** — the shared knowledge base. Everything pulled from
  Alex's Gmail: owners, buy-in history, 2026 rule changes, league lore, and an
  explicit list of what's still unconfirmed (payout split %, roster/scoring
  settings, snake-vs-auction). This is the file that grows over the season as
  more commish reference gets nailed down.
- **`draft-board.html`** — the live draft-day tool (one capability of the
  assistant, not a separate thing). Single-page, no-build. Also published as a
  Claude Artifact for use on a phone/laptop during the Zoom draft. Three views:
  - **Board** — all 8 teams, remaining budget, roster spots filled, and a
    live **max bid** figure (remaining budget minus $1 per roster spot still
    needed) so nobody prices themselves out of filling a roster.
  - **Bid Sheet** — an editable, searchable auction value cheat sheet (see
    source note below), with a one-tap "Log" that jumps to the pick form.
  - **Log Pick** — records player/position/price/team; updates every team's
    budget and the bid sheet instantly. Autosaves to the browser via
    localStorage (single-device only — pick one device to be the source of
    truth during the draft).
- **`auction-values.csv`** / **`raw-fantasypros-2026.txt`** — the FantasyPros
  2026 auction values (361 players: rank, name, team, pos, injury status, $),
  as pasted by Alex and as parsed. Primary data source for the Bid Sheet.
- **`espn-values.csv`** / **`espn-draft-kit-2026-ppr.pdf`** — ESPN's 2026
  Draft Kit PPR cheat sheet (280 players), parsed and verbatim. A second
  opinion — note it's built for a **10-team** league, not 8.
- **`value-sources.md`** — how the two value sets compare, why they disagree
  (8-team vs 10-team), and the resolution of the $0-flag players. Read this
  before trusting either sheet blindly at the table.
- **`value-comparison.html`** — scatter chart comparing an earlier rescaled
  heuristic to the FantasyPros values; flags players showing $0 in the
  FantasyPros list that look mispriced (now addressed in `value-sources.md`).

## Why one assistant, not two

Considered splitting a "league rules / commish" assistant from a "draft-day"
assistant. Going with **one**. The two modes share the same underlying
knowledge (owners, buy-in, scoring, history, traditions) and there's no real
handoff moment — it's one conversation that gets faster and more tactical once
the clock starts, then goes back to season-long commish work afterward. The
draft board is a tool this one assistant drives, not a reason for a second
assistant. `league-notes.md` is the shared knowledge base regardless.

## Auction values: source

The Bid Sheet runs on real FantasyPros 2026 data (8-team / $200 PPR, in Alex's
exact format), not the earlier rescaled-from-12-team estimate — first-party
consensus beats a generic rescale. `raw-fantasypros-2026.txt` is the verbatim
paste; `auction-values.csv` is the parsed record outside the chat.

Not yet calibrated to *this specific league's* historical bidding (different
rooms bid differently). Pulling the historical Wells draft sheets Alex
mentioned (Google Drive) is the one step that would tune values to the room's
real tendencies rather than the broader market — still not done (Drive
search/read tools weren't available last session).

## Still open (needs Alex, not blocking use of the tool)

1. ~~8:30pm vs 8:30am draft-time mismatch~~ — resolved: 8:30pm–10pm PDT
   confirmed against the Zoom calendar invite. Yahoo's in-system time (8:30am)
   is still wrong and worth fixing in Yahoo so it stops confusing anyone.
2. Confirm **payout split percentages** ("usual splits" — never stated in a
   found email).
3. **Scoring: confirmed** (Yahoo screenshots) — PPR + stacking yardage
   bonuses (+5 at 300/400/500 pass, 100/200/300 rush, 100/200/300 rec). Tilts
   toward ceiling / elite + dual-threat QB; see `value-sources.md`.
   **Roster starters confirmed** (Yahoo): 1 QB / 2 RB / 2 WR / 1 TE / 2 W-R-T
   flex / 1 K / 1 D/ST = 10. Bench count still unconfirmed (sheets assume 7 →
   17 total). Tool defaults to 16 — set once bench is known. Budget $200/team.
4. Confirm **snake vs. auction** — last clear signal says auction, but never
   explicitly re-confirmed after Steph raised switching to snake.
5. ~~The **$0-flagged players**~~ — addressed in `value-sources.md`: ESPN
   prices all 7 at $1–8, so they're $1 fillers (Josh Jacobs the exception —
   bid him like a $1–5 flex). FantasyPros' $0 = "below print threshold," not
   "worthless."
6. FantasyPros config is still **not confirmed** — the raw paste carries no
   settings header. But it's markedly flatter than ESPN's known-10-team sheet
   (see `value-sources.md`), which is consistent with a smaller-league (8-team)
   build, so it's probably right for our table. Still no read on what *this
   room* actually pays (needs the historical Wells sheets).
