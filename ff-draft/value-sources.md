# Auction value sources

Two independent auction-value sets are now in the repo. The draft tool
(`draft-board.html`) runs on **FantasyPros**; ESPN is a cross-check.

| Source | File(s) | League config | Players | Notes |
|---|---|---|---|---|
| **FantasyPros 2026** (primary) | `auction-values.csv`, `raw-fantasypros-2026.txt` | 8-team / $200 PPR *(assumed — the paste has no settings header)* | 361 | Pasted by Alex in his exact format. Powers the Bid Sheet. |
| **ESPN 2026 Draft Kit** (cross-check) | `espn-values.csv`, `espn-draft-kit-2026-ppr.pdf` | **10-team** / $200 PPR | 280 | "PPR League Cheat Sheet," last updated Aug 31 2026. Roster: 1 QB / 2 RB / 2 WR / 1 TE / 1 FLEX / 1 K / 1 D/ST / 7 bench (15 total). Decimal scoring, 1 PPR. |

## Reading the two together

**They disagree systematically, and it's not noise:** FantasyPros is much
*flatter* — it prices elite/second-tier RBs and mid WRs well below ESPN, and
pays *up* for elite QB relative to ESPN.

- This is the expected direction for **8-team vs 10-team**. With only 8 teams ×
  15 spots (~120 rostered), replacement level is very high — a startable RB is
  a $1 bid or a waiver add — so the scarcity premium on studs collapses and
  the middle compresses toward $1. ESPN's 10-team sheet has scarcer starters,
  so its top end costs more.
- Net: **trust FantasyPros for the absolute dollar figure at our table.** Use
  ESPN to sanity-check *rank/relative* value — especially RB2/RB3 types where
  FantasyPros looks aggressively cheap (if the room bids them up toward ESPN
  levels, that's normal, not a steal).
- The two sheets also reflect different roster philosophies (FantasyPros:
  spend on QB; ESPN: punt QB). Our actual room's behavior is the only real
  tiebreaker — see the still-missing historical Wells draft sheets.

## The 7 "$0 in FantasyPros" flags — resolved enough to bid

`value-comparison.html` flagged 7 players showing `$0` in FantasyPros despite
clearly being rostered everywhere. ESPN prices all 7 above zero:

| Player | FantasyPros | ESPN (10-team) | Read for our 8-team table |
|---|---|---|---|
| Josh Jacobs (RB) | $0 (rank 123) | **$8** (RB25) | The real one. Bid him as a genuine **$1–5 flex**, not a $0. FP rank 123 looks stale/low. |
| Jordan Addison (WR) | $0 (rank 145) | $3 (WR42) | $1–2 bench WR. Suspended start of season — that's the FP $0. |
| Xavier Worthy (WR) | $0 (rank 146) | $2 (WR46) | $1 bench WR. |
| Mark Andrews (TE) | $0 (rank 121) | $2 (TE13) | $1 streaming TE. |
| Jordan Mason (RB) | $0 (rank 150) | $1 (RB40) | $1 handcuff. |
| Kyler Murray (QB) | $0 (rank 142) | $1 (QB16) | $1 QB2. |
| Jared Goff (QB) | $0 (rank 171) | $1 (QB18) | $1 QB2. |

**Conclusion:** FantasyPros' `$0` here means "below our printed price
threshold," not "worthless." Only Josh Jacobs needs a mental correction at the
table (bid him like a $1–5 flex). The rest are $1 end-of-roster guys either
way. Same pattern hits a cluster of FP rank ~118–141 players ESPN has at $3–4
(Herbert, Stafford, Bo Nix, Jayden Reed) — all `$1` fillers, not zeros.

## Biggest FP vs ESPN gaps to keep in mind live

Among FantasyPros' top ~170, where the two sheets diverge by ≥ $8 (FP minus
ESPN — all negative, i.e. FP cheaper):

| Player | Pos | FP | ESPN | Δ |
|---|---|---|---|---|
| Jeremiyah Love | RB | $21 | $45 | −24 (FP tags INJ) |
| James Cook III | RB | $27 | $46 | −19 |
| Saquon Barkley | RB | $24 | $42 | −18 |
| CeeDee Lamb | WR | $35 | $51 | −16 |
| Ashton Jeanty | RB | $23 | $38 | −15 (DTD) |
| Justin Jefferson | WR | $35 | $50 | −15 |
| Kenneth Walker III | RB | $22 | $37 | −15 (DTD) |
| Breece Hall | RB | $18 | $32 | −14 (INJ) |
| De'Von Achane | RB | $34 | $48 | −14 |
| Javonte Williams | RB | $14 | $27 | −13 |
| Derrick Henry | RB | $28 | $40 | −12 |
| Jonathan Taylor | RB | $40 | $52 | −12 |

And the one gap the other way: **Josh Allen QB $31 FP vs $22 ESPN (+9)** —
FantasyPros wants you to pay up for the top QB; ESPN doesn't.

If the room bids these RBs toward the ESPN numbers, that is the market
correcting FantasyPros' 8-team compression — don't treat it as other owners
overpaying.

## League scoring bonuses — how they tilt values

Confirmed Sept 1: stacking yardage bonuses (+5 at each of 300/400/500 pass,
100/200/300 rush, 100/200/300 rec). Neither FantasyPros nor ESPN bakes these
in, so adjust at the table:

- **Pay up for elite QB, especially dual-threat.** A 300+ yd passing game is
  common for the top tier and worth +5 to +15; a rushing QB can also clip the
  +5 rushing bonus. Josh Allen (pass **and** rush bonus equity), Lamar, Jayden
  Daniels, Burrow, Mahomes gain the most. FantasyPros already has Allen at $31
  (vs ESPN $22) — in *this* scoring that's fair, maybe light. Expect the QB
  tier to clear above sheet value; be willing to.
- **Favor ceiling over floor at RB/WR.** The 100-yд bonus (+5 on a game
  that's already ~10 pts base) rewards boom weeks and clear alphas, not
  steady-volume PPR grinders. Between two similar-priced players, take the
  explosive one / the undisputed target hog.
- **Reinforces RB-heavy and Studs.** Bell-cow backs who hit 100+ get the
  bonus; committee backs don't. Widens the gap between true RB1s and the
  replacement pool — which is already wide in an 8-team league.
- **TE is mostly untouched** (few TEs hit 100 rec yds regularly) — stays a
  punt unless you land McBride/Bowers.
- **Cheap dual-threat QB2** (Fields, Daniels-type in a good matchup) is a
  live streaming edge for the rushing bonus.

Net: not league-warping, but a real thematic tilt toward explosiveness and
elite QB. Treat sheet QB prices as a floor.

## Still would sharpen this

The historical Wells draft sheets (Google Drive) remain the missing piece —
they'd show what *this room* actually pays, which is the only thing that
settles the FP-vs-ESPN question for our table.
