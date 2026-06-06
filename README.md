# Fraud Detection System — Adey Innovations

A machine learning system that detects fraudulent transactions
across e-commerce and bank credit card data.

---

## Project Overview

Adey Innovations needs a unified fraud detection system that handles:
- **E-commerce transactions** — with user, device, and behavioral data
- **Bank credit card transactions** — with anonymized PCA features

---

## Project Structure

```
fraud-detection/
├── data/
│   ├── raw/              # Original datasets (git ignored)
│   └── processed/        # Cleaned datasets (git ignored)
├── notebooks/
│   ├── eda-fraud-data.ipynb        # Task 1 - EDA & Preprocessing
│   ├── eda-creditcard.ipynb        # Task 1 - Credit Card EDA
│   ├── feature-engineering.ipynb   # Task 1 - Feature Engineering
│   ├── modeling.ipynb              # Task 2 - Model Training
│   └── shap-explainability.ipynb   # Task 3 - SHAP Analysis
├── src/                  # Reusable source code
├── tests/                # Unit tests
├── models/               # Saved trained models
├── scripts/              # Standalone scripts
├── requirements.txt      # Python dependencies
└── .github/workflows/    # CI/CD pipeline
```

---

## Datasets

| Dataset | Description | Rows |
|---|---|---|
| Fraud_Data.csv | E-commerce transactions | 151,112 |
| IpAddress_to_Country.csv | IP to country mapping | 138,846 |
| creditcard.csv | Bank credit card transactions | 284,807 |

---

## Task 1 — Data Analysis and Preprocessing

### What was done
- Loaded and explored all three datasets
- Removed 1,081 duplicate rows from credit card data
- Fixed datetime types for signup and purchase times
- Merged e-commerce data with IP geolocation table
- Engineered new fraud signal features
- Applied SMOTE to balance training data

### Key Findings

| Finding | Value |
|---|---|
| E-commerce fraud rate | 9.36% |
| Credit card fraud rate | 0.17% |
| New account fraud rate | 87.34% |
| Rows lost in IP merge | 21,966 |

### Features Engineered
- `time_since_signup` — hours between signup and purchase
- `hour_of_day` — hour the transaction happened
- `day_of_week` — day the transaction happened
- `transaction_velocity` — purchases per hour per user
- `is_new_account` — account less than 24 hours old
- `country` — derived from IP address lookup

### Class Imbalance Handling
- Applied SMOTE on training data only
- Balanced fraud ratio from 9.36% → 50%
- Test data left untouched and real

---

## How to Run

```bash
# 1. Clone the repo
git clone https://github.com/YOUR-USERNAME/fraud-detection.git
cd fraud-detection

# 2. Create virtual environment
python -m venv venv
source venv/bin/activate  # Windows: venv\Scripts\activate

# 3. Install dependencies
pip install -r requirements.txt

# 4. Open notebooks
jupyter lab
```

---

