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

---

# Experimental Setup

This section describes the experimental protocol adopted throughout the project.

The objective is to ensure that every reported result can be reproduced under identical conditions.

All experiments were performed using the same implementation, evaluation strategy, and preprocessing pipeline.

---

# Experimental Workflow

Every experiment follows the pipeline shown below.

```

Dataset

↓

Cleaning

↓

Train/Test Split

↓

Universe Construction

↓

Partitioning

↓

Membership Functions

↓

Fuzzification

↓

FLR Extraction

↓

FLRG Construction

↓

Forecasting

↓

Evaluation

↓

Visualization

↓

Export Results

```

This workflow is executed independently for every dataset.

---

# Forecasting Tasks

Four independent forecasting problems are evaluated.

| Dataset | Forecast Target |
|-----------|----------------|
| Mackey–Glass | Next Numerical Observation |
| Influenza | TOTAL SPECIMENS |
| Influenza | TOTAL A |
| Influenza | TOTAL B |

Each target is modeled independently using a separate FTS model.

---

# Model Orders

The implementation supports arbitrary forecasting orders.

The experiments evaluate

| Model | Order |
|--------|------|
| FOFTS | 1 |
| HOFTS | 2 |
| HOFTS | 3 |
| HOFTS | 4 |

For every order,

a complete FLRG table is generated.

---

# Partition Search

Different numbers of fuzzy partitions were evaluated.

The grid includes

| Number of Partitions |
|----------------------|
| 7 |
| 10 |
| 15 |
| 20 |
| 30 |

Each partition count produces a different fuzzy representation of the universe.

The optimal value is selected according to the lowest RMSE.

---

# Membership Functions

Two membership functions are available.

| Membership Function | Used |
|--------------------|------|
| Triangular | ✔ |
| Gaussian | Available |

Although Gaussian membership functions were implemented,

the reported experiments use triangular membership functions because they

- require fewer computations,
- are easier to interpret,
- are the most common choice in classical FTS literature.

---

# Partitioning Strategies

The framework supports two partition generation methods.

## Equal Width

Uniform interval lengths across the universe.

Suitable for

- continuous data
- approximately uniform distributions

---

## Quantile

Adaptive partition widths based on empirical quantiles.

Suitable for

- skewed distributions
- count data
- dense local regions

For the Influenza datasets,

both strategies are evaluated,

and the one producing the lowest RMSE is selected.

---

# Teacher Forcing Evaluation

Prediction is performed using one-step-ahead teacher forcing.

Instead of recursively feeding predicted values back into the model,

the true observation is appended after every prediction.

Workflow

```

Known History

↓

Predict Next Value

↓

Observe True Value

↓

Append True Value

↓

Predict Again

```

Advantages

- prevents error accumulation,
- ensures fair comparison,
- isolates model quality from recursive drift.

---

# Forecasting Horizon

The forecasting horizon is

```
One-Step Ahead
```

Only the immediate next observation is predicted.

This is the standard evaluation protocol in most FTS studies.

---

# Hyperparameter Grid Search

The notebook automatically evaluates every parameter combination.

Grid

```

Orders

1

2

3

4

×

Partitions

7

10

15

20

30

```

Total Configurations

```
4 × 5 = 20
```

Each configuration is trained and evaluated independently.

---

# Model Selection

The primary model selection criterion is

```
Minimum RMSE
```

Secondary metrics are reported for completeness.

- MAE
- MAPE

The best-performing configuration is automatically selected for each dataset.

---

# Evaluation Metrics

Three forecasting metrics are reported.

---

## Root Mean Squared Error (RMSE)

RMSE measures the square root of the average squared prediction error.

Characteristics

- sensitive to large errors,
- emphasizes forecasting accuracy,
- primary optimization criterion.

Lower values indicate better performance.

---

## Mean Absolute Error (MAE)

MAE computes the average absolute prediction error.

Advantages

- intuitive interpretation,
- robust to individual outliers,
- measured in the original unit of the data.

Lower values indicate better performance.

---

## Mean Absolute Percentage Error (MAPE)

MAPE measures prediction error relative to the magnitude of the observations.

Advantages

- scale independent,
- easy to compare across datasets,
- commonly used in forecasting literature.

For observations equal to zero,

appropriate safeguards are applied to avoid numerical instability.

---

# Logarithmic Transformation

Because Influenza Type A and Type B exhibit highly skewed count distributions,

a logarithmic transformation is applied before model construction.

Training

```
Original Counts

↓

log1p

↓

FTS Training
```

Prediction

```
Prediction

↓

expm1

↓

Original Scale

↓

Clip Negative Values
```

The reported evaluation metrics are always computed on the original scale.

---

# Rule Statistics

For every experiment,

the implementation records

- number of generated FLRGs,
- rule coverage,
- hit rate,
- fallback rate,
- back-off rate,
- unique fuzzy states,
- number of active partitions.

These statistics help explain the forecasting behavior of different model orders.

---

# Computational Complexity

Although FTS models are computationally lightweight,

their complexity depends on the forecasting order.

Approximate behavior

| Stage | Complexity |
|--------|------------|
| Partition Generation | O(m) |
| Membership Computation | O(n × m) |
| Fuzzification | O(n × m) |
| FLR Construction | O(n) |
| FLRG Generation | O(n) |
| Forecasting | O(1) average lookup |

where

- n = number of observations
- m = number of fuzzy partitions

Increasing the model order increases the number of possible antecedent patterns,

which may reduce rule density and increase sparsity.

---

# Reproducibility

To ensure reproducible experiments,

the following practices are adopted.

✔ Fixed preprocessing pipeline

✔ Fixed train/test split

✔ No random shuffling

✔ Identical evaluation protocol

✔ Automatic parameter search

✔ Consistent visualization settings

✔ Exported experiment summaries

Running the notebook from beginning to end reproduces all reported figures, tables, and evaluation metrics.

# Results & Analysis

The proposed Fuzzy Time Series framework was evaluated on two independent forecasting problems with fundamentally different characteristics. The first dataset, Mackey–Glass, represents a deterministic nonlinear chaotic system and is commonly used as a benchmark for time series forecasting algorithms. The second dataset consists of real influenza surveillance records containing weekly epidemiological counts, which exhibit substantial stochasticity, nonstationarity, and skewness.

All experiments followed the identical evaluation protocol presented in the Methodology section.

* Chronological 80% / 20% train–test split
* One-step-ahead forecasting
* Teacher forcing evaluation
* Grid search over model order and number of fuzzy partitions
* RMSE used for model selection
* MAE and MAPE reported as complementary evaluation metrics

For every dataset, both First-Order FTS (FOFTS) and Higher-Order FTS (HOFTS) models were trained and evaluated using exactly the same experimental pipeline.

---

# Evaluation Protocol

Each candidate model is uniquely defined by two hyperparameters:

* Model order
* Number of fuzzy partitions

The following search space was explored.

| Hyperparameter | Values            |
| -------------- | ----------------- |
| Order          | 1, 2, 3, 4        |
| Partitions     | 7, 10, 15, 20, 30 |

This results in twenty independent configurations for each forecasting target.

For Influenza datasets, both equal-width and quantile partitioning strategies were evaluated during experimentation. The configuration with the lowest RMSE was selected as the final model.

---

# Performance Metrics

Three standard forecasting metrics were used.

### Root Mean Squared Error (RMSE)

RMSE penalizes larger prediction errors more heavily and serves as the primary optimization criterion.

Lower RMSE indicates better predictive performance.

---

### Mean Absolute Error (MAE)

MAE measures the average magnitude of forecasting errors regardless of direction.

Unlike RMSE, MAE is less sensitive to occasional large deviations.

---

### Mean Absolute Percentage Error (MAPE)

MAPE measures prediction error as a percentage of the observed value.

This metric allows comparison between datasets with different numerical scales.

---

# Dataset 1 — Mackey–Glass

The Mackey–Glass dataset represents a nonlinear chaotic dynamical system with long-range temporal dependencies.

Such systems are particularly suitable for evaluating higher-order fuzzy models because future observations depend on several previous states rather than only the immediately preceding one.

After evaluating all parameter combinations, the following model achieved the lowest forecasting error.

| Model      | Order | Partitions |         RMSE |          MAE |       MAPE |
| ---------- | ----: | ---------: | -----------: | -----------: | ---------: |
| Best HOFTS | **3** |     **30** | **0.034076** | **0.025283** | **4.075%** |
| Best FOFTS |     1 |         30 |     0.050110 |     0.040302 |     6.766% |

The higher-order model reduced RMSE by approximately **32%** compared with the strongest first-order baseline.

---

### Rule Statistics

| Statistic        | Value |
| ---------------- | ----: |
| Order            |     3 |
| Partitions       |    30 |
| High-order FLRGs |   232 |
| Rule hit rate    |   97% |
| Fallback rate    |    3% |
| Back-off rate    |    9% |

The very high rule hit rate indicates that the learned fuzzy logical relationships successfully covered most temporal patterns encountered during testing.

Only a small proportion of predictions required persistence fallback, demonstrating that the proposed hierarchical back-off strategy effectively mitigated the sparsity introduced by higher-order antecedents.

---

### Interpretation

Several observations can be drawn from these experiments.

* Increasing the model order substantially improved forecasting accuracy.
* Larger numbers of fuzzy partitions produced finer representations of the state space.
* The hierarchical back-off mechanism prevented excessive forecasting failures caused by missing high-order rules.
* HOFTS successfully captured longer temporal dependencies characteristic of chaotic systems.

These findings are consistent with the theoretical motivation behind higher-order fuzzy time series.

---

### Generated Figures

The notebook automatically produces the following visualizations.

Figure 1

Actual vs Predicted Values (Best Configuration)

```
images/mackey_glass_prediction.png
```

Figure 2

RMSE Heatmap

```
images/mackey_glass_rmse_heatmap.png
```

Figure 3

Membership Functions

```
images/mackey_glass_membership_functions.png
```

Figure 4

Forecast Error Distribution

```
images/mackey_glass_error_distribution.png
```

---

# Dataset 2 — Influenza Surveillance

Unlike Mackey–Glass, influenza surveillance data originate from a real epidemiological monitoring system.

These observations exhibit

* measurement noise,
* abrupt seasonal fluctuations,
* irregular outbreaks,
* skewed count distributions,
* changing variance over time.

Consequently, forecasting this dataset is considerably more challenging.

Three independent forecasting targets were evaluated.

* TOTAL SPECIMENS
* TOTAL A
* TOTAL B

For TOTAL A and TOTAL B, a log1p transformation was applied before training to stabilize variance.

Predictions were transformed back to the original scale before evaluation.

---

# Target 1 — TOTAL SPECIMENS

### Best Model

| Model        | Order | Partitions | Partitioning |          RMSE |         MAE |       MAPE |
| ------------ | ----: | ---------: | ------------ | ------------: | ----------: | ---------: |
| Best Overall | **1** |     **15** | Equal Width  | **10617.999** | **8352.66** | **10.13%** |
| Best FOFTS   |     1 |         15 | Equal Width  |     10617.999 |     8352.66 |     10.13% |

---

### Rule Statistics

| Statistic       | Value |
| --------------- | ----: |
| Order           |     1 |
| Partitions      |    15 |
| Number of FLRGs |    13 |
| Rule hit rate   |  100% |
| Back-off rate   |    0% |
| Fallback rate   |    0% |

---

### Interpretation

Higher-order models did not improve forecasting accuracy for this target.

Possible explanations include

* limited temporal dependency,
* high observational noise,
* insufficient repeated higher-order patterns,
* increased rule sparsity.

Since every test pattern matched an existing first-order rule, increasing the model order only enlarged the rule space without introducing additional predictive information.

---

### Generated Figures

```
images/specimens_prediction.png

images/specimens_rmse_heatmap.png

images/specimens_membership_functions.png
```

---

# Target 2 — TOTAL A

TOTAL A contains significantly skewed weekly counts.

To reduce heteroscedasticity, the series was transformed using

log(1+x)

before fuzzy modeling.

---

### Best Model

| Model        | Order | Partitions | Partitioning | Transform |        RMSE |         MAE |       MAPE |
| ------------ | ----: | ---------: | ------------ | --------- | ----------: | ----------: | ---------: |
| Best Overall | **3** |     **30** | Equal Width  | log1p     | **3700.41** | **1700.00** | **25.62%** |
| Best FOFTS   |     1 |         30 | Equal Width  | log1p     |     3701.47 |     1955.95 |     32.06% |

---

### Rule Statistics

| Statistic        | Value |
| ---------------- | ----: |
| High-order FLRGs |   124 |
| Rule hit rate    |  100% |
| Back-off rate    | 35.4% |
| Fallback rate    |    0% |

---

### Interpretation

Although HOFTS achieved the lowest RMSE, the numerical improvement over FOFTS was relatively small.

The relatively high back-off rate indicates that more than one-third of predictions relied on lower-order rules rather than exact third-order matches.

This observation illustrates one of the primary challenges of higher-order fuzzy models: increasing the order rapidly expands the antecedent space while reducing the frequency of repeated patterns.

The proposed hierarchical back-off strategy successfully prevented complete rule failures and maintained full rule coverage throughout testing.

---

### Generated Figures

```
images/totalA_prediction.png

images/totalA_rmse_heatmap.png

images/totalA_membership_functions.png
```

---

# Target 3 — TOTAL B

TOTAL B exhibits even greater sparsity than TOTAL A, with numerous weeks containing relatively small case counts.

---

### Best Model

| Model        | Order | Partitions | Partitioning | Transform |        RMSE |         MAE |       MAPE |
| ------------ | ----: | ---------: | ------------ | --------- | ----------: | ----------: | ---------: |
| Best Overall | **1** |     **15** | Equal Width  | log1p     | **332.418** | **214.615** | **28.38%** |
| Best FOFTS   |     1 |         15 | Equal Width  | log1p     |     332.418 |     214.615 |     28.38% |

---

### Rule Statistics

| Statistic     | Value |
| ------------- | ----: |
| FLRGs         |    13 |
| Rule hit rate |  100% |
| Back-off rate |    0% |
| Fallback rate |    0% |

---

### Interpretation

For this dataset, higher-order models did not improve predictive performance.

The combination of sparse observations and irregular fluctuations produced insufficient repeated higher-order patterns for effective rule learning.

Consequently, the simpler FOFTS model provided the best balance between model complexity and forecasting accuracy.

---

### Generated Figures

```
images/totalB_prediction.png

images/totalB_rmse_heatmap.png

images/totalB_membership_functions.png
```

---

# Comparative Performance

The best-performing configuration for each forecasting target is summarized below.

| Dataset         | Best Order | Partitions |          RMSE |          MAE |       MAPE |
| --------------- | ---------: | ---------: | ------------: | -----------: | ---------: |
| Mackey–Glass    |      **3** |     **30** |  **0.034076** | **0.025283** | **4.075%** |
| TOTAL SPECIMENS |      **1** |     **15** | **10617.999** |  **8352.66** | **10.13%** |
| TOTAL A         |      **3** |     **30** |   **3700.41** |  **1700.00** | **25.62%** |
| TOTAL B         |      **1** |     **15** |   **332.418** |  **214.615** | **28.38%** |

---

# Discussion

The experimental results demonstrate that the effectiveness of Higher-Order Fuzzy Time Series models strongly depends on the temporal characteristics of the underlying data.

For the Mackey–Glass benchmark, which exhibits deterministic nonlinear dynamics and long-memory behavior, HOFTS clearly outperformed FOFTS. Incorporating multiple historical fuzzy states enabled the model to learn more informative fuzzy logical relationships, resulting in substantially lower prediction errors.

In contrast, the influenza surveillance datasets presented a considerably more challenging forecasting problem due to stochastic fluctuations, sparse observations, and abrupt changes. Under these conditions, increasing the model order frequently produced sparse FLRG tables with relatively few repeated antecedent patterns. Although the proposed hierarchical back-off strategy successfully maintained high rule coverage, the additional historical context did not consistently translate into improved predictive performance.

These findings highlight an important trade-off in fuzzy time series modeling. Increasing model order enhances representational power for deterministic systems but simultaneously enlarges the antecedent space, making rule sparsity a significant practical concern for noisy real-world datasets.

Overall, the experiments confirm that HOFTS is particularly advantageous when long-range temporal dependencies are present, whereas FOFTS remains an efficient and competitive choice for sparse or highly stochastic time series.


# Repository Outputs & Generated Files

One of the primary objectives of this repository is **full reproducibility**. Every experiment can be regenerated directly from the provided notebook, datasets, and source implementation without requiring any manual modification.

To facilitate reproducible research and simplify project navigation, all generated artifacts are automatically organized into dedicated directories.

---

# Output Directory Structure

The repository stores generated results using the following structure.

```text
outputs/
│
├── figures/
│   ├── mackey_glass/
│   ├── total_specimens/
│   ├── total_A/
│   └── total_B/
│
├── metrics/
│   ├── mackey_glass_metrics.csv
│   ├── total_specimens_metrics.csv
│   ├── total_A_metrics.csv
│   ├── total_B_metrics.csv
│   └── overall_results.csv
│
├── predictions/
│   ├── mackey_glass_predictions.csv
│   ├── total_specimens_predictions.csv
│   ├── total_A_predictions.csv
│   └── total_B_predictions.csv
│
├── flrgs/
│   ├── FOFTS/
│   └── HOFTS/
│
├── memberships/
│
├── grid_search/
│
├── logs/
│
└── output.zip
```

Each directory contains a specific category of exported experimental artifacts.

---

# Forecast Figures

All forecasting plots generated by the notebook are stored under

```text
outputs/figures/
```

Example

```text
outputs/
└── figures/
    ├── mackey_glass_prediction.png
    ├── mackey_glass_rmse_heatmap.png
    ├── mackey_glass_membership_functions.png
    ├── specimens_prediction.png
    ├── specimens_rmse_heatmap.png
    ├── totalA_prediction.png
    ├── totalA_rmse_heatmap.png
    ├── totalB_prediction.png
    └── totalB_rmse_heatmap.png
```

These figures are automatically exported in high resolution and can be directly inserted into reports or publications.

---

# Prediction Files

For every forecasting experiment, the notebook exports the predicted values together with the corresponding ground-truth observations.

Directory

```text
outputs/predictions/
```

Each CSV file contains

| Column           | Description                   |
| ---------------- | ----------------------------- |
| Time Index       | Observation index             |
| Actual           | Ground truth value            |
| Predicted        | Forecast generated by FTS     |
| Error            | Actual − Predicted            |
| Absolute Error   | Absolute prediction error     |
| Percentage Error | Relative prediction error (%) |

Example

```text
Time,Actual,Predicted,Error,AbsoluteError
501,0.892,0.881,0.011,0.011
502,0.905,0.899,0.006,0.006
...
```

These files allow users to reproduce all quantitative analyses and generate custom visualizations.

---

# Performance Metrics

Every evaluated configuration is summarized inside

```text
outputs/metrics/
```

Example

```text
overall_results.csv
```

contains

| Dataset         | Order | Partitions |      RMSE |      MAE |  MAPE |
| --------------- | ----: | ---------: | --------: | -------: | ----: |
| Mackey–Glass    |     3 |         30 |  0.034076 | 0.025283 | 4.075 |
| TOTAL SPECIMENS |     1 |         15 | 10617.999 |  8352.66 | 10.13 |
| TOTAL A         |     3 |         30 |   3700.41 |  1700.00 | 25.62 |
| TOTAL B         |     1 |         15 |   332.418 |  214.615 | 28.38 |

Additional CSV files provide the complete grid-search results for every dataset.

---

# Grid Search Results

All evaluated parameter combinations are exported for transparency and reproducibility.

Directory

```text
outputs/grid_search/
```

Each CSV contains

| Order | Partitions | RMSE | MAE | MAPE |
| ----- | ---------: | ---: | --: | ---: |
| 1     |          7 |  ... | ... |  ... |
| 1     |         10 |  ... | ... |  ... |
| 1     |         15 |  ... | ... |  ... |
| ...   |        ... |  ... | ... |  ... |
| 4     |         30 |  ... | ... |  ... |

These files make it straightforward to reproduce every heatmap presented in the report.

---

# Membership Function Exports

The fuzzy partitions generated during training are also exported.

Directory

```text
outputs/memberships/
```

Each exported file stores

* Universe of discourse
* Partition boundaries
* Fuzzy set centers
* Membership parameters

Example

```text
A1
A2
A3
...
A30
```

This enables users to inspect the exact fuzzy partitioning employed during forecasting.

---

# FLRG Exports

The learned Fuzzy Logical Relationship Groups are exported for both FOFTS and HOFTS models.

Directory

```text
outputs/flrgs/
```

Example

```text
outputs/flrgs/

FOFTS/

HOFTS/
```

Each file stores

Antecedent

↓

Consequent

↓

Frequency

Example

```text
A7 → A8 (15)

A8 → A8 (22)

A8 → A9 (4)

(A6,A7,A8) → A8 (11)

(A7,A8,A8) → A9 (6)
```

Exporting FLRGs allows detailed inspection of the learned fuzzy rule base.

---

# Experiment Logs

All experiment metadata are stored inside

```text
outputs/logs/
```

Example information includes

* execution time
* dataset name
* preprocessing options
* partitioning method
* model order
* random seed
* software version
* Python version

Maintaining detailed logs improves reproducibility and simplifies debugging.

---

# Report

The final report is included in

```text
reports/

FTS_Project1_Report_Hannah_Fathi_40360347.pdf
```

The report contains

* methodology
* mathematical formulation
* implementation details
* experimental configuration
* quantitative evaluation
* visual results
* comparative analysis
* conclusions

---

# Notebook

The complete implementation is provided as

```text
notebooks/

Fuzzy_Project1.ipynb
```

The notebook executes the entire workflow

Dataset Loading

↓

Preprocessing

↓

Partitioning

↓

Membership Construction

↓

Fuzzification

↓

FLRG Learning

↓

Forecasting

↓

Grid Search

↓

Evaluation

↓

Visualization

↓

Export Results

without requiring external scripts.

---

# Generated Images

All publication-quality figures are stored under

```text
images/
```

Typical outputs include

```text
images/

mackey_glass_prediction.png

mackey_glass_heatmap.png

mackey_glass_membership.png

specimens_prediction.png

totalA_prediction.png

totalB_prediction.png

rmse_comparison.png

membership_functions.png

forecast_errors.png

grid_search_results.png
```

Each image is exported at high resolution for direct inclusion in reports or academic papers.

---

# Compressed Release Package

For convenient distribution, the repository includes a compressed archive.

```text
output.zip
```

The archive contains

* generated figures
* exported CSV files
* prediction tables
* learned FLRGs
* membership definitions
* evaluation metrics
* notebook outputs

This package enables instructors and reviewers to inspect all experimental results without rerunning the notebook.

---

# Reproducibility Checklist

The repository is designed to ensure complete reproducibility.

✔ Original datasets included

✔ Source code implemented entirely from scratch

✔ No external fuzzy time series libraries

✔ Fixed experimental protocol

✔ Chronological train/test split

✔ Automatic hyperparameter search

✔ Deterministic evaluation

✔ Exported predictions

✔ Exported metrics

✔ Exported FLRGs

✔ Exported membership functions

✔ Publication-quality figures

✔ Complete notebook

✔ Final report

✔ Ready-to-use release package

---

# Summary

The repository provides a fully reproducible implementation of both First-Order and Higher-Order Fuzzy Time Series forecasting models. Every stage of the forecasting pipeline—from preprocessing and fuzzy partitioning to rule generation, prediction, visualization, and result export—is documented and accompanied by automatically generated artifacts.

By organizing outputs into dedicated directories and exporting intermediate as well as final results, the repository supports transparent experimentation, straightforward verification, and future extension. Researchers, students, and reviewers can reproduce all reported findings directly from the supplied notebook and datasets without relying on external fuzzy time series frameworks.


# Reproducibility, Limitations, Future Work & References

This section concludes the repository by discussing reproducibility, current limitations of the implementation, possible future research directions, and the primary references that motivated the project. The objective is to ensure that the repository is not only a complete course assignment but also a reproducible and extensible research implementation.

---

# Reproducibility

Reproducibility is a fundamental requirement in scientific computing and machine learning research. This repository has been designed so that every reported experiment can be regenerated directly from the provided datasets and notebook.

The implementation follows a deterministic experimental pipeline in which all preprocessing, model construction, hyperparameter search, forecasting, evaluation, and visualization steps are executed automatically.

To ensure reproducibility:

* Original datasets are included in the repository.
* All Fuzzy Time Series algorithms are implemented entirely from scratch.
* No external FTS libraries are used.
* The chronological train/test split is fixed.
* Experimental parameters are explicitly documented.
* Evaluation metrics are computed using identical procedures for every experiment.
* Generated figures, prediction tables, and performance summaries are automatically exported.
* The complete implementation is available in a single Jupyter Notebook.

Consequently, anyone cloning this repository and executing the notebook should obtain results consistent with those reported in the accompanying report, subject only to minor numerical differences arising from software versions or floating-point precision.

---

# Computational Complexity

The computational complexity of the implemented framework depends primarily on the number of observations, fuzzy partitions, and model order.

## Partition Construction

For a universe divided into (m) fuzzy sets, partition generation requires linear time with respect to the number of partitions.

**Complexity:**

O(m)

---

## Fuzzification

Each observation is evaluated against every membership function.

For

* n observations
* m fuzzy sets

the computational complexity becomes

O(nm)

---

## FLRG Construction

Rule generation requires a single pass through the fuzzified sequence.

For an order-(k) model,

Complexity:

O(n)

although memory consumption increases as higher-order antecedents produce a larger rule space.

---

## Forecasting

Each prediction consists of

* rule lookup,
* weighted defuzzification,
* optional hierarchical back-off.

Average prediction complexity remains close to constant time due to dictionary-based rule indexing.

Worst-case complexity is proportional to the selected model order.

---

## Grid Search

The complete experimental evaluation explores

* 4 model orders
* 5 partition counts

yielding

20 independent model configurations per forecasting target.

Since four forecasting targets are evaluated, the notebook trains and evaluates 80 individual FTS models.

---

# Limitations

Although the proposed implementation performs well across the selected datasets, several limitations should be acknowledged.

## Rule Sparsity

Higher-order FTS models rapidly increase the number of possible antecedent patterns.

As model order grows, many antecedents appear only once or never reoccur, leading to sparse FLRG tables.

Although the hierarchical back-off strategy alleviates this issue, it cannot completely eliminate sparsity.

---

## Fixed Membership Functions

The implementation employs manually constructed triangular and Gaussian membership functions.

The parameters of these functions are not optimized automatically.

Adaptive fuzzy partitioning could potentially improve forecasting performance.

---

## Single-Variable Forecasting

Each experiment models a univariate time series.

Interactions among multiple variables are intentionally ignored.

Consequently, external explanatory variables cannot influence predictions.

---

## Crisp Fuzzification

Each numerical observation is assigned to a single fuzzy state using the maximum membership principle.

Alternative approaches such as weighted fuzzification or probabilistic state assignments may preserve additional uncertainty information.

---

## Fixed Hyperparameter Grid

Only a predefined collection of

* model orders
* partition numbers

is evaluated.

More sophisticated optimization strategies could explore a substantially larger parameter space.

---

# Future Work

The current implementation provides a strong foundation for numerous future extensions.

Potential research directions include:

## Adaptive Partitioning

Automatically determine fuzzy partitions using optimization techniques such as

* Genetic Algorithms
* Particle Swarm Optimization
* Differential Evolution

rather than fixed equal-width or quantile partitions.

---

## Automatic Membership Learning

Instead of predefined triangular membership functions, future work could estimate membership parameters directly from data using optimization or clustering techniques.

---

## Interval Type-2 Fuzzy Sets

Type-2 fuzzy systems provide improved robustness under uncertainty and measurement noise.

Replacing Type-1 fuzzy sets with Interval Type-2 fuzzy sets represents a natural extension.

---

## Multivariate Fuzzy Time Series

The current implementation considers only one variable at a time.

Future work could incorporate multiple correlated variables, enabling richer forecasting models.

---

## Hybrid Forecasting Models

Combining FTS with modern machine learning methods may improve predictive accuracy.

Examples include

* FTS + Neural Networks
* FTS + LSTM
* FTS + Transformer models
* FTS + Gradient Boosting

Such hybrid architectures could preserve interpretability while exploiting nonlinear feature learning.

---

## Automatic Model Selection

Bayesian optimization or evolutionary search could replace exhaustive grid search for selecting

* model order,
* partition count,
* membership parameters.

---

## Parallel Computation

Current experiments are executed sequentially.

Parallelizing the grid search across CPU cores would substantially reduce computation time for larger datasets.

---

# Educational Value

Beyond its forecasting performance, this repository serves as a comprehensive educational resource for students studying fuzzy systems and soft computing.

Every stage of the Fuzzy Time Series pipeline is implemented explicitly, allowing readers to understand:

* construction of the universe of discourse,
* fuzzy partitioning,
* membership function design,
* fuzzification,
* fuzzy logical relationship generation,
* higher-order rule construction,
* weighted defuzzification,
* hierarchical back-off,
* model evaluation.

Unlike implementations that rely on specialized libraries, every algorithmic component is visible and modifiable.

---

# Citation

If this repository contributes to your research, coursework, or academic publication, please cite it using the accompanying `CITATION.cff` file.

**Suggested citation:**

```text
Fathi, H. (2025).
Fuzzy Time Series Forecasting from Scratch:
Implementation of FOFTS and HOFTS in Python.
Shiraz University,
Fuzzy Sets and Systems Course Project.
```

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
