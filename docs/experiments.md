# Experiments

## Experimental Setup

All experiments follow a consistent protocol:

- Time-ordered 80/20 split
- One-step-ahead forecasting
- Teacher forcing evaluation
- Grid search over:
  - Model order: 1 to 4
  - Partitions: {7, 10, 15, 20, 30}

---

## Datasets

### 1. Mackey–Glass
- Chaotic nonlinear system
- Long-term dependencies
- Benchmark dataset

### 2. Influenza Surveillance
- Real-world epidemiological data
- Noisy and sparse signals
- Targets:
  - TOTAL SPECIMENS
  - TOTAL A
  - TOTAL B

---

## Preprocessing

- Missing values removed
- No shuffling
- log1p transform applied for Influenza A/B
- Inverse transform applied before evaluation

---

## Evaluation Metrics

- RMSE (primary selection metric)
- MAE
- MAPE

---

## Hyperparameter Search

Grid:

| Parameter | Values |
|----------|--------|
| Order    | 1, 2, 3, 4 |
| Partitions | 7, 10, 15, 20, 30 |

Total: 20 configurations per dataset.

---

## Model Variants

- FOFTS (order = 1)
- HOFTS (order ≥ 2)

Each evaluated under identical conditions.

---

## Observations

- HOFTS improves performance in structured chaotic systems
- FOFTS performs better in noisy sparse datasets
- Back-off strategy significantly improves robustness
