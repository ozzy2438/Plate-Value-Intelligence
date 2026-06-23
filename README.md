# Plate Value Intelligence

Plate Value Intelligence is a portfolio data project built around UK DVLA personalised registration auction results.

The current repo focus is not data collection. It is structured around:

- auditing auction data quality
- building a governed modelling dataset
- engineering explainable plate features
- preparing valuation-ready tables for downstream modelling

## Repository Contents

- [01_data_audit_and_governance.ipynb](01_data_audit_and_governance.ipynb)
  - audits the 2025 auction dataset
  - checks completeness, duplicates, and event coverage
  - produces governed processed outputs
- [02_plate_feature_engineering.ipynb](02_plate_feature_engineering.ipynb)
  - derives interpretable plate-level features
  - prepares valuation-oriented feature tables
- [data/processed/all_sources_governed_2025.csv](data/processed/all_sources_governed_2025.csv)
  - governed dataset with quality and governance fields
- [data/processed/valuation_core_2025.csv](data/processed/valuation_core_2025.csv)
  - cleaned core dataset for modelling and feature work
- [data/processed/plate_features_2025.csv](data/processed/plate_features_2025.csv)
  - valuation-ready feature table derived from the core 2025 dataset
- [reports/](reports)
  - summary outputs for coverage, data quality, and price quantiles
- [sources/](sources)
  - supporting source indexes and historical reference files

## Project Positioning

This project is being developed as a job application portfolio piece.

The working modelling principle is:

- treat the 2025 full-auction dataset as the core modelling base
- treat earlier historical material as contextual or supporting evidence
- keep feature engineering explainable and commercially meaningful

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
