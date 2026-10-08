# Store Sales Forecasting Using Historical Retail Data

Forecasting daily store-level sales for the Kaggle
[Store Sales – Time Series Forecasting](https://www.kaggle.com/competitions/store-sales-time-series-forecasting)
dataset using a Random Forest model. Built as a Foundations of Data Science project (Version 1: a clean, beginner-friendly baseline).

## Project Overview

The script loads the raw retail data, checks and cleans it, engineers time/holiday/store/lag features, explores the data with charts, trains a Random Forest, compares it with a simple baseline, and produces a forecast for the dates in `test.csv`.

## Dataset

Download from Kaggle (not included in this repo): <https://www.kaggle.com/competitions/store-sales-time-series-forecasting/data>

| File | Used for |
|------|----------|
| `train.csv` | Historical sales (required) |
| `stores.csv` | Store city, state, type, cluster (required) |
| `test.csv` | Future dates to forecast |
| `oil.csv` | Daily oil price (economic factor) |
| `holidays_events.csv` | National / regional / local holidays and events |
| `transactions.csv` | Loaded, not used as a model feature |

The script finds these files automatically (or asks for the zip in Google Colab).

## Approach

1. **Load** – auto-detects CSV files and standardises column names
2. **Data quality check** – missing values, duplicates, invalid dates/values, train/test compatibility
3. **Cleaning** – fixes only what is actually wrong; aggregates product-level rows to one row per store per day; removes days before a store opened or when it was closed
4. **Feature engineering**
   - Calendar: year, month, day, day of week, week of year, quarter, weekend, month start/end
   - Holidays: national, regional, local, and special events (transferred holidays ignored)
   - Store: city, state, type, cluster; oil price; promotions
   - Lag features: sales from `HORIZON` days earlier and a 28-day rolling average, so they are available for the forecast period without leakage
5. **EDA** – sales trend, monthly trend, sales by store, distribution, day-of-week, holiday vs non-holiday, top stores, correlation heatmap
6. **Chronological train/test split** – the last 90 days are held out (no shuffling)
7. **Model** – `RandomForestRegressor` (200 trees, max depth 20)
8. **Evaluation** – MAE, MSE, RMSE, R², compared with a baseline ("same as `HORIZON` days ago")
9. **Forecast** – retrains on all history and predicts the dates in `test.csv`

## Results

> Fill this table in after running the script on your data. Do not copy numbers from anywhere else.

| Model | MAE | RMSE | R² |
|-------|-----|------|----|
| Baseline (sales `HORIZON` days earlier) | | | |
| Random Forest Regressor | | | |

Add your key charts to an `images/` folder and link them here, e.g. `![Actual vs Predicted](images/actual_vs_predicted.png)`.

## How to Run

**Google Colab (easiest)**
1. Upload `store_sales_forecasting.py` content into a notebook (or upload the file and run `%run store_sales_forecasting.py`)
2. Run it and upload the Kaggle dataset zip when prompted

**Locally**
```bash
git clone https://github.com/<your-username>/<your-repo>.git
cd <your-repo>
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
# put the Kaggle CSV files (or the zip) in this folder, then:
python3 store_sales_forecasting.py
```
Charts open in windows when run locally; running inside Jupyter/Colab shows them inline.

## Output

- Charts and metric tables printed during the run
- `future_sales_forecast.csv` – predicted sales per store per forecast date

## Limitations and Future Work (Version 2)

- Forecasts at store level, not product-family level
- Only a few years of history for seasonality
- Try Gradient Boosting models (e.g. XGBoost / LightGBM) and hyperparameter tuning
- Add more lag/rolling features and cross-validation for time series

## Tech Stack

Python, pandas, NumPy, matplotlib, seaborn, scikit-learn

## Author

Lalithanjali – B.Tech CSE (Data Science), GITAM Deemed University, Visakhapatnam
