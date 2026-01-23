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
- `assets/cover/` — project images
- `docs/` — report/notes
