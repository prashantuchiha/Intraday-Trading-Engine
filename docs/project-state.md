# Project state

_Last updated: 2026-11-20 (session 1, project chat)._

## Where we are

- **Phase:** scope and requirements (brief phase 1, 20–26 Nov).
- **Code:** none. **Architecture:** under discussion, **not approved**.
- **Repo:** docs scaffold only (this branch).
- Decisions so far: `docs/decisions/decision-log.md` (U1–U7, R1–R5, proposals P1–P2, open Q1–Q8).

## Design discussion progress

| # | Question | Status |
| --- | --- | --- |
| DQ1 | Steps from a price update to a recorded paper position | Attempted twice. The owner separated entry from exit management. Gaps: risk check, paper execution, persistence. |
| DQ2 | (a) What to check before a paper buy; (b) who decides the paper fill price | Attempted. (a) mixed up ranking/allocation with risk checks; (b) thought the broker fills paper orders. Corrected: **our paper execution simulator** decides the fill, conservatively. |
| DQ3 | Two signals competing for the same cash at the same moment | **Asked, waiting for answer.** |

## Calendar facts (verified 2026-11-20)

- NSE trading holidays left in 2026: **Tue 24 Nov** (Guru Nanak Jayanti) and **Fri 25 Dec** (Christmas).
- Normal session 09:15–15:30, with pre-open 09:00–09:15. **F&O stocks:** continuous trading ends at 15:15, followed by the closing auction from 15:15 to 15:35 (from 3 Aug 2026).

## Next task (≤ 1 hour)

**Upstox access check (Q1).** Using only the official Upstox developer docs and your own account, write `docs/research/broker-access.md` with a short table answering:

1. How to get API access, and the cost.
2. How login works and when the access token expires (daily?).
3. The live market-data feed: protocol, max instruments per connection, and whether it gives LTP only or bid/ask depth.
4. Historical intraday candles: which intervals and how far back.
5. Rate limits that matter for 50 stocks.
6. Anything that blocks us.

**Done when:** each row has an answer **with a link** to the official page, or says "not found". Note anything you could not verify with your own account. If you have time, add a Zerodha Kite Connect column.

## Owner tasks queued

- Read Zerodha Varsity Module 1, ch. 6 (§6.2–6.4) and explain bid, ask and last traded price in 3–4 lines (about 45 min).
- First draft of `docs/requirements.md` (after Q1, so that the data limits are known).
