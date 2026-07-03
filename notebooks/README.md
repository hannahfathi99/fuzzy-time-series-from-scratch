# Notebooks

This directory contains the Jupyter notebook used to reproduce every experiment presented in the project report.

---

# Available Notebook

```
Fuzzy_Project1.ipynb
```

The notebook implements the complete forecasting pipeline, including

* data loading
* preprocessing
* fuzzy partitioning
* membership function construction
* fuzzification
* FLRG generation
* FOFTS forecasting
* HOFTS forecasting
* true hierarchical back-off
* evaluation
* visualization
* export utilities
* interactive forecasting interface

---

# Execution Order

The notebook is organized into consecutive sections.

1. Imports and configuration

2. Dataset loading

3. Evaluation metrics

4. Fuzzy Time Series implementation

5. Visualization utilities

6. Grid search

7. Mackey–Glass experiments

8. Influenza experiments

9. Interactive prediction

10. Packaging and export

Each section should be executed sequentially.

---

# Outputs

Executing the notebook automatically generates

* forecast figures
* membership function plots
* RMSE comparison plots
* FLRG exports
* grid-search results
* appendix tables
* packaged output files

These outputs are stored in the repository's results directory.

---

# Reproducibility

Random seeds are fixed to ensure deterministic experimental results.
