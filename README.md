# TradingOS

TradingOS is the umbrella for personal, research-first Indian-market analysis. It must remain paper/research-only until live data quality, realistic costs, safety controls and out-of-sample validation have been independently demonstrated.

## Current state

- **Status:** repository foundation only; no application implementation yet.
- **Existing research module:** [NIFTY AI Options Signal System](https://github.com/harishmudgonda-611/NIFTY-AI-Options-Signal-System-), maintained separately.
- **Scope:** NIFTY, BANK NIFTY and eligible NSE stocks; later adapters may cover other markets.
- **Capital assumption:** small account (reference ₹4,000; configurable).
- **Execution:** no broker login, no real orders, no autonomous trading.
- **Options:** CE/PE trade-entry signals remain disabled until timestamped option-chain data includes expiry, strike, bid/ask, LTP, volume, OI, lot size and source provenance.

## Architecture direction

1. **Market data adapters** — source metadata, timestamps, staleness detection, schema validation and explicit data-quality scores.
2. **Research engine** — technical indicators, regime classification, volatility/liquidity analysis and candidate ranking. Signals are hypotheses, not instructions.
3. **Options research** — contract selection only from verified option-chain data; no premium inferred from underlying index points.
4. **Backtesting** — event-driven replay, realistic slippage, brokerage, STT, exchange fees, GST, stamp duty and expiry/lot-size rules.
5. **Paper portfolio** — simulated entries/exits, position sizing, risk limits and journal; isolated from broker APIs.
6. **Validation** — chronological train/test split, walk-forward tests, transaction-cost sensitivity, Monte Carlo, drawdown and minimum sample-size gates.
7. **Mobile research dashboard** — watchlists, data-quality warnings, candidate explanations, paper journal and exportable reports.

## Hard safety rules

- Never place orders or connect to a funded brokerage account.
- Never label delayed/unofficial data as live.
- Reject stale, missing, crossed or inconsistent quotes.
- No guaranteed-return, win-rate or profit claims.
- A bullish/bearish underlying view is not an options entry.
- Small-account options are often infeasible after lot size, premium and costs; the system must show **NO TRADE** rather than force a setup.
- Store no broker credentials or secrets in source control.

## Roadmap

- [ ] Repository governance, CI and dependency/security checks
- [ ] Read-only market-data contracts and validation fixtures
- [ ] Reusable indicator and regime modules
- [ ] Deterministic backtest harness with cost model
- [ ] Paper-trading ledger and risk guardrails
- [ ] Mobile-first dashboard and journal
- [ ] Independent strategy validation and release gate

## Definition of done

A module is not considered complete until tests pass, data-source limitations are documented, outputs are reproducible, safety rules are enforced, and no real-money execution path exists.
