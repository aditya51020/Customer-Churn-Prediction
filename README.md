# Customer Churn Prediction ⭐

Predicting which customers are likely to stop using a telecom service (churn),
so the business can act early with retention offers.

## Problem

Kaunse customers service chhod sakte hain? — a binary classification problem:
given a customer's demographics, account details, and subscribed services, predict
whether they will churn (`Yes` / `No`).

## Dataset

[Telco Customer Churn](https://www.kaggle.com/datasets/blastchar/telco-customer-churn)
— 7,043 customers, 21 features (demographics, account info, services subscribed).
Included in this repo at `data/Telco-Customer-Churn.csv`.

## Tech Stack

- Python, Pandas, NumPy
- Matplotlib, Seaborn (visualization)
- Scikit-learn (modeling)

## Models

- Logistic Regression (interpretable baseline)
- Random Forest (non-linear, stronger predictive power)

## What's covered

- Exploratory Data Analysis (EDA)
- Missing value handling
- Categorical encoding
- Feature selection
- Train/test split
- Model training & evaluation (accuracy, precision, recall, F1, ROC-AUC, confusion matrix)
- Feature importance

## Project structure

```
Customer Churn Prediction/
├── data/
│   └── Telco-Customer-Churn.csv
├── Customer_Churn_Prediction.ipynb
├── requirements.txt
└── README.md
```

## Getting started

```bash
git clone <your-repo-url>
cd "Customer Churn Prediction"
pip install -r requirements.txt
jupyter notebook Customer_Churn_Prediction.ipynb
```

## Results

Both models are trained and compared on accuracy, precision, recall, F1 score, and
ROC-AUC (see the notebook's Model Comparison section). Random Forest generally
edges out Logistic Regression on ROC-AUC/F1 by capturing non-linear feature
interactions, while Logistic Regression stays valuable for its interpretability.

Top churn drivers (from Random Forest feature importance): **tenure**, **contract
type**, **monthly charges**, and **online security / tech support add-ons** — new,
month-to-month, high-paying customers without add-on protections churn the most.

## Interview answer

> "I framed customer churn as a binary classification problem. After EDA, I found the
> data was moderately imbalanced (~27% churn) and had a data-quality issue where
> `TotalCharges` was stored as text with blanks for brand-new customers — I imputed
> those with 0 since they hadn't been billed yet. I label-encoded categorical
> features, split the data with stratification to preserve the class ratio, and
> trained both Logistic Regression (for interpretability and a fast baseline) and
> Random Forest (for stronger predictive power via non-linear feature interactions).
> I evaluated both with precision, recall, F1, and ROC-AUC rather than accuracy alone,
> since accuracy is misleading on imbalanced data. Feature importance from the Random
> Forest confirmed that tenure, contract type, and monthly charges are the strongest
> churn signals — which lines up with business intuition and gives the retention team
> concrete levers to act on, like incentivizing longer contracts for new customers."
