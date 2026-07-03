# Fuzzy Time Series Forecasting from Scratch

A complete implementation of **First-Order Fuzzy Time Series (FOFTS)** and **Higher-Order Fuzzy Time Series (HOFTS)** forecasting models developed entirely from scratch in Python.

This project was implemented as part of a Fuzzy Sets and Systems course and follows the assignment requirement of **not using any pre-implemented fuzzy time series libraries**. Every component of the forecasting framework—including fuzzy partitioning, membership functions, fuzzification, fuzzy logical relationship groups (FLRGs), forecasting, and defuzzification—was implemented manually.

---

# Project Overview

Fuzzy Time Series (FTS) is a rule-based forecasting technique that models temporal data using fuzzy set theory instead of conventional statistical assumptions. Compared with classical forecasting methods, FTS provides an interpretable framework capable of handling uncertainty and nonlinear behavior.

This repository implements both:

* **First-Order Fuzzy Time Series (FOFTS)**
* **Higher-Order Fuzzy Time Series (HOFTS)**

and compares their forecasting performance on two benchmark datasets.

The implementation includes an experimental framework for parameter tuning, performance evaluation, visualization, and interactive prediction.

---

# Features

* Complete implementation from scratch
* No external Fuzzy Time Series libraries
* First-Order FTS (FOFTS)
* Higher-Order FTS (HOFTS)
* True Back-off mechanism for higher-order models
* Equal-width partitioning
* Quantile-based partitioning
* Triangular membership functions
* Gaussian membership functions
* Automatic fuzzification
* Frequency-aware FLRG generation
* Weighted defuzzification
* Grid search over model order and number of partitions
* Teacher forcing evaluation
* Interactive forecasting interface
* Publication-quality visualizations

---

# Repository Structure

```text
fuzzy-time-series-from-scratch/

├── datasets/
├── notebooks/
├── report/
├── results/
├── docs/
├── README.md
├── LICENSE
├── requirements.txt
└── environment.yml
```

---

# Datasets

Two datasets are used throughout the experiments.

## 1. Mackey–Glass Time Series

A nonlinear chaotic benchmark widely used for evaluating forecasting algorithms.

Characteristics:

* Continuous-valued
* Deterministic chaotic dynamics
* Long-term temporal dependencies

---

## 2. Influenza Surveillance Dataset

Weekly influenza surveillance records containing three forecasting targets:

* TOTAL SPECIMENS
* TOTAL A
* TOTAL B

Characteristics:

* Real-world epidemiological data
* Count-based observations
* Noisy and highly skewed distributions

---

# Methodology

The forecasting pipeline consists of the following stages.

## 1. Data Preprocessing

* Load datasets
* Remove invalid observations
* Preserve chronological ordering
* Split data into

  * 80% training
  * 20% testing

No random shuffling is applied.

---

## 2. Universe of Discourse

For every training series, the universe is defined as

U = [min(X) − δ , max(X) + δ]

where δ equals 5% of the data range.

---

## 3. Fuzzy Partitioning

The universe is divided into

* 7 partitions
* 10 partitions
* 15 partitions
* 20 partitions
* 30 partitions

Two partitioning strategies are implemented:

* Equal-width partitioning
* Quantile-based partitioning

---

## 4. Membership Functions

Two membership functions are implemented.

### Triangular Membership Function

Used in all reported experiments due to

* simplicity
* interpretability
* computational efficiency

### Gaussian Membership Function

Implemented for comparison and extensibility.

---

## 5. Fuzzification

Each numerical observation is converted into its corresponding fuzzy state using the maximum membership principle.

---

## 6. FLRG Generation

Fuzzy Logical Relationship Groups (FLRGs) are generated from the fuzzified sequence.

### First-Order

A(t−1) → A(t)

### Higher-Order

(A(t−k), … , A(t−1)) → A(t)

Each FLRG stores frequency information to preserve empirical transition probabilities.

---

## 7. Forecasting

Predictions are obtained by

* matching fuzzy rules
* applying weighted defuzzification
* computing the weighted average of consequent fuzzy set centers

If no exact rule exists, a persistence strategy is used.

---

## 8. True Back-off Strategy

To reduce rule sparsity in higher-order models, a true hierarchical back-off mechanism is implemented.

Prediction proceeds as follows:

1. Search the highest-order FLRG
2. If unavailable, search lower-order FLRGs
3. Continue until order one
4. If no rule exists, return the previous observation

This significantly improves rule coverage during inference.

---

# Experimental Configuration

Model orders:

* 1
* 2
* 3
* 4

Number of partitions:

* 7
* 10
* 15
* 20
* 30

Evaluation strategy:

* One-step-ahead forecasting
* Teacher forcing
* Time-ordered train/test split

---

# Evaluation Metrics

The following forecasting metrics are reported.

* RMSE
* MAE
* MAPE

For Influenza A and B, a log1p transformation is applied during training and inverted before evaluation.

---

# Results Summary

| Dataset         | Best Order | Partitions |
| --------------- | ---------: | ---------: |
| Mackey–Glass    |          3 |         30 |
| TOTAL SPECIMENS |          1 |         15 |
| TOTAL A         |          3 |         30 |
| TOTAL B         |          1 |         15 |

The experiments demonstrate that Higher-Order FTS substantially improves forecasting performance for the nonlinear Mackey–Glass benchmark, while first-order models remain competitive for sparse and noisy epidemiological data.

---

# Visual Outputs

The repository generates:

* Forecast plots
* Membership function plots
* RMSE comparison plots
* Grid search results
* FLRG exports
* Appendix tables

All generated figures are stored inside the **results** directory.

---

# Interactive Prediction

An interactive command-line interface is included.

Users may enter the most recent historical observations and obtain the predicted next value using the trained FTS model.

---

# Requirements

Python 3.10 or newer.

Main dependencies:

* NumPy
* Pandas
* Matplotlib
* OpenPyXL
* Jupyter Notebook

Install all packages using

```bash
pip install -r requirements.txt
```

or

```bash
conda env create -f environment.yml
```

---

# Running the Project

Clone the repository

```bash
git clone https://github.com/your-username/fuzzy-time-series-from-scratch.git
```

Move into the project directory

```bash
cd fuzzy-time-series-from-scratch
```

Launch the notebook

```bash
jupyter notebook notebooks/Fuzzy_Project1.ipynb
```

Execute all notebook cells to reproduce every experiment, figure, table, and exported result.

---

# Reproducibility

Random seeds are fixed throughout the implementation to ensure reproducible experiments.

All reported results can be regenerated directly from the provided notebook and datasets.

---

# License

This repository is released under the MIT License.

---

# Acknowledgments

The Mackey–Glass time series is widely used as a benchmark for nonlinear forecasting research.

The Influenza surveillance dataset is included exclusively for educational forecasting experiments.

---

# Keywords

Fuzzy Time Series • FOFTS • HOFTS • Fuzzy Logic • Time Series Forecasting • Soft Computing • Mackey–Glass • Influenza Forecasting • Rule-Based Systems • Python
