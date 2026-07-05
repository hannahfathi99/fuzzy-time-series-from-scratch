# Results

## Dataset 1: Mackey–Glass

Best configuration:
- Order: 3
- Partitions: 30

Metrics:
- RMSE: 0.034076
- MAE: 0.025283
- MAPE: 4.075%

FOFTS baseline:
- RMSE: 0.050110

Improvement:
~32% RMSE reduction with HOFTS

---

## Dataset 2: Influenza

### TOTAL SPECIMENS
- Best: FOFTS (order 1, 15 partitions)
- RMSE: 10617.999

### TOTAL A
- Best: HOFTS (order 3, 30 partitions)
- RMSE: 3700.41 (log1p scale)

### TOTAL B
- Best: FOFTS (order 1, 15 partitions)
- RMSE: 332.418 (log1p scale)

---

## Key Findings

### 1. Mackey–Glass
- Strong benefit from higher-order modeling
- Captures long-range dependencies

### 2. Influenza Data
- Mixed performance
- Higher-order models suffer from sparsity

---

## Rule Statistics (Mackey–Glass)

- Rule hit rate: 97%
- Fallback rate: 3%
- Back-off rate: 9%
- High rule coverage

---

## Conclusion from Results

- HOFTS is effective for structured dynamics
- FOFTS is more stable for noisy real-world data
- Back-off mechanism is essential for HOFTS stability
