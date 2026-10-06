# Time-Series Forecasting with ARIMA / SARIMA

An end-to-end time-series forecasting project that analyzes historical demand patterns, evaluates stationarity, selects ARIMA models, and generates future demand forecasts.

## Project Overview

This project implements a complete statistical forecasting workflow:

- Exploratory time-series analysis
- Trend and seasonal decomposition
- Augmented Dickey-Fuller (ADF) stationarity testing
- First- and second-order differencing
- Chronological train-test splitting
- Naive forecasting baseline
- ARIMA model selection using AIC
- Forecast evaluation using RMSE and MAPE
- 30-day future demand forecasting

## Dataset

The project uses a daily demand dataset containing:

- `date` — observation date
- `demand` — daily demand
- `marketing_event` — marketing event indicator
- `holiday` — holiday indicator

The dataset contains **30 daily observations** from June 1, 2026 to June 30, 2026.

## Methodology

```text
Raw Demand Data
       │
       ▼
Exploratory Analysis
       │
       ▼
Time-Series Decomposition
       │
       ▼
ADF Stationarity Test
       │
       ▼
Differencing
       │
       ▼
Train / Test Split
       │
       ▼
Naive Baseline
       │
       ▼
ARIMA Model Selection
       │
       ▼
RMSE + MAPE Evaluation
       │
       ▼
Best Model: ARIMA(0,2,2)
       │
       ▼
30-Day Future Forecast

Stationarity Analysis

The original demand series was non-stationary:

ADF p-value: 0.7867

After first-order differencing, the series remained non-stationary:

ADF p-value: 0.1943

Second-order differencing achieved stationarity:

ADF p-value: 6.09 × 10⁻²⁸

Therefore, the candidate ARIMA models were evaluated using d = 2.

Model Evaluation

The naive baseline achieved:

Model	RMSE	MAPE
Naive Baseline	15.2698	6.80%
ARIMA(0,2,2)	13.2212	6.44%

ARIMA(0,2,2) achieved the best test-set performance among the evaluated candidates.

30-Day Forecast

The selected ARIMA(0,2,2) model was refitted using the complete historical dataset and used to generate a 30-day future demand forecast.

The forecast begins on July 1, 2026.

Outputs
outputs/time_series_decomposition.png
outputs/30_day_demand_forecast.png
outputs/30_day_demand_forecast.csv
Limitations

The dataset contains only 30 historical observations, which limits the statistical reliability of long-horizon forecasting and seasonal inference.

The current model also does not explicitly incorporate marketing_event or holiday as external regressors.

Therefore, the 30-day forecast should be considered a demonstration of the forecasting pipeline rather than a production-ready demand forecast.

Technologies
Python
Pandas
NumPy
Matplotlib
Seaborn
SciPy
Statsmodels
Scikit-learn
Jupyter Notebook
Project Structure
Time-Series-Forecasting/
├── data/
│   └── daily-demand-series.csv
├── notebooks/
│   └── time_series_forecasting.ipynb
├── outputs/
│   ├── time_series_decomposition.png
│   ├── 30_day_demand_forecast.png
│   └── 30_day_demand_forecast.csv
├── .gitignore
├── README.md
└── requirements.txt
Author

Deban Kumar Das D

BCA Data Science Student
GitHub: Debankumardas