# Retail Sales Forecasting using Time Series & Machine Learning (Rossmann Store Sales)

## Project Overview

This project develops a **retail sales forecasting pipeline** using the **Rossmann Store Sales** dataset.  
The objective is to predict **daily store-level sales** using historical transaction data and store metadata, and to compare different forecasting approaches for practical retail demand planning.

The project combines:

- **Store-level forecasting** with machine learning models:
  - Baseline (naive lag-based forecast)
  - Random Forest
  - XGBoost
- **Aggregate daily sales forecasting** using:
  - Prophet (for portfolio-level trend and seasonality analysis)

This project demonstrates a realistic business-oriented forecasting workflow, including:

- Data integration from multiple sources
- Time series feature engineering
- Forecasting model comparison
- Model evaluation using business-relevant metrics
- Interpretability via feature importance
- Trend and seasonality analysis at aggregate level

---

## Business Problem

Retail companies need accurate sales forecasts to support:

- Inventory planning
- Workforce scheduling
- Promotion strategy
- Operational decision-making
- Demand-driven business planning

The goal of this project is to build a forecasting system that predicts future sales and helps identify the strongest modeling approach for structured retail data.

---

## Dataset

**Dataset:** Rossmann Store Sales (Kaggle)

Files used:

- `train.csv` → historical daily sales data
- `store.csv` → store metadata and attributes

Files not used directly in this project:

- `test.csv`
- `sample_submission.csv`

### Key Variables

- `Sales` → target variable
- `Store` → store identifier
- `Date` → transaction date
- `Promo` → whether a promotion is active
- `StateHoliday` → holiday indicator
- `SchoolHoliday` → school holiday indicator
- `StoreType` → type of store
- `Assortment` → assortment type
- `CompetitionDistance` → distance to nearest competitor
- `Promo2` / `PromoInterval` → extended promotion information

---

## Project Structure

```bash
rossmann-sales-forecasting/
│
├── data/
│   ├── raw/
│   │   ├── train.csv
│   │   ├── store.csv
│   └── processed/
│
├── notebooks/
│   ├── rossmann_forecasting.ipynb
│
├── outputs/
│   ├── store_level_model_comparison.csv
│   ├── aggregate_prophet_results.csv
│   ├── prophet_aggregate_forecast_results.csv
│   ├── xgboost_feature_importance.csv
│   ├── xgboost_store_level_predictions.csv
│
├── images/
│   ├── model_comparison.png
│   ├── xgboost_feature_importance.png
│   ├── prophet_forecast.png
│
├── README.md
└── requirements.txt
