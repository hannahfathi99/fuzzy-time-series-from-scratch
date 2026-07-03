# Data

This directory contains the datasets used throughout the experiments.

The project evaluates the proposed Fuzzy Time Series forecasting framework on two independent datasets representing different forecasting scenarios.

---

# Directory Structure

```text
data/

├── raw/
│      mackey_glass.csv
│      Specimens-Train.xlsx
│
└── processed/
```

---

# Raw Data

The **raw** directory stores the original datasets exactly as used during the experiments.

No modifications should be made to these files.

## Mackey–Glass

**File**

```
mackey_glass.csv
```

Description

* nonlinear chaotic time series
* continuous-valued observations
* benchmark dataset for forecasting research
* used to evaluate long-term temporal dependency modeling

The series is treated as a univariate forecasting problem.

---

## Influenza Surveillance Dataset

**File**

```
Specimens-Train.xlsx
```

Forecasting targets

* TOTAL SPECIMENS
* TOTAL A
* TOTAL B

Characteristics

* weekly observations
* real epidemiological surveillance data
* count-based measurements
* highly skewed distributions
* noisy temporal behavior

Each target is modeled independently.

---

# Processed Data

The **processed** directory is reserved for optional intermediate datasets generated during preprocessing.

Typical examples include

* cleaned datasets
* transformed datasets
* normalized series
* log-transformed series
* derived features

The current implementation performs preprocessing in memory and therefore does not generate processed files by default.

---

# Reproducibility

The experiments always read the original datasets located inside

```
data/raw/
```

No manual preprocessing is required before running the notebook.
