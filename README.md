# Credit Card Fraud — Statistical Analysis

## Overview
Statistical analysis of 284,807 real Mastercard transactions to identify fraud patterns and validate a fraud alert intervention using 5 hypothesis tests.

## Business problem
Can statistical analysis identify which transaction characteristics — amount, time of day, category — are 
significant fraud signals? And does a real-time SMS alert intervention significantly reduce fraud rate?

## Dataset
Kaggle — Credit Card Fraud Detection (ULB) https://www.kaggle.com/datasets/mlg-ulb/creditcardfraud
- 284,807 transactions
- 492 fraud cases (0.17% fraud rate)
- Features: Time, Amount, V1–V28 (PCA anonymised), Class

## Tests applied & findings

### 1. Z-test & T-test
**Question:** Is mean transaction amount significantly different between fraud and legit transactions?

**Result:** Yes (z=-3.0056, p=0.0027). Fraud mean €122.21 vs legit mean €88.29. Both tests converged at large sample sizes confirming Central Limit Theorem.

### 2. Chi-square — Amount category
**Question:** Is fraud rate independent of transaction amount category?

**Result:** No (χ²=33.78, p≈0.00). Fraud rate doubles from low (0.16%) to very high (0.38%) amount segments.

### 3. Chi-square — Time of day
**Question:** Is fraud rate independent of time of day?

**Result:** No (χ²=170.27, p≈0.00). Night transactions (0–6am) carry 0.47% fraud rate — 3x higher than daytime. Time of day is a stronger fraud signal than amount.

### 4. ANOVA + Tukey HSD
**Question:** Are mean amounts significantly different across all amount categories?

**Result:** Yes (F=136,675, p≈0.00). All 6 pairwise comparisons significant. Justifies separate risk thresholds per amount tier.

### 5. A/B Test + Power Analysis
**Question:** Does SMS fraud alert significantly reduce fraud rate?

**Result:** Yes (t=3.07, p=0.0022). 39.18% relative reduction — from 1.94% (control) to 1.18% (treatment). Minimum sample size calculated at 393 per group via power analysis before running test.

## Key insight
Highest risk fraud profile identified:
- Transaction amount above €500
- Occurring between 0–6am
- Statistically validated across multiple tests

## Limitations
- A/B test is simulated — live pilot recommended
- V1–V28 features anonymised via PCA
- Class imbalance (0.17% fraud) requires SMOTE (Synthetic Minority Oversampling Technique) for predictive modelling

## Tech stack
Python · pandas · numpy · scipy · statsmodels · seaborn · matplotlib · Jupyter Notebook

## Statistical concepts demonstrated
Z-test · T-test · Chi-square · ANOVA · Tukey HSD · A/B testing · Power analysis · Cohen's d · CLT · Type 1 & 2 error · FWER · Effect size · Class imbalance · Degrees of freedom

## Author
Rishita Bansal  
https://www.linkedin.com/in/rish-bansal/
https://github.com/RishitaBansal12