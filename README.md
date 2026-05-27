# PM2.5 Air Quality Prediction — West Bengal

Regression-based modelling to predict PM2.5 concentration across West Bengal air quality monitoring stations, with full diagnostic analysis and SHAP-based interpretability.

---

## Overview

Air quality forecasting is a critical public health problem. This project builds and compares five regression models to predict PM2.5 levels using pollutant and meteorological features from **14 CPCB monitoring stations** across West Bengal.

The analysis progresses from interpretable statistical baselines (OLS) through gradient boosting ensembles, with rigorous diagnostics at each stage — multicollinearity checks (VIF), residual analysis, log-transformation for skewed targets, and SHAP feature attribution on the best model.

---

## Dataset

- **Source:** Central Pollution Control Board (CPCB), Government of India
- **Coverage:** 14 monitoring stations across West Bengal (`WB001` – `WB014`)
- **Features:** PM10, CO, NO₂, NOₓ, SO₂, NH₃, humidity, and station metadata
- **Target:** PM2.5 concentration (µg/m³)

---

## Approach

| Step | Details |
|------|---------|
| Data Loading | Multi-station CSV merge with station metadata join |
| EDA | Correlation heatmaps (raw + log-transformed), VIF analysis for multicollinearity |
| Preprocessing | Log transformation of skewed features, StandardScaler, train-test split (80/20) |
| Modelling | OLS (raw), OLS (log), Polynomial Ridge (degree 2), LightGBM, XGBoost |
| Evaluation | RMSE, MAE, R², Adjusted R² on original PM2.5 scale |
| Interpretability | SHAP summary plot and bar chart on LightGBM (25,000-sample explanation) |

---

## Models Compared

| Model | Description |
|-------|-------------|
| OLS — Raw | Baseline linear regression on standardised features |
| OLS — Log | Linear regression with log-transformed features and back-transformation |
| Polynomial Ridge (D=2) | Degree-2 expansion on top correlated features with Ridge regularisation |
| LightGBM | Gradient boosted trees with early stopping (1000 rounds, lr=0.05) |
| XGBoost | Gradient boosted trees with L1/L2 regularisation and early stopping |

---

## Key Visualisations

| File | What it shows |
|------|--------------|
| `correlation_heatmap_raw.png` | Feature–target correlations on raw scale |
| `correlation_heatmap_log.png` | Feature–target correlations after log transformation |
| `vif_chart.png` | Variance Inflation Factor — multicollinearity check |
| `ols_raw_plots.png` | OLS residual diagnostics (raw) |
| `ols_log_plots.png` | OLS residual diagnostics (log-transformed) |
| `polynomial_plots.png` | Polynomial regression fit |
| `lgb_avp.png` | LightGBM actual vs predicted plot |
| `xgb_avp.png` | XGBoost actual vs predicted plot |
| `model_comparison.png` | Side-by-side metric comparison across all models |
| `shap_summary.png` | SHAP dot plot — feature impact on LightGBM predictions |
| `shap_bar.png` | SHAP bar chart — mean absolute feature importance |

---

## Tech Stack

![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-150458?style=flat-square&logo=pandas&logoColor=white)
![NumPy](https://img.shields.io/badge/NumPy-013243?style=flat-square&logo=numpy&logoColor=white)
![Statsmodels](https://img.shields.io/badge/Statsmodels-4051B5?style=flat-square&logoColor=white)
![Scikit-Learn](https://img.shields.io/badge/scikit--learn-F7931E?style=flat-square&logo=scikit-learn&logoColor=white)
![LightGBM](https://img.shields.io/badge/LightGBM-02569B?style=flat-square&logoColor=white)
![XGBoost](https://img.shields.io/badge/XGBoost-FF6600?style=flat-square&logoColor=white)
![SHAP](https://img.shields.io/badge/SHAP-Interpretability-6A0DAD?style=flat-square&logoColor=white)
![Matplotlib](https://img.shields.io/badge/Matplotlib-11557C?style=flat-square&logoColor=white)
![Seaborn](https://img.shields.io/badge/Seaborn-4C8CBF?style=flat-square&logoColor=white)

---

## Repository Structure

```
pm25-air-quality-prediction/
│
├── Data/
│   ├── stations_info.csv          # Station metadata
│   ├── WB001.csv – WB014.csv      # Per-station pollution readings
│
├── PM25_WestBengal_Final_1.ipynb  # Main modelling notebook
├── code.ipynb                     # Alternate analysis notebook
│
├── correlation_heatmap_raw.png
├── correlation_heatmap_log.png
├── vif_chart.png
├── model_comparison.png
├── shap_summary.png
├── shap_bar.png
├── lgb_avp.png
├── xgb_avp.png
├── ols_raw_plots.png
├── ols_log_plots.png
├── polynomial_plots.png
│
└── PM2.5 Prediction Report (Regression).pdf   # Full written report
```

---

## Report

A detailed written report (`PM2.5 Prediction Report (Regression).pdf`) is included in the repository, covering methodology, results, and discussion.

---

*Part of coursework in Regression and Time Series Modelling (RTSM) — PGDBA, IIM Calcutta · IIT Kharagpur · ISI Kolkata*
