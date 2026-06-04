## Taken from other project - update for this project ##

## Customer Churn Prediction

Predicting customer churn for a UK-based e-commerce retailer using two 
years of transaction history. The goal was build a reliable ranking tool 
that allows a business to prioritize retention outreach toward the customers 
most likely to disengage.

## Key Finding

A tuned Gradient Boosting model achieves **~50% lift in churn 
identification over random selection**, with precision remaining stable 
between 45–50% across a wide coverage range (20%–70% of customers). 
While the model is not a high-accuracy binary classifier, it provides 
meaningful value as a targeting tool for retention campaigns where 
outreach cost is low relative to the cost of losing a customer.

## Project Structure

- `churn_analysis.ipynb` — Full analysis notebook (EDA, feature 
  engineering, modeling, evaluation, SHAP interpretation)
- `data/` — Data not included; source below
- `environment.yml` — Python dependencies

## Methodology

- **Data:** UCI Online Retail II dataset (Dec 2009 – Dec 2011, ~800K 
  transactions, ~4K customers after cleaning)
- **Churn definition:** No purchase in the subsequent 180-day period
- **Feature engineering:** RFM-style aggregation per customer per period 
  (transaction frequency, recency, AOV, UPT, AUR, SKU breadth, return 
  rate, streak length)
- **Models:** Logistic Regression (baseline) vs. Gradient Boosting 
  Classifier (tuned via Random Search and Bayesian Optimization with 
  Optuna)
- **Evaluation:** Average Precision (PR-AUC) prioritized over ROC-AUC 
  given class imbalance (~30% churn rate in test period)
- **Interpretability:** SHAP values (waterfall, beeswarm, bar plots)

## Results Summary

| Model | Avg. Precision | ROC-AUC |
|---|---|---|
| Logistic Regression | 0.420 | 0.704 |
| GBM – Random Search | 0.461 | 0.729 |
| GBM – Histogram Search | 0.453 | 0.719 |
| GBM – Bayesian Optimization | 0.458 | 0.723 |

## Data Source

[UCI Machine Learning Repository – Online Retail II](https://archive.ics.uci.edu/dataset/502/online+retail+ii)

## Tech Stack

Pandas · NumPy · scikit-learn · Optuna · SHAP · Matplotlib · Seaborn · Statsmodels

## Author

Hunter Phelan · [LinkedIn](https://www.linkedin.com/in/hunter-phelan-604/) · 
Vancouver, BC


---

## How to Run

### 1. Download the Data
Download the dataset from the [UCI Repository](https://archive.ics.uci.edu/dataset/502/online+retail+ii)
and place `online_retail_II.xlsx` in a `data/` folder in the project root.

### 2. Create and Activate the Environment
```bash
conda env create -f environment.yml
conda activate churn-project
```

### 3. Launch Jupyter and Open the Notebook
```bash
jupyter lab
```
Then open `churn_analysis.ipynb` and run all cells in order.