# Wells FF Draft Agent

Everything built so far for Alex's "All's Well That Ends Wells" 8-team, $100
Yahoo auction league — league knowledge + a live draft-day tool. Draft is
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

## Auction values: what's real vs. approximate

Google Drive's search/read tools weren't available this session (only
share/trash/update were exposed), so the historical draft-price sheets Alex
mentioned couldn't be pulled — that's the data that would actually calibrate
values to this specific league's bidding tendencies.

What's in `draft-board.html` instead: current (late Aug 2026) 12-team/$200
PPR auction consensus pulled via web search (RotoWire, Draft Sharks, Fantasy
Points), rescaled to 8-team/$100. The rescale isn't a flat 50% cut — shallower
leagues concentrate value at the top faster than they compress it at the
bottom, so elite tiers were rescaled more gently than mid/replacement tiers.
This is a **heuristic, not a calibration** — treat the ranges in the Bid Sheet
tab as a starting anchor and let the room's real bidding move you off them.

**To get an actually-calibrated sheet**: either fix Drive access so the past
draft sheets can be read, or paste/share the historical auction prices
directly and the values can be rebuilt from real data instead of rescaled
consensus.

## Still open (needs Alex, not blocking use of the tool)

1. Confirm the 8:30pm vs 8:30am draft-time mismatch in Yahoo.
2. Confirm payout split percentages ("usual splits" — never stated in a
   found email).
3. Confirm roster/scoring settings — the tool defaults to a 16-spot roster
   and $100 budget, both editable in the Board tab.
4. Confirm snake vs. auction stuck as auction (last clear signal says yes,
   but never explicitly re-confirmed after Steph raised switching to snake).
