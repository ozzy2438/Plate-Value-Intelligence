# Plate Value Intelligence

Plate Value Intelligence is a portfolio data project built around UK DVLA personalised registration auction results.

The current repo focus is not data collection. It is structured around:

- auditing auction data quality
- building a governed modelling dataset
- engineering explainable plate features
- building valuation models
- converting model outputs into premium-asset, pricing, and auction-strategy decision support

## Repository Contents

- [01_data_audit_and_governance.ipynb](01_data_audit_and_governance.ipynb)
  - audits the 2025 auction dataset
  - checks completeness, duplicates, and event coverage
  - produces governed processed outputs
- [02_plate_feature_engineering.ipynb](02_plate_feature_engineering.ipynb)
  - derives interpretable plate-level features
  - prepares valuation-oriented feature tables
- [03_exploratory_pricing_analysis.ipynb](03_exploratory_pricing_analysis.ipynb)
  - explores observed pricing patterns across events, formats, numeric bands, and scarcity signals
  - produces stakeholder-friendly pricing summary reports
- [04_valuation_baseline_models.ipynb](04_valuation_baseline_models.ipynb)
  - establishes median, plate-length, and Ridge regression valuation baselines
  - validates the event-based train / validation / test design
- [05_valuation_tree_models.ipynb](05_valuation_tree_models.ipynb)
  - evaluates tree-based valuation models against baseline performance
  - produces final holdout test metrics, feature importance, and model artifacts
- [06_premium_collectible_asset_detection.ipynb](06_premium_collectible_asset_detection.ipynb)
  - turns valuation and structural rarity signals into premium, collectible, and specialist-review decisions
  - produces portfolio-level asset-decision reports
- [07_pricing_and_auction_strategy_simulation.ipynb](07_pricing_and_auction_strategy_simulation.ipynb)
  - converts holdout valuation predictions and collectibility decisions into transparent fixed-price, auction, premium-showcase, and specialist-review recommendations
  - simulates indicative pricing and reserve-policy scenarios for retrospective decision support
  - does not claim to be a live dynamic pricing optimisation engine
- [data/processed/all_sources_governed_2025.csv](data/processed/all_sources_governed_2025.csv)
  - governed dataset with quality and governance fields
- [data/processed/valuation_core_2025.csv](data/processed/valuation_core_2025.csv)
  - cleaned core dataset for modelling and feature work
- [data/processed/plate_features_2025.csv](data/processed/plate_features_2025.csv)
  - valuation-ready feature table derived from the core 2025 dataset
- [reports/](reports)
  - summary outputs for coverage, data quality, price quantiles, and exploratory pricing signals
- [sources/](sources)
  - supporting source indexes and historical reference files

## Project Positioning

This project is being developed as a job application portfolio piece.

The working modelling principle is:

- treat the 2025 full-auction dataset as the core modelling base
- treat earlier historical material as contextual or supporting evidence
- keep feature engineering explainable and commercially meaningful
- keep pricing and auction-strategy outputs framed as transparent simulations until internal conversion, bidder, reserve, and sales-outcome data are available

## Environment

Install dependencies with:

```bash
pip install -r requirements.txt
```

Key libraries:

- `pandas`
- `numpy`
- `matplotlib`
- `seaborn`
- `scikit-learn`
- `statsmodels`

## Data Note

Raw auction files under `data/raw/` are intentionally ignored by git.

Notebook `01` expects the local raw file:

```text
data/raw/dvla_auction_results_2025.csv
```

That file is kept local because it is a raw extract. The repository commits processed outputs and compact reports so the project can still be reviewed without publishing raw extracts.

Notebook `02` starts from the committed processed dataset:

```text
data/processed/valuation_core_2025.csv
```
