# MSCS 634 – Lab 1: Data Visualization, Preprocessing & Statistical Analysis

## Purpose

This lab explores a synthetic retail sales dataset (500 rows, 11 features) through four stages of the data analytics pipeline:

1. **Data Collection** – Generation and loading of a realistic sales dataset.
2. **Data Visualization** – Six chart types (scatter, line, bar, histogram, box, pie) to uncover patterns.
3. **Data Preprocessing** – Missing-value imputation, IQR-based outlier removal, dimension/sample reduction, and feature scaling/discretization.
4. **Statistical Analysis** – Central tendency, dispersion measures, and correlation analysis.

## Key Insights

| Area | Finding |
|------|---------|
| Revenue Drivers | Quantity and Unit Price are the strongest predictors of Revenue. |
| Outliers | IQR analysis flagged ~30+ extreme Revenue values; removing them tightened distributions significantly. |
| Missing Data | ~5 % of Discount, Customer Rating, and Shipping Cost values were missing; median fill, forward fill, and mean fill strategies were applied respectively. |
| Correlation | Revenue–Profit correlation is very high (~0.9+), confirming profit is a direct function of revenue in this dataset. Discount has a slight negative relationship with Revenue. |

## Challenges & Decisions

- **Pandas version compatibility:** Newer versions of pandas deprecated `resample('M')` in favor of `'ME'` and removed the `method` parameter from `fillna()`. Code was updated to use `.ffill()` / `.bfill()` and `'ME'` accordingly.
- **Outlier threshold:** The standard 1.5×IQR rule was chosen over the 3×IQR rule to demonstrate a more aggressive cleaning approach; in practice the threshold should be domain-driven.
- **Scaling choice:** Both Min-Max and Z-score scaling are demonstrated side-by-side so readers can compare outputs.

## Repository Contents

```
├── MSCS_634_Lab_1.ipynb   # Jupyter Notebook with all code and outputs
├── retail_sales.csv       # Generated dataset
└── README.md              # This file
```

## How to Run

```bash
pip install pandas numpy matplotlib seaborn scikit-learn jupyter
jupyter notebook MSCS_634_Lab_1.ipynb
```
