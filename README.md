# Plate Value Intelligence

Plate Value Intelligence is a portfolio data project built around UK DVLA personalised registration auction results.

The current repo focus is not data collection. It is structured around:

- auditing auction data quality
- building a governed modelling dataset
- engineering explainable plate features
- preparing valuation-ready tables for downstream modelling

## Repository Contents

- [01_data_audit_and_governance.ipynb](/Users/osmanorka/Plate-Value-Intelligence/01_data_audit_and_governance.ipynb)
  - audits the 2025 auction dataset
  - checks completeness, duplicates, and event coverage
  - produces governed processed outputs
- [02_plate_feature_engineering.ipynb](/Users/osmanorka/Plate-Value-Intelligence/02_plate_feature_engineering.ipynb)
  - derives interpretable plate-level features
  - prepares valuation-oriented feature tables
- [data/processed/all_sources_governed_2025.csv](/Users/osmanorka/Plate-Value-Intelligence/data/processed/all_sources_governed_2025.csv)
  - governed dataset with quality and governance fields
- [data/processed/valuation_core_2025.csv](/Users/osmanorka/Plate-Value-Intelligence/data/processed/valuation_core_2025.csv)
  - cleaned core dataset for modelling and feature work
- [reports/](/Users/osmanorka/Plate-Value-Intelligence/reports)
  - summary outputs for coverage, data quality, and price quantiles
- [sources/](/Users/osmanorka/Plate-Value-Intelligence/sources)
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

The committed repository keeps processed outputs and compact reports needed for analysis and portfolio review, while larger raw extracts remain local.
