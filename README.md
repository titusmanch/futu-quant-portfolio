# Systematic Strategy Research and Futu Paper Execution

A Python portfolio project exploring single-instrument US-equity backtesting, pre-trade controls and simulation-only broker execution.

**Repository purpose:** Public case study for portfolio review. Implementation source and its development history are private.

## Project overview

The project separates strategy logic, backtesting, risk assessment, broker interaction and audit logging. It is intended to make execution assumptions and research outputs inspectable.

## Implemented scope

- Close-based strategy signals evaluated using historical OHLC data.
- Next-bar-open backtest fills with configurable commission and adverse slippage.
- Strategy equity and buy-and-hold comparison.
- CAGR, Sharpe, Calmar and maximum drawdown reporting.
- Position-size, position-count, cash-buffer, daily-loss, market-hours, connectivity and kill-switch checks.
- Futu OpenD execution interface restricted to SIMULATE.
- SQLite decision, risk, submission and order-status records.
- Sequential duplicate replay detection after a submission is durably recorded.

## Architecture

Historical OHLC data → Strategy signals → Backtest → Metrics and reports

Execution signal → Risk assessment → Simulation broker interface → Order status

Decision and execution events → SQLite audit trail

## Verification and evidence

Automated checks cover next-open fills, risk gates and duplicate replay handling. A locally prepared revision passed 12 tests and produced an offline mock execution trace in which two identical decisions resulted in one mock submission.

These are local test results. They do not establish a live brokerage connection or real investment performance. Included/generated demonstration prices are synthetic.

## Design limitations

- The backtester is single-instrument; multi-asset portfolio accounting is outside the current scope.
- Fill assumptions simplify spreads, market impact, partial fills and fees.
- Sequential replay detection is not an exactly-once guarantee across process crashes or concurrent workers.
- Exchange holidays, early closes, outstanding-order exposure and reconnect reconciliation require further work.
- Authenticated Futu simulation execution needs separate verification.
- No live-money trading or production availability claim is made.

## Technology

Python · pandas · NumPy · matplotlib · SQLite · pytest · Futu OpenAPI

## Interview discussion

The project supports discussion of time-series causality, next-bar execution assumptions, transaction costs, modular broker interfaces, pre-trade checks and auditable execution records.

Implementation can be discussed during an interview. This public case study does not distribute the source code, account information or credentials.