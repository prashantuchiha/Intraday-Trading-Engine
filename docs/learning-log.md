# Learning log

Records what the owner has **demonstrated**, not what was explained to him. "Explained" does not mean "understood".

## Market basics

| Date | Topic | Evidence | Status |
| --- | --- | --- | --- |
| 2026-11-20 | Order matching | Described correctly in his own words: a buy trades when a seller is available at an acceptable price. | Basic understanding |
| 2026-11-20 | Exchange vs broker vs our system | Thought our system must handle the market's millions of trades. Explained: the exchange matches orders, and we subscribe to about 50 symbols. | Explained, **not yet checked** |
| 2026-11-20 | Data vs reasons | Inferred news or insider trading from demand. Explained: the system sees only price, volume and time. | Explained, not yet checked |
| 2026-11-20 | Market hours | Believed prices change continuously outside session hours. Corrected with the NSE session times and the F&O closing auction. | Explained, not yet checked |
| 2026-11-20 | Paper fills | Thought the broker fills paper orders. Explained: our simulator decides the fill, with bid/ask, slippage and costs. | Explained, not yet checked |
| — | Bid, ask, spread, LTP | Reading task assigned. | Pending |

## Design thinking

| Date | Topic | Evidence | Status |
| --- | --- | --- | --- |
| 2026-11-20 | Entry vs exit responsibility | Proposed, unprompted, a separate component that monitors open positions and manages exits. | **Demonstrated** |
| 2026-11-20 | Risk check vs strategy ranking | Mixed up "which stock is best" (strategy/allocation) with "is this order allowed" (risk). | Gap |
| 2026-11-20 | Scope discipline | First answer put ML into the milestone path. | Gap: keep the baseline rules-only |

## Brief scenario checks

- Concurrent signals competing for cash: asked as DQ3, awaiting answer.
- Recovery after an order-submission timeout: not yet asked.
