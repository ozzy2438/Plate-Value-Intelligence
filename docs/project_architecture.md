# Project Architecture

Plate Value Intelligence is structured as a portfolio decision-support pipeline. The core modelling distribution is the complete 2025 DVLA auction event dataset; historical Regtransfers material is retained only as supporting evidence.

```mermaid
flowchart LR
    subgraph DataLayer[Data layer]
        A[Raw auction extract]
        B[Governed processed data]
        C[Feature table]
    end

    subgraph AnalyticalLayer[Analytical layer]
        D[Exploratory pricing analysis]
        E[Baseline valuation models]
        F[Tree-based valuation models]
        G[Premium and collectible scoring]
    end

    subgraph DecisionLayer[Decision layer]
        H[Valuation ranges]
        I[Fixed-price routing]
        J[Standard auction routing]
        K[Premium showcase routing]
        L[Specialist review]
        M[Commercial investigation flags]
    end

    A --> B --> C --> D --> E --> F --> G --> H
    H --> I
    H --> J
    H --> K
    G --> L
    H --> M
    G --> M
```

## Design Principles

- Keep the modelling base anchored on the full 2025 event-level export.
- Use event-based validation instead of random splits.
- Keep predictor sets leakage-safe and explainable.
- Treat specialist-review assets as human-in-the-loop decisions, not automatic pricing cases.
- Present reserve and fixed-price policies as transparent retrospective simulations, not optimal pricing claims.

