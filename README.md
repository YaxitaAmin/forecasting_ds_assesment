# Global Weather Repository — Trend Forecasting & Advanced Analysis

> PM Accelerator Tech Assessment | Weather Trend Forecasting

---

## PM Accelerator Mission

PM Accelerator is the world's leading Product Manager training program.
Our mission is to accelerate the careers of aspiring and experienced Product Managers
through real-world projects, mentorship, and a global community.
We believe everyone deserves access to world-class PM education, regardless of background.
Visit us at [pmaccelerator.io](https://www.pmaccelerator.io)

---

## Project Overview

This project performs a comprehensive analysis of the **Global Weather Repository** dataset —
daily weather observations for capital cities worldwide, starting May 2024.

It covers both the Basic and Advanced assessment requirements:

| Requirement | Status |
|---|---|
| Data cleaning & preprocessing | Done |
| Exploratory Data Analysis (EDA) | Done |
| Temperature & precipitation visualizations | Done |
| Anomaly detection | Done |
| Multiple forecasting models | Done |
| Ensemble model | Done |
| Climate pattern analysis | Done |
| Air quality & environmental impact | Done |
| Feature importance (SHAP) | Done |
| Spatial / geographical analysis | Done |

---

## Repository Structure

```
├── Global_Weather_Forecasting.ipynb   # Main analysis notebook
├── README.md                          # This file
├── requirements.txt                   # Python dependencies
└── temperature_heatmap.html           # Folium interactive map (generated at runtime)
```

---

## Dataset

**Source:** [Kaggle — Global Weather Repository](https://www.kaggle.com/datasets/nelgiriyewithana/global-weather-repository/code)

- ~143,000+ daily records
- 41 features: temperature, wind, pressure, precipitation, humidity, visibility, air quality, moon phase, and more
- Coverage: May 2024 to present (daily updates)
- Scope: Capital cities across ~195 countries

Download the dataset from Kaggle and place it in the project root as:

```
GlobalWeatherRepository.csv
```

---

## Setup & Installation

### 1. Clone the repository

```bash
git clone https://github.com/YaxitaAmin/forecasting_ds_assesment.git
cd forecasting_ds_assesment
```

### 2. Install dependencies

```bash
pip install -r requirements.txt
```

### 3. Download the dataset

Download `GlobalWeatherRepository.csv` from [Kaggle](https://www.kaggle.com/datasets/nelgiriyewithana/global-weather-repository) and place it in the project root.

### 4. Launch the notebook

```bash
jupyter notebook Global_Weather_Forecasting.ipynb
```

---

## Methodology

### Data Cleaning

- Parsed `last_updated` as datetime for time series indexing
- Dropped redundant unit columns (Fahrenheit, mph, inches, epoch timestamp)
- Imputed missing air quality values with column medians
- Forward-filled other numeric columns within each city, then backfilled
- Capped outliers at 1st/99th percentile using IQR method

### Exploratory Data Analysis

- Global temperature trend with 30-day rolling average
- Monthly seasonality for temperature, precipitation, and humidity
- Temperature distribution by continent (boxplots)
- Correlation heatmap across 12+ weather features
- Top wettest capitals, weather condition distribution, wind violinplots

### Anomaly Detection

- Isolation Forest (contamination=2%) on 6 core weather features
- Z-score analysis to identify extreme temperature events
- Country-level anomaly frequency ranking

### Forecasting Models

All models forecast global average daily temperature (train/test split: last 60 days as test).

| Model | Notes |
|---|---|
| Linear Regression | Baseline with sine/cosine seasonal features |
| SARIMA(2,1,2) | Classical time series with statsmodels |
| XGBoost | Gradient boosting with lag + rolling features |
| LightGBM | Faster gradient boosting, same feature set |
| Prophet | Trend + seasonality decomposition (optional) |
| Ensemble | Weighted average by inverse MAE |

Evaluation metrics: MAE, RMSE, R²

### Advanced Analyses

- **Climate patterns:** Seasonal decomposition, continent-level monthly trends, temperature variability by country, hottest/coldest months
- **Air quality:** PM2.5 by continent vs WHO guidelines, PM2.5 over time, AQ–weather correlation heatmap, most polluted capitals
- **Feature importance:** Random Forest MDI, XGBoost gain, SHAP summary and bar plots
- **Spatial analysis:** Plotly choropleth maps (temperature + PM2.5), bubble map (temp + precipitation), Folium heatmap, latitude band analysis

---

## Requirements

See `requirements.txt`. Core dependencies:

```
pandas
numpy
matplotlib
seaborn
plotly
scikit-learn
xgboost
lightgbm
statsmodels
prophet
shap
folium
notebook
```

---

## Key Findings

- Global average temperature follows a clear annual seasonal cycle, peaking July–August.
- XGBoost and LightGBM with lag/rolling features outperform SARIMA; the ensemble achieves best overall metrics.
- Asian capitals record the highest PM2.5 concentrations, frequently exceeding WHO guidelines; wind speed is the strongest dispersal factor.
- Humidity, seasonality (month/day-of-year), and pressure are the top predictors of temperature per SHAP analysis.
- A clear latitude-temperature gradient is confirmed: tropical bands are hottest, arctic bands coldest.

---

## Demo Video

[Link to demo video — add your Google Drive / YouTube / Vimeo link here]

---

*Submitted as part of the PM Accelerator Tech Assessment.*
