# Quantitative Finance Portfolio

A curated repository of quantitative research, algorithmic trading architectures, and stochastic financial modeling projects. 

## Projects Directory

* **[01. Cross-Sectional Momentum & Stochastic Derivatives Pricing](./Momentum%20Options%20Pricer/)**
  * *Overview:* A bifurcated quantitative research engine. Features a discrete Pandas-based momentum factor evaluation alongside a 50,000-path Monte Carlo options pricer integrated with closed-form Black-Scholes Greeks.
  * *Tech Stack:* Python, Pandas, SciPy, Matplotlib (3D Surface Modeling), yfinance.

* **[02. Institutional Event-Driven Momentum Engine](./Institutional%20Event-Driven%20Momentum%20Engine/)**
  * *Overview:* An advanced, event-driven algorithmic backtester executing on the Nifty 50 universe. Prioritizes capital preservation and out-of-sample viability by enforcing strict 10-bps frictional costs, 200-day SMA regime filtering, and dynamic drawdown circuit breakers. 
  * *Tech Stack:* Python, Backtrader, Pandas, NumPy, yfinance.

## Ongoing Research
* *Algorithmic Execution:* Transitioning static arrays to event-driven architectures to accurately simulate market microstructure, slippage, and overnight gap risk.
* *Derivatives Pricing:* Variance reduction techniques in stochastic path generation and volatility surface modeling.
