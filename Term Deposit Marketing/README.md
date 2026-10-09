# Term Deposit Subscription Prediction

## Project Overview

This project predicts whether a bank customer will subscribe to a **term deposit** using data from a direct marketing campaign.

The main objectives are to:

* Predict customer subscription (`yes/no`)
* Compare **Random Forest** and **XGBoost**
* Identify customers who are more likely to subscribe
* Determine important features influencing subscription
* Provide business recommendations for better customer targeting

## Dataset

The dataset contains approximately **40,000 customer records** with customer, financial, and campaign-related information.

The target variable is:

* `y = yes` → Customer subscribed
* `y = no` → Customer did not subscribe

The dataset is imbalanced, with approximately **7.24% subscribers** and **92.76% non-subscribers**.

> The original dataset is not included in this GitHub repository.

## Models Used

Two ensemble learning models were developed and optimized:

* **Random Forest**
* **XGBoost**

Hyperparameter tuning was performed using **GridSearchCV**, 5-fold cross-validation, and **Optuna** for XGBoost.

## Final Model Comparison

| Metric    | Random Forest |    XGBoost |
| --------- | ------------: | ---------: |
| Accuracy  |        91.26% | **91.95%** |
| Precision |        43.24% | **45.91%** |
| Recall    |    **66.30%** |     62.60% |
| F1 Score  |        52.34% | **52.97%** |
| ROC-AUC   |        0.9175 | **0.9256** |

**XGBoost Grid 4** was selected as the final model because it provided the strongest overall balance across the evaluation metrics.

## Key Findings

* XGBoost achieved **91.95% holdout accuracy**.
* Random Forest achieved slightly higher recall.
* XGBoost achieved better Accuracy, Precision, F1 Score, and ROC-AUC.
* Customers aged **60+**, students, retired customers, higher-balance customers, and selected campaign periods showed stronger historical subscription behavior.
* Call duration was highly predictive, but it should not be used for pre-call customer selection because it is only known after a call begins.

## Business Recommendation

Use the XGBoost model to **rank customers by subscription probability** rather than treating every customer equally.

Customer profile, financial information, loan status, and campaign timing can then be combined with the model predictions to improve call-center targeting.

## Project Structure

```text
Task2/
│
├── notebooks/
│   ├── exploration/
│   │   └── 01_Bank_Marketing_EDA.ipynb
│   └── modeling/
│       ├── 02_Random_Forest_Modeling.ipynb
│       ├── 03_XGBoost_Modeling.ipynb
│       └── 04_Model_Comparison_and_Business_Analysis.ipynb
│
├── reports/
│   ├── figures/
│   │   └── Bank_Term_Deposit_Analysis_Figures.pdf
│   └── summary/
│       └── Bank_Term_Deposit_Final_Report.pdf
│
└── README.md
```

## Detailed Report

For complete model evaluation, visualizations, customer segmentation, feature analysis, and business recommendations, see:

`reports/summary/Bank_Term_Deposit_Final_Report.pdf`

## Author

**Mitesh Sonani**
