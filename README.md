# Fuzzy Time Series Forecasting from Scratch

[![Python](https://img.shields.io/badge/Python-3.10+-blue.svg)](https://www.python.org/)
[![Jupyter Notebook](https://img.shields.io/badge/Jupyter-Notebook-orange.svg)](https://jupyter.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![Course](https://img.shields.io/badge/Course-Fuzzy%20Sets%20and%20Systems-red.svg)]()
[![Status](https://img.shields.io/badge/Project-Completed-success.svg)]()
[![University](https://img.shields.io/badge/Shiraz-University-purple.svg)]()

---

# Project Information

**Course**

Fuzzy Sets and Systems

**Project**

Project 1 – Fuzzy Time Series Forecasting

**Semester**

Fall 2025

**Student**

Hannah Fathi

**Student Number**

40360347

**University**

Shiraz University

---

# Abstract

This repository presents a complete implementation of a **Fuzzy Time Series (FTS) forecasting framework** developed entirely **from scratch** in Python.

Unlike existing implementations that rely on dedicated fuzzy time series packages, every component of the forecasting pipeline has been manually designed and implemented, including:

- Universe of discourse generation
- Fuzzy partitioning
- Membership functions
- Fuzzification
- FLR construction
- FLRG generation
- Frequency-aware inference
- Weighted defuzzification
- Higher-order fuzzy models
- Hierarchical Back-off strategy
- Forecast evaluation
- Hyperparameter search
- Visualization

The project was developed as part of the **Fuzzy Sets and Systems** graduate course and follows the assignment requirement of **not using any pre-implemented Fuzzy Time Series library**.

---

# Motivation

Classical forecasting approaches often require assumptions such as

- linearity
- stationarity
- Gaussian noise

Real-world systems rarely satisfy these assumptions.

Fuzzy Time Series models overcome these limitations by replacing numerical relationships with interpretable linguistic rules.

Instead of estimating statistical parameters, the model learns transitions between fuzzy states.

This makes FTS particularly attractive for

- nonlinear systems
- uncertain environments
- noisy observations
- explainable forecasting

---

# Repository Highlights

This repository includes

✔ Complete implementation from scratch

✔ FOFTS

✔ HOFTS

✔ Frequency-aware FLRG

✔ Equal-width partitioning

✔ Quantile partitioning

✔ Triangular membership functions

✔ Gaussian membership functions

✔ Teacher forcing evaluation

✔ True Back-off strategy

✔ Interactive forecasting

✔ Grid Search

✔ Automatic model selection

✔ Publication-quality visualizations

✔ Reproducible experiments

---

# Key Features

## First-Order Fuzzy Time Series (FOFTS)

Implements the classical Chen-style fuzzy forecasting model using one previous fuzzy state.

Relationship:

A(t−1) → A(t)

---

## Higher-Order Fuzzy Time Series (HOFTS)

Supports arbitrary forecasting order.

Example:

(A(t−3), A(t−2), A(t−1))
            ↓
          A(t)

Higher-order models capture longer temporal dependencies.

---

## True Hierarchical Back-off

One of the main contributions of this implementation.

Rather than failing whenever an exact higher-order rule is unavailable, the algorithm progressively searches

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

This greatly improves rule coverage while maintaining prediction stability.

---

## Frequency-aware FLRG

Each FLRG stores

Rule

  ↓

Frequency

  ↓

Probability

  ↓

Weighted consequence

instead of keeping only unique transitions.

This preserves empirical transition distributions.

---

## Multiple Membership Functions

Implemented

- Triangular
- Gaussian

The reported experiments use triangular membership functions.

---

## Multiple Partitioning Methods

Implemented

Equal-width partitioning

Quantile partitioning

Both methods are available through a unified interface.

---

## Automatic Hyperparameter Search

The notebook evaluates every combination of

Model Order

   1

   2

   3

   4

   ×

Number of Partitions

   7

   10

   15

   20

   30

and automatically reports the best configuration.

---

## Interactive Prediction

After training, users can provide the most recent observations and obtain a forecast using the trained FTS model.

---

# Repository Structure

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

# Repository Workflow

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

# Project Objectives

The objectives of this project are

- Develop a complete FTS forecasting framework from scratch.
- Compare FOFTS and HOFTS models.
- Investigate the influence of model order.
- Evaluate different partitioning strategies.
- Analyze rule sparsity.
- Implement a true hierarchical back-off mechanism.
- Compare forecasting performance on benchmark and real-world datasets.
- Produce fully reproducible experimental results.

---

# Datasets

This project evaluates two different forecasting problems.

| Dataset | Type | Samples | Goal |
|----------|------|----------|------|
| Mackey–Glass | Chaotic | Continuous | Nonlinear Benchmark |
| Influenza Surveillance | Real-world | Weekly Counts | Epidemiological Forecasting |

---

# Datasets

This project evaluates the proposed Fuzzy Time Series framework using two datasets with fundamentally different temporal characteristics.

The first dataset is a classical nonlinear chaotic benchmark that is extensively used in forecasting literature, while the second dataset consists of real-world epidemiological surveillance records.

Using these two datasets allows the proposed implementation to be evaluated under both deterministic nonlinear dynamics and noisy real-world conditions.

---

# Dataset 1 — Mackey–Glass Time Series

## Description

The Mackey–Glass time series is one of the most widely used benchmark datasets for evaluating nonlinear forecasting algorithms.

It originates from the Mackey–Glass delay differential equation, which models physiological control systems and exhibits deterministic chaotic behavior under specific parameter settings.

Because of its nonlinear dynamics and long-term temporal dependencies, it is commonly used to assess forecasting models capable of learning complex temporal patterns.

---

## Characteristics

| Property | Value |
|-----------|-------|
| Type | Synthetic |
| Domain | Chaotic Dynamical System |
| Data Type | Continuous |
| Forecasting Task | One-step Ahead |
| Target Variable | Time Series Value |
| Noise Level | Very Low |
| Temporal Dependency | Strong |
| Stationarity | Non-stationary |

---

## Why Mackey–Glass?

The Mackey–Glass benchmark provides an ideal environment for evaluating High-Order Fuzzy Time Series models because:

- temporal dependencies extend beyond one lag,
- nonlinear dynamics dominate the system,
- forecasting requires memory of previous states,
- local patterns repeat with different amplitudes,
- conventional linear models often perform poorly.

For these reasons, it has become one of the standard benchmarks in Soft Computing, Computational Intelligence, and Time Series Forecasting research.

---

## File Location

```
data/raw/mackey_glass.csv
```

---

## Data Format

Example

| Time | Value |
|------|-------|
|1|0.8734|
|2|0.9012|
|3|0.9258|
|4|0.9511|

Only the numerical observations are used during forecasting.

---

# Dataset 2 — Influenza Surveillance Data

## Description

The second dataset contains real influenza surveillance records collected over multiple epidemiological weeks.

Unlike Mackey–Glass, this dataset represents real-world observations and therefore contains

- noise,
- irregular fluctuations,
- seasonal variations,
- highly skewed count distributions.

These characteristics make forecasting considerably more challenging.

---

## Forecasting Targets

Three independent forecasting problems are evaluated.

### 1. TOTAL SPECIMENS

Represents the total number of laboratory specimens collected during each surveillance period.

Characteristics

- largest magnitude
- relatively smoother dynamics
- lower variance compared with subtype counts

---

### 2. TOTAL A

Represents confirmed Influenza Type A cases.

Characteristics

- highly skewed
- intermittent peaks
- large seasonal outbreaks
- positive-valued counts

Because of the heavy-tailed distribution, a log1p transformation is applied before training.

---

### 3. TOTAL B

Represents confirmed Influenza Type B cases.

Characteristics

- sparse observations
- many small values
- higher uncertainty
- irregular fluctuations

A log1p transformation is also applied during training.

---

## File Location

```
data/raw/Specimens-Train.xlsx
```

---

## Dataset Summary

| Variable | Description |
|----------|-------------|
| TOTAL SPECIMENS | Number of laboratory specimens |
| TOTAL A | Confirmed Influenza Type A |
| TOTAL B | Confirmed Influenza Type B |

Each variable is treated as an independent univariate forecasting problem.

---

# Directory Organization

The repository separates original datasets from processed data to ensure reproducibility.

```
data/

├── raw/
│
│   ├── mackey_glass.csv
│   └── Specimens-Train.xlsx
│
└── processed/
```

---

## Raw Data

Contains the original datasets exactly as provided.

No modifications should be made to these files.

---

## Processed Data

Contains cleaned datasets generated automatically by the notebook.

Typical outputs include

- cleaned CSV files
- transformed datasets
- normalized values
- intermediate preprocessing outputs

---

# Data Preprocessing

Before constructing the Fuzzy Time Series model, each dataset undergoes a preprocessing pipeline designed to preserve temporal integrity while removing invalid observations.

The preprocessing procedure is identical for all datasets unless otherwise stated.

---

## Step 1 — Load Dataset

The dataset is imported using Pandas.

Supported formats

- CSV
- Excel (.xlsx)

---

## Step 2 — Remove Invalid Records

The following observations are removed automatically.

- missing values
- NaN
- infinite values
- non-numeric entries

This guarantees numerical consistency throughout the forecasting pipeline.

---

## Step 3 — Preserve Chronological Order

Unlike conventional machine learning tasks, forecasting requires maintaining the temporal ordering of observations.

Therefore,

❌ random shuffling is never performed.

The original sequence order is preserved throughout the entire experiment.

---

## Step 4 — Train/Test Split

Each dataset is divided chronologically.

Training set

80%

Testing set

20%

Illustration

```
|-------------------------------|
 Training           Testing
      80%              20%
|-------------------------------|
```

The split is performed strictly according to observation time.

---

## Step 5 — Teacher Forcing

Forecast evaluation follows the one-step-ahead teacher forcing strategy.

For each prediction,

history

    ↓

predict next value

    ↓

append the true observation

    ↓

predict again

instead of recursively using previous predictions.

Advantages include

- prevents error accumulation,
- fair comparison between models,
- consistent evaluation across parameter settings.

---

# Data Transformations

Different datasets require different preprocessing strategies.

## Mackey–Glass

No transformation is applied.

The original numerical values are used directly.

---

## TOTAL SPECIMENS

No transformation is applied because the variance remains relatively stable.

---

## TOTAL A

A logarithmic transformation is applied.

```
y = log(1 + x)
```

Advantages

- variance stabilization,
- reduced skewness,
- improved numerical stability,
- better fuzzy partition utilization.

After forecasting,

```
x = exp(y) − 1
```

is applied to recover the original scale.

Negative predictions are clipped to zero.

---

## TOTAL B

The same log1p transformation is used.

```
Training

  ↓

log1p

  ↓

FTS

  ↓

prediction

  ↓

expm1

  ↓

non-negative clipping
```

---

# Experimental Philosophy

The entire preprocessing pipeline follows one guiding principle:

**No information from the future is allowed to influence model training.**

Consequently,

- partition boundaries are estimated using only training data,
- universe of discourse uses only training observations,
- fuzzy rules are extracted exclusively from the training sequence,
- testing data are never used during model construction.

This protocol ensures that the reported forecasting performance accurately reflects real-world predictive scenarios and avoids data leakage.

---

# Methodology

The proposed forecasting framework follows the classical Fuzzy Time Series paradigm while extending it with Higher-Order modeling, frequency-aware inference, and a true hierarchical back-off mechanism.

Unlike implementations that rely on external FTS libraries, every stage of the algorithm has been implemented manually from first principles.

The complete forecasting workflow consists of the following stages:

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

Each stage is described in detail below.

---

# 1. Universe of Discourse

The first step in constructing a Fuzzy Time Series model is defining the **Universe of Discourse**, which specifies the numerical interval over which fuzzy sets are created.

Using an interval that is too narrow may cause boundary observations to fall outside the fuzzy space, while an excessively large interval decreases partition resolution.

Therefore, a small margin is added to both ends of the training data range.

The universe is defined as

\[
U=[\min(X_{train})-\delta,\;
\max(X_{train})+\delta]
\]

where

\[
\delta=0.05\times
(\max(X_{train})-\min(X_{train}))
\]

The 5% margin prevents edge effects during fuzzification while preserving the overall scale of the original data.

---

## Why Only Training Data?

The universe is estimated **exclusively** from the training observations.

Using test data during this step would introduce information leakage and invalidate the forecasting experiment.

Therefore,

- minimum value → training only
- maximum value → training only
- universe boundaries → training only

This guarantees a fair evaluation protocol.

---

# 2. Fuzzy Partitioning

Once the universe has been constructed, it is divided into several fuzzy regions.

Each region corresponds to one linguistic state.

Examples include

- Very Low
- Low
- Medium
- High
- Very High

although the implementation labels them numerically

A1

A2

A3

...

Am

where

m ∈ {7, 10, 15, 20, 30}

These partition counts are selected through grid search.

---

# Equal-Width Partitioning

The first partitioning strategy divides the universe into intervals of identical length.

The interval width is

\[
w=
\frac{U_{max}-U_{min}}{m}
\]

The center of each fuzzy set is

\[
c_i=
U_{min}
+
\left(i-\frac12\right)w
\]

Advantages

- simple implementation
- uniform coverage
- computationally efficient
- widely used in classical FTS literature

Limitations

- inefficient for skewed distributions
- sparse regions receive unnecessary partitions
- dense regions receive insufficient resolution

---

# Quantile-Based Partitioning

To better represent non-uniform datasets, a second partitioning strategy is implemented.

Instead of equally spaced intervals, fuzzy set centers are determined from empirical quantiles.

This allocates

more fuzzy sets

    ↓

to dense regions

and

fewer fuzzy sets

     ↓

to sparse regions.

Advantages

- adaptive resolution
- improved representation of skewed data
- better utilization of fuzzy rules

This strategy is particularly beneficial for epidemiological datasets where observations are highly concentrated near small values.

---

# Partition Selection

The notebook automatically evaluates

7 partitions

10 partitions

15 partitions

20 partitions

30 partitions

for every forecasting model.

The optimal number of partitions is selected using the smallest RMSE.

---

# 3. Membership Functions

After partitioning the universe, a membership function is assigned to every fuzzy set.

A membership function determines the degree to which a numerical observation belongs to each fuzzy region.

The implementation includes two different membership functions.

---

## Triangular Membership Function

This is the default membership function used throughout all reported experiments.

For a fuzzy set centered at

\[
c_i
\]

with neighboring centers

\[
c_{i-1},\;
c_{i+1}
\]

the membership degree is computed using a piecewise linear function.

The triangular shape provides

- simple interpretation
- efficient computation
- continuous overlap
- low computational cost

Because adjacent fuzzy sets overlap, one observation may belong partially to multiple fuzzy states.

---

### Advantages

✔ computational efficiency

✔ smooth transitions

✔ easy visualization

✔ interpretable fuzzy regions

✔ standard choice in FTS literature

---

## Gaussian Membership Function

For completeness and extensibility, Gaussian membership functions are also implemented.

The membership degree is computed as

\[
\mu(x)
=
\exp
\left(
-\frac{(x-c_i)^2}
{2\sigma^2}
\right)
\]

where

- \(c_i\) is the fuzzy center
- \(\sigma\) controls the spread

Gaussian functions produce smoother transitions between neighboring fuzzy sets.

Although not used in the final experiments, they remain available for future research and comparison studies.

---

# Membership Overlap

Neighboring fuzzy sets intentionally overlap.

This overlap provides

- robustness against noise,
- smoother fuzzification,
- reduced sensitivity to partition boundaries,
- improved interpretability.

Without overlap, small numerical perturbations could abruptly change the assigned fuzzy state, reducing forecasting stability.

---

# Membership Visualization

For every experiment, the notebook automatically generates plots showing

- fuzzy set centers,
- partition boundaries,
- membership curves,
- active regions.

These figures are stored in

```

outputs/plots/

```

and included in the project report.

---

# Implementation Details

The entire forecasting framework has been implemented from scratch using pure Python without relying on any dedicated Fuzzy Time Series libraries.

The implementation follows a modular design, where each stage of the forecasting pipeline is isolated into a logical component. This improves readability, maintainability, extensibility, and reproducibility.

The project is organized around a sequence of computational stages, beginning with data preprocessing and ending with performance evaluation and visualization.

---

# Overall Software Architecture

The implementation follows the pipeline illustrated below.

```

Input Dataset

    ↓

Data Preprocessing

    ↓

Universe Construction

    ↓

Partition Generation
 
    ↓

Membership Functions

    ↓

Fuzzification

    ↓

FLR Extraction

    ↓

FLRG Construction

    ↓

Forecasting Engine

    ↓

Defuzzification

    ↓

Evaluation Metrics

    ↓

Visualization

    ↓

Result Export

```

Each stage is implemented independently, allowing future extensions without modifying the remaining components.

---

# Core Components

The implementation consists of the following logical modules.

| Component | Responsibility |
|-----------|----------------|
| Data Loader | Import datasets |
| Preprocessing | Cleaning and train/test split |
| Universe Builder | Construct universe of discourse |
| Partition Generator | Generate fuzzy intervals |
| Membership Functions | Compute membership degrees |
| Fuzzification | Convert numerical observations into fuzzy states |
| FLR Builder | Generate fuzzy logical relationships |
| FLRG Builder | Aggregate relationships into rule groups |
| Forecast Engine | Produce predictions |
| Defuzzification | Convert fuzzy outputs into crisp values |
| Evaluation | Compute forecasting metrics |
| Visualization | Generate publication-quality figures |

---

# Data Loading

The implementation supports multiple input formats.

Supported formats include

- CSV
- Microsoft Excel (.xlsx)

The loader automatically

- detects numeric columns,
- removes invalid values,
- preserves chronological ordering,
- prepares the selected forecasting target.

No random sampling or shuffling is performed.

---

# Data Preprocessing Module

The preprocessing stage performs several operations before model construction.

These include

- removing missing values,
- removing non-numeric observations,
- removing infinite values,
- resetting indices,
- preserving temporal order,
- generating training and testing subsets.

The train/test split is always chronological.

```
Training 80%

     ↓

Testing 20%
```

This procedure prevents future information from leaking into the training phase.

---

# Universe Builder

The universe builder computes

```
minimum(training)

     ↓

maximum(training)

     ↓

5% margin

     ↓

Universe of Discourse
```

The universe is estimated only once during training and remains fixed throughout forecasting.

---

# Partition Generator

The partition generator creates fuzzy intervals over the universe.

Implemented strategies

### Equal Width

Uniform interval lengths.

Advantages

- simplicity
- efficiency
- reproducibility

---

### Quantile

Adaptive interval spacing based on empirical quantiles.

Advantages

- better resolution
- robust for skewed distributions
- improved representation of dense regions

---

# Membership Function Module

The membership module computes the membership degree of every observation with respect to every fuzzy set.

Implemented functions

## Triangular

Default implementation.

Characteristics

- linear
- interpretable
- efficient

---

## Gaussian

Implemented for experimentation.

Characteristics

- smooth
- differentiable
- wider overlap

The notebook allows switching between membership functions with minimal code modifications.

---

# Fuzzification Module

Each numerical observation is transformed into a fuzzy state.

The implementation follows the Maximum Membership Principle.

```
Numerical Value

     ↓

Membership Degrees

     ↓

Largest Membership

     ↓

Assigned Fuzzy State
```

Example

```
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

The fuzzified sequence becomes the symbolic representation used throughout the forecasting process.

---

# FLR Construction

Fuzzy Logical Relationships are extracted directly from the fuzzified sequence.

For First-Order models

```
A5

↓

A7
```

represents

```
A5 → A7
```

For Higher-Order models

```
(A2,A4,A5)

↓

A6
```

represents

```
(A2,A4,A5) → A6
```

Every valid transition observed in the training sequence is recorded.

---

# FLRG Construction

Rather than storing independent rules, the implementation groups relationships sharing identical antecedents.

Example

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

becomes

```
A3

↓

{A4:2 , A5:2}
```

Each FLRG stores

- antecedent
- consequent states
- occurrence frequencies

This representation preserves empirical transition probabilities.

---

# Rule Storage

Rules are internally stored using hash-based lookup structures.

Conceptually

```
Antecedent

    ↓

Dictionary

    ↓

Counter

    ↓

Frequency
```

This enables efficient retrieval during inference while supporting arbitrary forecasting orders.

---

# Forecasting Engine

The forecasting engine receives

- historical observations,
- model order,
- trained FLRG tables,

and returns the predicted next value.

The forecasting process consists of

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

For first-order forecasting

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

For higher-order forecasting

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

Instead of terminating the search, the implementation performs hierarchical back-off.

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

If no rule exists,

the previous observation is returned.

This strategy dramatically increases rule coverage while maintaining forecasting stability.

---

# Weighted Defuzzification

After identifying the matching FLRG,

every consequent contributes according to its frequency.

Workflow

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

This approach preserves information contained in repeated transitions and typically produces smoother forecasts than selecting a single consequent.

---

# Evaluation Module

Each experiment computes

- RMSE
- MAE
- MAPE

using one-step-ahead forecasting with teacher forcing.

For Influenza A and B,

predictions are transformed back to the original scale before evaluation.

---

# Visualization Module

The notebook automatically generates

- actual vs predicted plots,
- RMSE heatmaps,
- membership function diagrams,
- fuzzy partition visualizations,
- parameter comparison figures.

All figures are exported at publication quality.

---

# Result Export

Every experiment automatically exports

- prediction tables,
- evaluation metrics,
- selected hyperparameters,
- generated figures,
- summary tables.

The outputs are organized inside the `outputs/` directory to facilitate reproducibility and further analysis.

