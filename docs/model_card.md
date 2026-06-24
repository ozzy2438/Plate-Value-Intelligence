# Model Card

## Model Purpose

The valuation model produces an explainable benchmark for DVLA personalised-registration hammer prices.

## Intended Use

- pricing benchmark
- portfolio prioritisation
- premium-screening support
- commercial review routing

## Not Intended For

- fully autonomous pricing
- guaranteed sale-price prediction
- causal commercial-uplift estimation
- customer-level targeting
- live dynamic pricing without internal calibration

## Training Data

- Training events: B270-B276
- Validation event: B277
- Final test event: B278
- Modelling base: 2025 core auction dataset only

Historical Regtransfers material is not merged into training because it is partial, selected, and high-value biased.

## Target

`log_hammer_price`

The model is trained on the log-transformed hammer price and evaluated on both log and GBP scales.

## Primary Model

Random Forest regressor.

## Challenger Model

HistGradientBoosting regressor.

## Metrics

| Model | Dataset | MAE | Median absolute error | RMSE | Log RMSE |
|---|---|---:|---:|---:|---:|
| Ridge regression | B277 validation | GBP 1,259 | GBP 644 | GBP 2,396 | 0.767 |
| Random Forest | B277 validation | GBP 1,230 | GBP 639 | GBP 2,348 | 0.753 |
| HistGradientBoosting | B277 validation | GBP 1,229 | GBP 650 | GBP 2,352 | 0.755 |
| Final Random Forest | B278 final test | GBP 1,248 | GBP 621 | GBP 2,551 | 0.755 |

Final B278 top-decile premium recall was approximately 55.28%.

## Model Selection Rationale

HistGradientBoosting had a very small validation MAE advantage. Random Forest was selected because it offered a better overall trade-off across premium capture, RMSE, median error, and feature-level explainability.

## Known Weaknesses

- premium-tail underprediction
- missing semantic and name-value signals
- missing brand and cultural signals
- no bidder-side demand signals
- data limited to a single calendar year
- no verified unsold or withdrawn outcome field

## Governance

- leakage exclusions for target-derived fields
- event-based split instead of random split
- final holdout discipline
- human review path for specialist assets
- feature-importance reporting
- reproducible exports under `reports/`
