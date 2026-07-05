# Methodology

## Overview
This project implements a fully from-scratch Fuzzy Time Series (FTS) forecasting framework, including both First-Order FTS (FOFTS) and Higher-Order FTS (HOFTS). The entire pipeline is designed without using any external FTS libraries to ensure interpretability and reproducibility.

---

## Data Preprocessing and Temporal Split

Each dataset is treated as a univariate time series.

- Missing or invalid values are removed
- No random shuffling is applied
- Data is split chronologically:
  - 80% training
  - 20% testing

Evaluation uses one-step-ahead forecasting with teacher forcing, where the true observation is appended after each prediction step.

---

## Universe of Discourse

The universe of discourse is defined as:

U = [min(X_train) − δ, max(X_train) + δ]

where:

δ = 0.05 × (max(X_train) − min(X_train))

Only training data is used to prevent data leakage.

---

## Fuzzy Partitioning

The universe is partitioned into m fuzzy sets:

m ∈ {7, 10, 15, 20, 30}

Two strategies are used:

### 1. Equal-width partitioning
- Uniform interval spacing
- Simple and computationally efficient

### 2. Quantile-based partitioning
- Based on empirical data distribution
- Better for skewed datasets

---

## Membership Functions

Two membership functions are implemented:

### Triangular (default)
- Low computational cost
- High interpretability
- Used in all final experiments

### Gaussian (optional extension)
- Smooth and differentiable
- Suitable for research extensions

Fuzzification uses the maximum membership principle:

A(x) = argmax μ_Ai(x)

---

## Fuzzy Logical Relationships (FLR)

### FOFTS
A(t−1) → A(t)

### HOFTS
(A(t−k), ..., A(t−1)) → A(t)

---

## FLRG Construction

FLRs are aggregated into Frequency-aware Fuzzy Logical Relationship Groups (FLRGs):

- Antecedent → set of consequents
- Each consequent has frequency counts
- Preserves empirical transition distribution

---

## Forecasting and Defuzzification

Prediction is computed using weighted defuzzification:

ŷ(t) = Σ(cj × wj) / Σ(wj)

where:
- cj: centroid of fuzzy set
- wj: frequency weight

Fallback strategy:
- If no rule exists → persistence (last value)

---

## Higher-Order Back-off Strategy

If HOFTS rule is not found:

Order K → K−1 → ... → 1 → persistence

This ensures robustness under rule sparsity.
