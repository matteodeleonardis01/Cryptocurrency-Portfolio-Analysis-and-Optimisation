# Cryptocurrency Portfolio Analysis and Optimisation

**Python research project by Matteo De Leonardis** — financial data collection, quality control, database compilation, time-series visualisation and exploratory portfolio backtesting. The notebook uses a seven-asset cryptocurrency universe, selected market benchmarks, and a separately matched quarterly macroeconomic comparison.

## What the notebook demonstrates

- **Collect and validate data:** download five years of Yahoo Finance OHLCV records for seven cryptocurrencies, standardise timestamps and fields, write per-asset CSVs and compile combined databases.
- **Explore:** calculate returns, summary statistics, Sharpe/Sortino, drawdowns, VaR/CVaR and correlations; visualise prices, distributions and time-varying allocation.
- **Model:** construct MA20/MA100 trend-following portfolio heuristics (equal weight, max Sharpe, minimum variance, max diversification and inverse-volatility weights), including turnover costs and a lagged target-volatility overlay.
- **Compare:** inspect benchmark returns, daily cross-market correlations, quarterly GDP comparisons and a chronological 75/25 performance split.

## Quick start

1. Open `crypto_portfolio_analysis.ipynb` in [Google Colab](https://colab.research.google.com/) or Jupyter with Python 3.10+.
2. Install dependencies in a terminal with `pip install -r requirements.txt` (or run `!pip install ...` within Colab).
3. Run cells in order. The first part downloads public data into `data/`, which is excluded from Git. Internet access is required, and live data may differ from the historical demonstration.

## Files

- [`crypto_portfolio_analysis.ipynb`](crypto_portfolio_analysis.ipynb): annotated Python notebook.
- [`METHODOLOGY.md`](METHODOLOGY.md): assumptions, changes relative to the original exploratory notebook and methodological limitations.
- `requirements.txt`: Python dependencies.
- `.gitignore`: excludes downloaded/generated data and local environment files.

## Scientific transparency

This public revision eliminates backward-filled pre-history, switches crypto-daily annualisation to 365, lags the realised-volatility signal used for today's exposure and correctly distinguishes a chronological **descriptive split** from a genuinely untouched out-of-sample test. It also prevents quarterly GDP observations from being interpreted as daily independent data. Previous saved notebook outputs were cleared because the revised methodology changes results; **no current return/performance claim is made without rerunning the notebook**.

The project is educational and exploratory. It is not investment advice. See [`METHODOLOGY.md`](METHODOLOGY.md) for important remaining biases and execution-model simplifications.
