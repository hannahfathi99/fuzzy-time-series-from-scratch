# Implementation

## System Architecture

The system is implemented as a modular pipeline with the following components:

1. Data Loader
2. Universe Constructor
3. Fuzzy Partitioning Engine
4. Membership Function Module
5. Fuzzification Engine
6. FLR / FLRG Builder
7. Forecasting Engine
8. Evaluation Module

---

## Pipeline Flow

Raw Time Series  
→ Cleaning  
→ Train/Test Split  
→ Universe of Discourse  
→ Partitioning  
→ Membership Functions  
→ Fuzzification  
→ FLR Extraction  
→ FLRG Construction  
→ Forecasting  
→ Defuzzification  
→ Evaluation  

---

## Core Modules

### 1. Universe Construction
Computes bounds from training data and applies safety margin δ.

---

### 2. Partitioning Module
Supports:
- Equal-width partitioning
- Quantile-based partitioning

Outputs fuzzy set centers and intervals.

---

### 3. Membership Function Module

Implements:

- Triangular membership function (default)
- Gaussian membership function (optional)

Each crisp input is mapped to a fuzzy label using max membership.

---

### 4. Fuzzification Engine

Converts numeric series into symbolic fuzzy sequence:

X(t) → A_i

Produces discrete sequence:
A1, A3, A5, ...

---

### 5. FLR / FLRG Construction

- Extract transitions from fuzzified sequence
- Store frequency counts in dictionary-like structure

Example:
A3 → {A4:2, A5:3}

---

### 6. Forecasting Engine

Supports:

#### FOFTS
Uses last state only.

#### HOFTS
Uses k-length history window.

If no match:
- Apply back-off strategy
- Fall back to lower-order rules
- Final fallback: persistence

---

### 7. Defuzzification

Weighted centroid calculation:

Prediction = weighted average of consequent centroids

Ensures smooth numerical output.

---

## Design Characteristics

- Fully modular
- No external fuzzy time series libraries
- Reproducible pipeline
- Extensible to higher-order systems
