# Fraud Detection

A machine learning project that classifies simulated card transactions as legitimate or fraudulent, comparing Logistic Regression, Random Forest, XGBoost, and LightGBM within a highly imbalanced dataset.

## Project Overview

Financial institutions process enormous volumes of transactions every day, and only a very small fraction of these are fraudulent. This project addresses the problem of identifying fraudulent card transactions within a dataset where fraud represents roughly 0.5 percent of all activity, with particular focus on recall for the fraud class rather than overall accuracy.

## Dataset

The dataset contains 80,000 simulated card transactions, stratified sampled to preserve the original fraud rate from a larger source dataset. Each transaction includes details about the customer, the merchant, the amount, the time, and the location, with a genuine `is_fraud` label.

## Approach

Exploratory data analysis, data cleaning, feature engineering including frequency encoding for high cardinality columns, model comparison across four algorithms, stratified cross validation, hyperparameter tuning, final model selection, and interpretation using feature importance and SHAP analysis. Full details and reasoning are in the notebook.

## Results

| Model | Test Accuracy | Fraud Recall | Fraud F1 |
|---|---|---|---|
| Dummy Classifier | 99.47% | 0% | 0.00 |
| Random Forest | 99.61% | 26.76% | 0.42 |
| XGBoost | 99.81% | 70.42% | 0.80 |
| LightGBM | 99.60% | 70.42% | 0.79 |
| Tuned XGBoost | 99.84% | 71.83% | 0.82 |
| **Tuned LightGBM (final model)** | **99.84%** | **74.65%** | **0.83** |

## Key Findings

Transaction amount and hour of transaction were the strongest predictors of fraud, confirmed independently by both feature importance and SHAP analysis. Frequency encoding of merchant, city, and job captured meaningful signal from high cardinality columns that would otherwise have been unusable or noisy. An investigation into unusually old customer birth years, prompted by a suspicious 1924 entry, was tested directly and ruled out as evidence of fabricated identities, the fraud rate among elderly customers stayed close to the dataset average.

## Limitations

This model has not been validated against real transaction data and should be treated strictly as a research and demonstration project. See [DISCUSSION.md](./DISCUSSION.md) for a full discussion of dataset limitations, generalization concerns, and ethical considerations.

## Tech Stack

Python, Pandas, NumPy, scikit learn, XGBoost, LightGBM, SHAP, Matplotlib, Seaborn

## Author

Rebecca Akinboro
