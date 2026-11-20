# Resources

Only resources that answer a current question. "Verified" means Claude found and checked the page on the given date; it does not mean every claim inside it is endorsed.

## Market basics

- **Zerodha Varsity, Module 1 "Introduction to Stock Markets", ch. 6** — https://zerodha.com/varsity/module/introduction-to-stock-markets/ (verified to exist 2026-11-20).
  - *Question it answers:* what the stock market is, what moves a stock, and how a trade happens.
  - *Read:* §6.2–6.4.
  - *Then:* explain bid, ask and LTP in 3–4 lines in `docs/learning-log.md`.

## Exchange rules

- **NSE pre-open session** — https://www.nseindia.com/static/products-services/equity-market-pre-open (verified 2026-11-20). How the opening price is discovered. This matters for the opening range.
- **NSE Closing Auction Session (CAS)** — SOP circular NSE/CMTR/73362 (18 Mar 2026): https://nsearchives.nseindia.com/content/circulars/CMTR73362.pdf. FAQ: https://www.nseindia.com/static/trade/continuous-markets-FAQs (found 2026-11-20, not yet read in full). It defines session end for F&O stocks (Q7).
- **NSE 2026 trading holidays** — the official list is on nseindia.com under "Market Timings & Holidays". Remaining 2026 holidays were cross-checked on 2026-11-20: 24 Nov and 25 Dec.

## Strategy research (read critically)

- **Zarattini & Aziz, "Can Day Trading Really Be Profitable?"** (SSRN 4416622) — https://papers.ssrn.com/abstract=4416622. A 5-minute ORB study.
- **Zarattini, Barbon & Aziz, "A Profitable Day Trading Strategy For The U.S. Equity Market"** (SSRN 4729284) — https://papers.ssrn.com/sol3/papers.cfm?abstract_id=4729284. ORB on "stocks in play", filtered by relative volume. This is closest to U3.
- *Transfer caveats:* both use **US** markets and the period 2016–2023. They allow shorts (we are long-only). Their costs and slippage differ from Indian intraday costs (STT, stamp duty, GST, brokerage). An independent replication on index CFDs reported that the gross edge disappeared after costs. Treat them as a source of **rule ideas**, not proof that the strategy will work for us.
