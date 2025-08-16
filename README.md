# BigDataProject — Customer Segmentation & Recommender Notebook

This repository contains two Jupyter notebooks used for a retail/customer analytics project:

- `Assignment_PartB.ipynb` — Customer-level feature engineering, exploratory visualizations, outlier handling, and K-Means clustering to segment customers.
- `Assignment_PartC.ipynb` — End-to-end recommender experiments: baseline, Frequent Pattern Mining (FPM), Collaborative Filtering (CF), SVD-based recommendations, and a hybrid blend.

Datasets
- The notebook expects CSV files located in the `dataset_looker/` directory. Files included in this repo (example): `orders.csv`, `order_items.csv`, `products.csv`, `users.csv`, `distribution_centers.csv`.

Quickstart (Windows)
1. Create and activate a Python environment (recommended):

```powershell
py -3 -m venv .venv
.\.venv\Scripts\Activate.ps1   # PowerShell
# or for cmd.exe
.\.venv\Scripts\activate.bat
```

2. Install dependencies:

```cmd
pip install -r requirements.txt
```

3. Start Jupyter Notebook and open the notebooks:

```cmd
jupyter notebook
```

Notes on what the notebooks do
- Both notebooks load CSVs from `./dataset_looker`, merge `order_items`, `products` and `users`, then perform date parsing, feature engineering and filtering.
- `Assignment_PartB.ipynb` focuses on customer aggregation and K-Means clustering. It includes scaling, elbow plots, cluster assignment, and cluster visualizations.
- `Assignment_PartC.ipynb` prepares train/test splits (time-based), creates interaction matrices, computes popularity tables, implements multiple recommenders (global baseline, month-based baseline, FPM, CF, SVD, hybrid), and evaluates with precision/recall/F1/hit-rate/coverage metrics.

Assumptions and caveats
- The notebooks use inline matplotlib (%matplotlib inline). Running them in a headless environment (no display) may require a non-interactive backend or saving plots to files.
- The `mlxtend` library is used for FPM and association rules and may require C extensions; wheels are available for common Python versions.
- The notebooks rely on date columns; if the CSVs have unexpected date formats, the provided robust parser attempts multiple formats and fills missing with medians.

Suggested next steps
- Add a small example script to run a subset of the notebooks automatically and save evaluation CSVs.
- Pin dependency versions after a successful run and add a few unit tests for the helper functions.

If you'd like, I can:
- Run a quick dependency installation and smoke-run the notebooks (fast mode) and report any missing packages or runtime errors.
- Add a script to produce evaluation CSV outputs for each model.
