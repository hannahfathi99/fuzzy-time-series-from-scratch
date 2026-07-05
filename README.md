# Fuzzy Time Series Forecasting from Scratch

[![Python](https://img.shields.io/badge/Python-3.10+-blue.svg)](https://www.python.org/)
[![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange.svg)](https://jupyter.org/)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![Status](https://img.shields.io/badge/Project-Completed-success.svg)]()
[![University](https://img.shields.io/badge/Shiraz%20University-purple.svg)]()

---

## Overview

This repository presents a **complete implementation of a Fuzzy Time Series (FTS) forecasting framework from scratch in Python**, without relying on any external FTS-specific libraries.

The main goal is to design a fully interpretable forecasting system capable of modeling:

- nonlinear temporal dynamics  
- chaotic time series  
- noisy real-world signals  
- sparse and irregular observations  

All components of the pipeline—including fuzzification, rule extraction, forecasting, and defuzzification—are implemented manually from first principles.

---

## Project Objectives

- Implement a full Fuzzy Time Series framework from scratch  
- Develop First-Order and Higher-Order FTS models  
- Introduce a hierarchical back-off mechanism for rule sparsity  
- Compare partitioning strategies (equal-width vs quantile-based)  
- Evaluate multiple membership functions  
- Perform hyperparameter optimization  
- Validate performance on benchmark and real-world datasets  

---

## Key Contributions

### 1. Scratch Implementation
No fuzzy time series library is used. Every component is independently implemented in Python.

---

### 2. Higher-Order FTS (HOFTS)
Supports arbitrary order \(k\), enabling learning of long-range dependencies:

(A(t-k), ..., A(t-1)) → A(t)

---

### 3. Hierarchical Back-off Strategy
To handle unseen rules, the system gradually backs off:

Order K

  ↓

Order K−1

  ↓

Order K−2

  ↓

  ...

  ↓

Order 1

  ↓

Persistence

This significantly improves robustness and rule coverage.

---

### 4. Frequency-Aware FLRG
Each fuzzy rule stores:

- transition frequency  
- probability  
- weighted consequents  

instead of simple deterministic mappings.

---

### 5. Multiple Partitioning Methods
- Equal-width partitioning  
- Quantile-based partitioning  

allowing adaptation to different data distributions.

---

### 6. Membership Functions
- Triangular (primary experimental setup)  
- Gaussian (research extension)

---

### 7. Automated Hyperparameter Search
Grid search over:

- model order: 1–4  
- number of partitions: 7, 10, 15, 20, 30  

---

## Repository Structure

```

fuzzy-time-series-from-scratch/

├── data/
│ ├── raw/
│ │ ├── mackey_glass.csv
│ │ └── Specimens-Train.xlsx
│ │
│ └── processed/
│
├── notebooks/
│ └── Fuzzy_Project1.ipynb
│
├── reports/
│ ├── Project1_Report.pdf
│ └── figures/
│
├── outputs/
│ ├── predictions/
│ ├── tables/
│ ├── metrics/
│ └── logs/
│
├── images/
│ ├── architecture.png
│ ├── pipeline.png
│ ├── membership.png
│ └── forecast.png
│
├── docs/
│ ├── methodology.md
│ ├── implementation.md
│ ├── experiments.md
│ ├── results.md
│ └── reproducibility.md
│
├── README.md
├── LICENSE
├── CHANGELOG.md
├── CONTRIBUTING.md
├── CODE_OF_CONDUCT.md
├── requirements.txt
├── environment.yml
├── CITATION.cff
└── .gitignore

```

---

## Repository Workflow

```

Raw Dataset

    ↓

Data Cleaning

    ↓

Train/Test Split

    ↓

Universe of Discourse

    ↓

Partitioning

    ↓

Membership Functions

    ↓

Fuzzification

    ↓

FLR Generation

    ↓

FLRG Construction

    ↓

Forecasting

    ↓

Defuzzification

    ↓

Evaluation

    ↓

Visualization

    ↓

Report Generation

```

---

## Datasets

### Mackey–Glass Time Series
A standard nonlinear chaotic benchmark used in forecasting research.

- deterministic chaos  
- nonlinear dynamics  
- long-term dependencies  

data/raw/mackey_glass.csv

---

### Influenza Surveillance Dataset
Real-world epidemiological dataset with:

- noise  
- seasonal behavior  
- sparse count distributions  

Targets:

| Variable | Description |
|----------|-------------|
| TOTAL SPECIMENS | Laboratory sample counts |
| TOTAL A | Influenza A cases |
| TOTAL B | Influenza B cases |


data/raw/Specimens-Train.xlsx

---

# Methodology

This project implements a complete **Fuzzy Time Series (FTS) forecasting framework from scratch**, designed based on the classical fuzzy time series paradigm and extended with higher-order modeling, frequency-aware rule learning, and a hierarchical back-off inference strategy.

The entire pipeline has been developed without relying on any external FTS libraries, ensuring full transparency, reproducibility, and educational clarity.

---

## End-to-End Forecasting Pipeline

The complete workflow of the proposed system is illustrated below:

```

Raw Time Series

    ↓

Data Cleaning

    ↓

Train/Test Split

    ↓

Universe of Discourse

    ↓

Fuzzy Partitioning

    ↓

Membership Function Construction

    ↓

Fuzzification

    ↓

FLR Extraction

    ↓

FLRG Construction

    ↓

Forecasting

    ↓

Weighted Defuzzification

    ↓

Performance Evaluation

    ↓

Visualization

```



Each stage is independently implemented to ensure modularity and extensibility.

---

# 1. Universe of Discourse

The first step in fuzzy time series modeling is defining the **Universe of Discourse (U)**, which determines the numerical range over which fuzzy sets are defined.

To avoid boundary issues, a small safety margin is added to the observed training range:

$$
U = \left[ \min(X_{train}) - \delta,\ \max(X_{train}) + \delta \right]
$$

where:

$$
\delta = 0.05 \times \left( \max(X_{train}) - \min(X_{train}) \right)
$$

### Key Design Choice

Only **training data** is used to compute the universe.  
This prevents data leakage and ensures a fair forecasting evaluation.

---

# 2. Fuzzy Partitioning

After defining the universe, it is partitioned into fuzzy intervals representing linguistic states.

Each interval corresponds to a fuzzy label:

A1, A2, A3, ..., Am

where

m ∈ {7, 10, 15, 20, 30}


The optimal number of partitions is selected through grid search.

---

## 2.1 Equal-Width Partitioning

The universe is divided into equal-length intervals:

$$
w = \frac{U_{max} - U_{min}}{m}
$$

Centers are defined as:

$$
c_i = U_{min} + \left(i - \frac{1}{2}\right) w
$$

**Advantages:**
- Simple and fast
- Standard in classical FTS
- Uniform coverage of space

**Limitations:**
- Poor adaptation to skewed distributions
- Inefficient allocation in dense regions

---

## 2.2 Quantile-Based Partitioning

To address distribution imbalance, a quantile-based strategy is also implemented.

This method assigns more fuzzy sets to dense regions and fewer to sparse regions.

**Benefits:**
- Adaptive resolution
- Better representation of real-world skewed data
- Improved rule coverage in epidemiological datasets

---

# 3. Membership Functions

Each fuzzy set is defined using a membership function that maps numerical values to degrees of belonging.

Two membership functions are implemented.

---

## 3.1 Triangular Membership Function (Default)

The triangular function is defined using adjacent centers:

$$
\(c_{i-1}\), \(c_i\), \(c_{i+1}\)
$$

It provides a piecewise linear approximation:

**Key properties:**
- Fast computation
- Interpretable structure
- Smooth overlap between neighboring sets

This function is used in all reported experiments.

---

## 3.2 Gaussian Membership Function

A Gaussian alternative is also implemented:

$$
\mu(x) = \exp\left(-\frac{(x - c_i)^2}{2\sigma^2}\right)
$$

**Characteristics:**
- Smooth and differentiable
- Wider influence range
- Suitable for advanced research extensions

---

## 3.3 Overlapping Structure

Fuzzy sets are intentionally overlapping to ensure:

- robustness to noise
- smooth transitions between states
- stability under small perturbations

---

# 4. Fuzzification

Each numerical observation is converted into a fuzzy state using the **maximum membership principle**.

```
Example

0.73
  ↓

A1 = 0.02
A2 = 0.18
A3 = 0.84
A4 = 0.31

  ↓
Assigned State

A3
```

The resulting fuzzy sequence forms the symbolic representation of the time series.

---

# 5. Fuzzy Logical Relationships (FLR)

FLRs represent transitions between fuzzy states.

## First-Order FLR

A(t−1) → A(t)

Example:

```
A5
  ↓
A7
```

represents:

```
A5 → A7
```

## Higher-Order FLR

Captures longer dependencies:

(A(t−k), ..., A(t−1)) → A(t)

Example:

```
(A2, A4, A5)
      ↓
     A6
```

represents:

```
(A2, A4, A5) → A6
```

Every valid transition observed in the training sequence is recorded.

---

# 6. Fuzzy Logical Relationship Groups (FLRG)

Instead of storing individual transitions, FLRs are aggregated into FLRGs.

Example:

```
A3
 ↓
A4
 ↓
A5
 ↓
A5
 ↓
A4
```

becomes:

```
A3
 ↓
{A4:2 , A5:2}
```

Each FLRG stores:
- antecedent
- consequent states
- transition frequencies

This structure preserves empirical distribution information.

---

# 7. Forecasting Engine

The forecasting process follows:

```
History
   ↓
Fuzzification
   ↓
Rule Matching
   ↓
Weighted Defuzzification
   ↓
Prediction
```

---

# FOFTS Prediction

For first-order forecasting:

```
Last State
   ↓
Locate FLRG
   ↓
Compute Weighted Center
   ↓
Prediction
```

Only one previous fuzzy state is required.

---

# HOFTS Prediction

For higher-order forecasting:

```
Last K States
   ↓
Construct Antecedent
   ↓
Search Order-K FLRG
   ↓
Prediction
```

Longer historical context allows more complex temporal dependencies to be modeled.

---

# Hierarchical Back-off

Higher-order models frequently encounter unseen antecedent patterns.

Instead of terminating the search, the implementation performs hierarchical back-off:

```
Order 4
  ↓
Order 3
  ↓
Order 2
  ↓
Order 1
  ↓
Persistence
```

The first matching rule is used.

If no rule exists, the previous observation is returned.

This strategy dramatically increases rule coverage while maintaining forecasting stability.

---

# 8. Weighted Defuzzification

Final predictions are computed using frequency-weighted averaging:

Prediction =
Σ (frequency × centroid) / Σ frequency

Workflow:

```
Matched FLRG
     ↓
Consequent Centers
     ↓
Frequency Weights
     ↓
Weighted Average
     ↓
Prediction
```

This ensures:
- stability
- smoother forecasts
- better representation of repeated transitions

---

# 9. Evaluation Strategy

Model performance is evaluated using:

- RMSE
- MAE
- MAPE

All metrics are computed using **one-step-ahead teacher forcing**, ensuring fair and stable evaluation.

For datasets with transformations (log1p), predictions are mapped back to original scale before evaluation.

---

# 10. Visualization & Outputs

The system automatically generates:

- actual vs predicted plots
- membership function visualizations
- partition diagrams
- heatmaps of hyperparameters
- performance comparison charts

All outputs are saved in:

```
outputs/
```

for full reproducibility.

---

# Result Export

Every experiment automatically exports:

- prediction tables
- evaluation metrics
- selected hyperparameters
- generated figures
- summary tables

The outputs are organized inside the `outputs/` directory to facilitate reproducibility and further analysis.

---

# Results & Analysis

The proposed Fuzzy Time Series framework was evaluated on two independent forecasting problems with fundamentally different characteristics. The first dataset, Mackey–Glass, represents a deterministic nonlinear chaotic system and is commonly used as a benchmark for time series forecasting algorithms. The second dataset consists of real influenza surveillance records containing weekly epidemiological counts, which exhibit substantial stochasticity, nonstationarity, and skewness.

All experiments followed the identical evaluation protocol presented in the Methodology section:

- Chronological 80% / 20% train–test split  
- One-step-ahead forecasting  
- Teacher forcing evaluation  
- Grid search over model order and number of fuzzy partitions  
- RMSE used for model selection  
- MAE and MAPE reported as complementary evaluation metrics  

For every dataset, both First-Order FTS (FOFTS) and Higher-Order FTS (HOFTS) models were trained and evaluated using exactly the same experimental pipeline.

---

# Evaluation Protocol

Each candidate model is uniquely defined by:

- Model order  
- Number of fuzzy partitions  

Search space:

| Hyperparameter | Values |
|----------------|--------|
| Order          | 1, 2, 3, 4 |
| Partitions     | 7, 10, 15, 20, 30 |

This results in twenty independent configurations per dataset.

For influenza datasets, both equal-width and quantile partitioning were evaluated. The best configuration was selected by lowest RMSE.

---

# Dataset 1 — Mackey–Glass

The Mackey–Glass dataset represents a nonlinear chaotic system with long-range dependencies.

| Model      | Order | Partitions | RMSE | MAE | MAPE |
|------------|------:|-----------:|-----:|----:|-----:|
| Best HOFTS | **3** | **30** | **0.034076** | **0.025283** | **4.075%** |
| Best FOFTS | 1 | 30 | 0.050110 | 0.040302 | 6.766% |

---

### Rule Statistics

| Statistic | Value |
|-----------|------:|
| Order | 3 |
| Partitions | 30 |
| High-order FLRGs | 232 |
| Rule hit rate | 97% |
| Fallback rate | 3% |
| Back-off rate | 9% |

---

### Interpretation

- Higher-order modeling improves accuracy  
- Back-off prevents sparsity issues  
- Strong coverage of temporal patterns  

---

# Dataset 2 — Influenza Surveillance

Real epidemiological data with noise, seasonality, and nonstationarity.

Targets:
- TOTAL SPECIMENS  
- TOTAL A  
- TOTAL B  

---

## TOTAL SPECIMENS

| Model | Order | Partitions | RMSE | MAE | MAPE |
|------|------:|-----------:|-----:|----:|-----:|
| Best | 1 | 15 | 10617.999 | 8352.66 | 10.13% |

---

## TOTAL A (log1p)

| Model | Order | Partitions | RMSE | MAE | MAPE |
|------|------:|-----------:|-----:|----:|-----:|
| Best | 3 | 30 | 3700.41 | 1700.00 | 25.62% |

---

## TOTAL B (log1p)

| Model | Order | Partitions | RMSE | MAE | MAPE |
|------|------:|-----------:|-----:|----:|-----:|
| Best | 1 | 15 | 332.418 | 214.615 | 28.38% |

---

# Comparative Performance

| Dataset | Best Order | Partitions | RMSE | MAE | MAPE |
|---------|----------:|-----------:|-----:|----:|-----:|
| Mackey–Glass | 3 | 30 | 0.034076 | 0.025283 | 4.075% |
| TOTAL SPECIMENS | 1 | 15 | 10617.999 | 8352.66 | 10.13% |
| TOTAL A | 3 | 30 | 3700.41 | 1700.00 | 25.62% |
| TOTAL B | 1 | 15 | 332.418 | 214.615 | 28.38% |


---

# Summary

This methodology implements a fully modular, interpretable, and extensible fuzzy time series framework. The design emphasizes:

- complete from-scratch implementation
- reproducibility
- interpretability of fuzzy rules
- robustness through hierarchical inference
- adaptability to both synthetic and real-world datasets

The resulting system serves both as a research prototype and an educational reference for advanced fuzzy time series modeling.


---

# References

The implementation and methodology were inspired by foundational literature in fuzzy time series forecasting and fuzzy systems.

1. Song, Q., & Chissom, B. S. (1993). *Forecasting enrollments with fuzzy time series*. Fuzzy Sets and Systems, 54(1), 1–9.

2. Song, Q., & Chissom, B. S. (1994). *Fuzzy time series and its models*. Fuzzy Sets and Systems, 54(3), 269–277.

3. Chen, S. M. (1996). *Forecasting enrollments based on fuzzy time series*. Fuzzy Sets and Systems, 81(3), 311–319.

4. Zadeh, L. A. (1965). *Fuzzy Sets*. Information and Control, 8(3), 338–353.

5. Ross, T. J. (2010). *Fuzzy Logic with Engineering Applications* (3rd ed.). Wiley.

6. Klir, G. J., & Yuan, B. (1995). *Fuzzy Sets and Fuzzy Logic: Theory and Applications*. Prentice Hall.

7. Jang, J. S. R., Sun, C. T., & Mizutani, E. (1997). *Neuro-Fuzzy and Soft Computing*. Prentice Hall.

8. Mendel, J. M. (2001). *Uncertain Rule-Based Fuzzy Logic Systems*. Prentice Hall.

---

# Conclusion

This project presents a complete implementation of First-Order and Higher-Order Fuzzy Time Series forecasting developed entirely from scratch without relying on specialized fuzzy time series libraries.

The framework includes every major component required for practical FTS modeling, including preprocessing, universe construction, fuzzy partitioning, membership function evaluation, fuzzification, FLRG generation, weighted defuzzification, hierarchical back-off, hyperparameter optimization, visualization, and quantitative evaluation.

Experimental results demonstrate that Higher-Order FTS models significantly improve forecasting accuracy for deterministic nonlinear systems such as the Mackey–Glass benchmark by effectively exploiting long-range temporal dependencies. Conversely, for noisy real-world epidemiological data, simpler First-Order models often achieve comparable or superior performance due to reduced rule sparsity and lower model complexity.

Overall, the repository provides a transparent, reproducible, and extensible implementation of Fuzzy Time Series forecasting that is suitable for educational purposes, academic coursework, and future research in fuzzy systems and intelligent forecasting.
