# Data Card

## Data Source

The core modelling dataset is based on 2025 DVLA personalised-registration auction event results.

## Coverage

- Auction year: 2025
- Events: 9
- Audited lots: 18,000
- Recorded hammer-price observations: 17,782
- Missing price records: 218

Records without a recorded hammer price were excluded from price modelling. They were not assumed to be unsold.

## Business Key

The event-level business key is:

```text
event_code + lot_number
```

This key is used for validation, joins, and final decision-table checks.

## Data Quality Checks

The audit process checks:

- total records
- event coverage
- duplicate event-lot keys
- missing lot numbers
- recorded and missing hammer prices
- price completeness
- event-level distribution

## Coverage Level

The 2025 event-level export is treated as the full modelling distribution for this project. It supports train, validation, and final test splits by auction event.

## Price Basis

The modelling target is recorded hammer price in GBP.

## Why 2025 Is the Modelling Core

The 2025 source is complete enough for event-based modelling. It contains full event coverage, real hammer prices, and enough volume to support feature engineering, model validation, and final holdout testing.

## Why Historical Data Is Not Merged Into Training

Earlier Regtransfers material is retained as historical supporting evidence, but it is not equivalent to the 2025 event-level export. The historical material is partial, editorial, and biased toward top sales or notable plates. It should not be used as model-training augmentation or annual price-trend evidence.

## Known Limitations

- no bidder history
- no bid sequence
- no customer-level demand
- no listing views
- no conversion
- no listing duration
- no price elasticity
- no reserve experiments
- no verified unsold / withdrawn outcome
- only one full calendar year is used for core modelling

