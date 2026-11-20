# Decision log

Status values:
- **Accepted** — the owner decided this explicitly.
- **Provisional** — the owner decided this for planning; it may change after investigation.
- **Proposed** — suggested by the brief or by Claude; not yet agreed.
- **Open** — needs a decision.

Significant decisions will get their own record (`NNNN-title.md`) with alternatives and consequences when they are made. The architecture is **not approved**.

## Owner decisions

| ID | Date | Status | Decision | Notes |
| --- | --- | --- | --- | --- |
| U1 | 2026-11-20 | Provisional | Investigate **Upstox first** for live and historical data; Zerodha is the alternative. | Select only after checking the official docs **and** actual account access. |
| U2 | 2026-11-20 | Accepted | Weekend budget is **3–5 h total**, giving 8–10 h/week. | |
| U3 | 2026-11-20 | Provisional | Initial strategy candidate: **opening-range breakout + relative-volume filter**. | Exact rules are open (Q2). |
| U4 | 2026-11-20 | Proposed | Operating budget **cap ₹3,000/month** (VM + data). | Planning figure only; **it does not authorise any purchase.** |
| U5 | 2026-11-20 | Accepted | Status UI = **small read-only HTTP interface**. Full website/app deferred. | Scope open (Q6). |
| U6 | 2026-11-20 | Accepted | Deploy early enough to observe **several full market sessions** before 30 Dec. | See schedule proposal P1. |
| U7 | 2026-11-20 | Accepted | Milestone trades **intraday long-only**. The domain model must represent **LONG and SHORT** so short selling can be added later without redesign. | Short trading is a later epic. Claude recommends not attempting it in December (see P2). |

## Requirements stated by the owner (2026-11-20)

These are accepted requirements. The owner will fold them into `docs/requirements.md` in the first draft.

- **R1 Loose coupling.** Clear component contracts and explicit dependencies. Broker SDK objects, authentication and message formats stay inside adapters. Strategy, risk and portfolio logic use our own domain types. Replacing Zerodha with Upstox should mainly require changes to the adapter, configuration and integration tests.
- **R2 Abstraction has costs.** Discuss the costs of abstraction as well as its benefits. Don't create an interface for every class. Introduce boundaries around genuine external dependencies or components we reasonably expect to replace.
- **R3 Storage architecture is a design topic.** Compare embedded storage (SQLite, H2), a database service on the same VM, and a managed database on persistence, concurrency, crash recovery, backups, schema migrations, retention and operational cost, not on subscription price alone.
- **R4 Separate storage needs.** Order/position records, configuration history, market-data recordings, research datasets and application logs may need different formats and retention policies.
- **R5 Storage behind contracts.** Business logic must not depend on database-specific queries. A database replacement may still need migrations and operational changes; never promise a configuration-only replacement.

## Proposals (not agreed)

| ID | Source | Proposal |
| --- | --- | --- |
| B1 | Brief | One deployable process with internal modules; no extra services until a requirement justifies them. |
| B2 | Brief | Paper and live share domain contracts but keep credentials, journals and account state separate. |
| B3 | Brief | Typed, validated configuration classified as runtime / safe-boundary / restart-only. |
| B4 | Brief | About 51 h phase plan: scope → paper core → live data → deploy → observe. |
| P1 | Claude, 2026-11-20 | **Schedule.** Keep **deploy by Tue 22 Dec** as the target, so that the trading sessions on 22, 23, 24, 28, 29 and 30 Dec are observable (25 Dec is an NSE holiday). Allow an **observation and hardening buffer up to about 9 Jan 2027** if needed. Add **no new epics** inside the buffer, because filling a buffer with features removes the buffer. Report any shortfall honestly. *Awaiting the owner's confirmation.* |
| P2 | Claude, 2026-11-20 | **Shorts.** In December, model `Side {LONG, SHORT}` in domain types and P&L sign handling only. Risk rejects SHORT entries by configuration. Real short support (exit direction, stop direction, broker product rules, auto square-off) is a separate epic after the milestone. |

## Open questions

| ID | Question | Blocks |
| --- | --- | --- |
| Q1 | Upstox: live feed (WebSocket) symbol limits, whether it gives bid/ask depth or only LTP, cost, login and token expiry, historical intraday candles for replay. | Everything live. **Highest priority.** |
| Q2 | Exact ORB + relative-volume rules: opening-range length, entry trigger, volume baseline, stop/target/time exit, sizing, costs, slippage. | Strategy spec |
| Q3 | Observation sessions and deployment date (see P1). | Schedule |
| Q4 | VM provider and region within the U4 budget, including the data cost. | Deployment |
| Q5 | Storage choice per data category (R3/R4). | Persistence |
| Q6 | Content of the read-only HTTP status interface. | Ops |
| Q7 | Session end per instrument. From 3 Aug 2026, **F&O stocks** have continuous trading until **15:15**, then a Closing Auction Session from **15:15 to 15:35**. Non-F&O stocks trade continuously until 15:30. Square-off and "no new entries" times must be per instrument. | Strategy spec, session handling |
| Q8 | Paper fill model: fill at the ask (buy) or bid (sell) plus slippage, or at LTP plus a buffer if the feed has no depth? Depends on Q1. | Paper execution |
