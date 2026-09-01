# Wells FF Draft Agent

Everything built so far for Alex's "All's Well That Ends Wells" 8-team Yahoo
auction league ($100 real-money buy-in, $200/team auction budget — see
`league-notes.md`, these are two different numbers) — league knowledge + a
live draft-day tool. Draft is
Tuesday Sept 1, 2026, 8:30pm PDT (see `league-notes.md` for a Yahoo time
mismatch that needs checking).

## What's here

- **`league-notes.md`** — everything pulled from Alex's Gmail: owners, buy-in,
  2026 rule changes, league lore, and an explicit list of what's still
  unconfirmed (payout split, roster/scoring settings, snake-vs-auction final
  call).
- **`draft-board.html`** — a single-page, no-build draft-day tool. Also
  published as a Claude Artifact for use on a phone/laptop during the Zoom
  draft. Three views:
  - **Board** — all 8 teams, remaining budget, roster spots filled, and a
    live **max bid** figure (remaining budget minus $1 per roster spot still
    needed) so nobody accidentally prices themselves out of filling a roster.
  - **Bid Sheet** — an editable, searchable auction value cheat sheet (see
    methodology note below), with a one-tap "Log" that jumps to the pick form.
  - **Log Pick** — records player/position/price/team; updates every team's
    budget and the bid sheet instantly. Autosaves to the browser via
    localStorage (single-device only — it doesn't sync across phones/laptops,
    so pick one device to be the source of truth during the draft).

## One agent, not two

Weighed a separate "league rules" agent and "draft-day" agent against a
single one — going with **one**. The two modes (answering rules/payout
questions beforehand, calling out values and tracking budget live during the
draft) share the same underlying knowledge (owners, buy-in, history) and
there's no real handoff moment between them — it's one conversation that
gets faster and more tactical once the clock starts. Splitting it would just
mean re-explaining league context to a second agent. `league-notes.md` is the
shared knowledge base either way.

## Auction values: source

**Update (Aug 31):** the Bid Sheet now runs on real data, not the earlier
rescaled estimate. Alex pasted the full FantasyPros 2026 auction values list
(361 players, 8-team/$200 PPR, already in his exact format) and it's fully
loaded into `draft-board.html` — see `raw-fantasypros-2026.txt` (verbatim
source as pasted) and `auction-values.csv` (parsed: rank, name, team, pos,
injury status, value) for the durable record outside the chat. This replaced
the earlier rescaled-from-12-team heuristic entirely — first-party consensus
beats a generic rescale.

It's still not calibrated to *this specific league's* historical bidding
(different rooms bid differently), but it's real market data rather than an
estimate. Google Drive's search/read tools weren't available this session
(only share/trash/update were exposed), so the historical Wells draft sheets
Alex mentioned still haven't been pulled — that remains the one step that
would tune this to the room's actual tendencies rather than the broader
market.

## Still open (needs Alex, not blocking use of the tool)

1. ~~8:30pm vs 8:30am draft-time mismatch~~ — resolved: 8:30pm–10pm PDT
   confirmed against the Zoom calendar invite. Yahoo's in-system time (8:30am)
   is still wrong and worth fixing so it stops confusing anyone who checks
   Yahoo directly.
2. Confirm payout split percentages ("usual splits" — never stated in a
   found email).
3. Confirm roster/scoring settings — the tool defaults to a 16-spot roster,
   editable in the Board tab. Budget is confirmed $200/team.
4. Confirm snake vs. auction stuck as auction (last clear signal says yes,
   but never explicitly re-confirmed after Steph raised switching to snake).
