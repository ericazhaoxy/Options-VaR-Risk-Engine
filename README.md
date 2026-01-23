# Options VaR Risk Engine

Quantitative risk analysis for an options butterfly spread. Simulates joint SPX–VIX market shocks and reports **1-day 95% Value at Risk (VaR)** via Monte Carlo + Black-Scholes repricing.

## Overview

A reproducible Python risk engine that simulates joint SPX–VIX scenarios via a Gaussian copula with Student-t marginals, re-prices an options butterfly spread using Black-Scholes, and estimates 1-day 95% Value at Risk (VaR) from the simulated PnL distribution.

## What’s inside

- Scenario generation: Gaussian copula + Student-t marginals (SPX, VIX)
- Repricing: Black-Scholes calls for a butterfly spread
- Risk metric: 1-day 95% VaR from simulated PnL

## Repo structure

- `notebooks/` — analysis notebook(s)
- `src/` — reusable Python modules (if extracted later)
- `results/` — figures/tables (PnL distribution, VaR summary)
- `assets/cover/` — project images
- `docs/` — report/notes/slides

## Key results

- 1-day 95% VaR (PnL): TBD
- 1-day 95% VaR (Return): TBD
- PnL distribution: see results/

## Method overview (high level)

1. Data & returns
   - Download SPX and VIX daily levels
   - Compute log returns for both series

2. Dependence + scenario generation
   - Transform marginals to allow heavy tails (Student-t style)
   - Couple SPX and VIX with a dependence structure (copula / correlation)
   - Generate Monte Carlo scenarios of 1-day shocks

3. Repricing + VaR
   - Reprice each option leg under simulated spot & vol shocks
   - Aggregate to portfolio value → PnL distribution
   - Report VaR as the 5th percentile loss (95% confidence)

## Notes & assumptions

- Pricing model: Black-Scholes (European call approximation)
- Risk factors: SPX level and VIX-derived volatility shock (as a proxy)
- Horizon: 1 trading day
- Metric: VaR at 95% confidence (historical calibration + Monte Carlo simulation)

## Limitations

- VIX is a proxy for implied volatility; mapping to option IV is simplified.
- Black-Scholes assumes lognormal dynamics and constant volatility within each scenario.
- Single-day horizon only; extensions could include multi-day simulation and stress testing.

## Project context

Originally developed as a team project (Portfolio Risk / Derivatives). This repo packages the work as a reproducible “risk engine” artifact for portfolio / interview use.

## Tech stack

Python · NumPy · pandas · SciPy · statsmodels · yfinance · matplotlib · seaborn

## Quickstart

### 1) Install dependencies

```bash
pip install -r requirements.txt
```

### 2) Run the analysis

- Open the notebook in notebooks/ (recommended), or
- Run the script in src/ (if/when extracted later)

Data is pulled from public sources (via yfinance) unless otherwise noted.
