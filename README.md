# Fraud Detection Using Machine Learning

## 📊 Project Overview

This project applies advanced machine learning techniques to detect fraud in applications involving Personal Identifying Information (PII), such as names, addresses, Social Security Numbers (SSNs), and phone numbers. Using a synthetic but realistic dataset of 1 million application records, we developed a fraud detection system capable of real-time decision-making with high accuracy and low false positive rates.

---

## 🧠 Key Objectives

•⁠  ⁠Identify fraudulent applications involving identity misuse or synthetic identities.
•⁠  ⁠Create robust models that generalize well over time.
•⁠  ⁠Balance fraud detection accuracy with cost-effectiveness (minimizing false positives).
•⁠  ⁠Recommend an optimal fraud probability cutoff for operational use.

---

## 🗃️ Dataset Description

•⁠  ⁠*Type*: Synthetic dataset resembling real-world application data.
•⁠  ⁠*Size*: 1,000,000 records.
•⁠  ⁠*Fields*: Names, SSNs, DOBs, phone numbers, addresses, fraud labels, etc.
•⁠  ⁠*Goal*: Predict the likelihood of an application being fraudulent.

---

## 🧹 Data Cleaning

Key cleaning steps:
•⁠  ⁠Replaced placeholder values (e.g., ⁠ 999999999 ⁠ for SSNs) with unique IDs.
•⁠  ⁠Created ⁠ fulladdress ⁠ by combining ⁠ address ⁠ and ⁠ zip5 ⁠.
•⁠  ⁠Repaired common date errors in ⁠ dob ⁠.
•⁠  ⁠Converted numeric identifiers (like phone and SSNs) into categorical features.

---

## 🛠️ Feature Engineering

•⁠  ⁠*Velocity Features*: Measured how often identifiers like SSN or phone numbers appear over rolling time windows.
•⁠  ⁠*Normalized Velocity*: Application activity normalized over time to detect spikes.
•⁠  ⁠*Cumulative and Relative Velocity*: Captured aggregated behavior.
•⁠  ⁠*Entity Combinations*: Created composite identifiers (e.g., ⁠ name_dob ⁠, ⁠ address_ssn ⁠) for deeper insights.

---

## 🔍 Feature Selection

Used *LightGBM* and *Random Forest* models with:
•⁠  ⁠*Forward and Backward Selection* strategies.
•⁠  ⁠Optimal config: ⁠ num_filter = 100 ⁠, ⁠ num_wrapper = 20 ⁠ (LightGBM).
•⁠  ⁠Resulted in a consistent and reduced feature set with high predictive power.

---

## 🤖 Models Explored

| Model              | Notes |
|-------------------|-------|
| Logistic Regression | Stable baseline, interpretable |
| Decision Tree       | Good interpretability, some overfitting |
| Random Forest       | Improved robustness, but performance varied |
| LightGBM            | High performance, sensitive to tuning |
| Neural Network      | Powerful but prone to overfitting |
| *CatBoost*        | ⭐ Final choice — best generalization & stability |

---

## 🏆 Final Model: CatBoost

*Why CatBoost?*
•⁠  ⁠Handles categorical data natively.
•⁠  ⁠Low variance in Out-of-Time (OOT) performance.
•⁠  ⁠Strong fraud detection rate (FDR) of *0.68%* on OOT data.
•⁠  ⁠Estimated fraud savings: *$3.1 billion*.

*Key Hyperparameters:*
•⁠  ⁠⁠ subsample ⁠: 0.85–0.9
•⁠  ⁠⁠ max_depth ⁠: 6–15
•⁠  ⁠⁠ learning_rate ⁠: 0.01–0.1
•⁠  ⁠⁠ n_estimators ⁠: 100–200
•⁠  ⁠⁠ l2_leaf_reg ⁠: 0.1–1

---

## 💰 Financial Analysis

Three key curves:
•⁠  ⁠*Fraud Detection Curve*: More fraud is detected as cutoff increases.
•⁠  ⁠*False Positive Cost Curve*: Shows the cost of wrongly flagged applications.
•⁠  ⁠*Total Cost Curve*: Helps choose the optimal operational point.

*📌 Recommended Cutoff: **0.68%*
•⁠  ⁠Maximizes fraud savings while minimizing false positives.

---

## 📈 Results Summary

| Dataset | Fraud Detection Rate (FDR) | Notes |
|---------|----------------------------|-------|
| Train   | High                       | Good fit |
| Test    | Consistent                 | Minimal overfitting |
| OOT     | 0.68%                      | Strong generalization |

---

## 📦 Project Structure
├── README.md
├── data/
│   └── application_data.csv
├── notebooks/
│   ├── 01_data_cleaning.ipynb
│   ├── 02_feature_engineering.ipynb
│   ├── 03_modeling.ipynb
├── models/
│   └── final_catboost_model.pkl
├── scripts/
│   └── fraud_detection_pipeline.py
---

## 📚 Appendix

- Data distributions (SSN, DOB, address, phone) visualized for anomaly detection.
- Summary statistics for all fields included in the report.

