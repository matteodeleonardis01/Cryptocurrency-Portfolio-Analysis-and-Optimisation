# Methodology and limitations

This is a revised and documented version of an earlier exploratory Python notebook. Original datasets are retrieved from Yahoo Finance at runtime. All old cell outputs were removed on publication because the assumptions have changed.

## 1. Data integrity

The research universe consists of BTC, ETH, BNB, SOL, XRP, LTC and LINK. Each daily OHLCV series is saved separately, and comparable variable-specific databases are merged by date. The principal close-price analysis excludes assets with less than 50% coverage, finds the shared first/last observed date, and uses only complete price dates; it does **not** backward-fill unobserved prices. Returns explicitly disable implicit forward-filling. This conservative approach can shorten the sample and is not immune to selection and survivorship biases.

## 2. Annualisation

For daily cryptocurrency series, arithmetic returns are annualised by multiplying by 365 and volatility by the square root of 365; hourly data use 365×24. A 52-observation convention is retained for weekly data. The risk-free rate is assumed to be zero. These choices differ from 252-day conventions commonly used for exchange-traded stocks. Historical compounded/CAGR returns and annualised arithmetic returns are different measures. Benchmark metrics using the same daily convention should **not** be interpreted as precise calendar-matched cross-market estimates, because equity and gold trading calendars differ.

## 3. Strategy timing

MA20/MA100 trend signals and rolling covariance/means are obtained at t−1, and target positions are applied to returns at t. Trend strategies use approximate equal-weight, max-Sharpe, minimum-variance, maximum-diversification or inverse-volatility formulations. Pseudo-inverse plus clipping is not an exact constrained quadratic-programming solution. Weights are nominally capped at 33%, with any remainder held in cash, and turnover carries a proportional fee of 0.1%. The cost calculation does not model intraday execution, spread, slippage or changes in portfolio weights through market movements.

## 4. Volatility overlay

The trailing 30-observation estimate of realised volatility is shifted by one observation before computing today's scale. The annual target is 30%, and leverage is capped at 1. The overlay de-risks into zero-yield cash; invested weights are not renormalised. This is a simplified exposure overlay, not a complete trade-level backtest.

## 5. Chronological split and selection bias

The original 75/25 split is applied to a MaxSharpe_TV series constructed by rolling past information. However, the research process does **not** establish that asset selection, model choice or hyperparameters were frozen before anyone examined the later period. We therefore describe the 75/25 results as a **chronological descriptive comparison**, *not* independently validated out-of-sample evidence. True validation would pre-register selection using only earlier data, apply it without revision to a previously unseen later sample, and audit all cross-validation and data-snooping decisions.

## 6. Macro analysis

Cryptocurrency strategy and equity/gold returns are matched on shared daily dates for descriptive correlations. GDP is quarterly, so quarterly GDP growth is compared only with compounded quarterly portfolio returns rather than spuriously repeating quarterly values over daily observations. US GDP releases are delayed and revised, so these correlations are not implementable real-time strategy inputs.

## Remaining limitations

Historical Yahoo Finance availability/revisions, survivorship, asset-specific liquidity, calendar differences, no separate price-impact/slippage model, and the exploratory selection process all limit external validity. This is a demonstrative data-science project, not an investment recommendation.
