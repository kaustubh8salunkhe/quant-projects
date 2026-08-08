# Quantitative Cross-Sectional Momentum Engine (NSE)

This repository houses an event-driven quantitative backtesting engine built upon the `Backtrader` architecture. The suite rigorously evaluates the empirical persistence of the 12-1 momentum anomaly within the National Stock Exchange (NSE) large-cap universe, benchmarking absolute and risk-adjusted returns against the Nifty 50 index across a highly volatile 2019–2024 test window.

By migrating from static array-based analysis (e.g., pure Pandas loops) to an event-driven execution environment, this architecture accurately simulates the frictional realities and structural constraints of institutional portfolio management.

## Architectural Integrity & Risk Parameters

The trading logic is heavily constrained by strict risk-management and execution protocols to prioritize capital preservation and out-of-sample viability over absolute return optimization:

* **Cross-Sectional Signal Generation:** Ranks a 50-stock high-liquidity NSE universe based on a 12-month trailing return profile, excluding the most recent one-month period to mitigate short-term mean reversion.
* **Frictional Cost Modeling:** The broker execution engine enforces a strict 10-basis-point (bps) commission model to account for slippage, taxes, and exchange fees during monthly rebalancing.
* **Regime Filtering (200-SMA):** The algorithm refuses to allocate capital to equities trading beneath their 200-day Simple Moving Average, structurally evading asset-specific downtrends.
* **Dynamic Circuit Breaker & Cooldown:** Engineered with a hard 15% maximum drawdown circuit breaker. Upon triggering, the algorithm liquidates and enforces a 3-month cash cooldown, allowing macroeconomic volatility (VIX proxy) to subside before re-entering the market.

## Empirical Achievements (2019-2024)

Despite the aggressive frictional costs and cash-heavy cooldown periods, the strategy produced a highly defensible risk-adjusted return profile.

| Metric | Adaptive 12-1 Momentum | Nifty 50 Benchmark (^NSEI) |
| :--- | :--- | :--- |
| **Annualized Sharpe Ratio** | **0.38** | 0.53 |
| **Maximum Drawdown** | **22.47%** | > 35.00% |
| **Annualized Return** | **10.45%** | N/A |
| **Frictional Cost** | 10 bps per trade | 0 bps (Theoretical) |

## Forensic Analysis: The March 2020 Liquidity Crisis

A critical component of this backtest is its realistic behavior during the March 2020 COVID-19 pandemic crash. 

**Observation:** The strategy sustained a 22.47% realized drawdown—exceeding the 15% hard-coded limit. 
**Diagnosis:** The algorithm correctly generated liquidation orders at the 15% threshold. However, due to extreme overnight liquidity gap-downs, the event-driven broker executed at the next available market price (simulating real-world slippage), finalizing the drawdown at 22.47%.
**Inference:** This confirms the architectural superiority of event-driven backtesting. Static array logic would have executed the stop-loss exactly at 15%, masking the catastrophic reality of overnight gap risk. Following liquidation, the 3-month cooldown safely isolated the portfolio from the remainder of the crash, demonstrating sound institutional risk management over curve-fitted return chasing.

## Technical Stack
* **Execution Engine:** `Backtrader`
* **Data Ingestion:** `yfinance`
* **Quantitative Libraries:** `Pandas`, `NumPy`
