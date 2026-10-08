# 🛒 Store Sales Time Series Forecasting

A beginner-friendly time series forecasting project that predicts future store sales from historical data using a **Random Forest Regressor**. It captures sales trends and seasonality and accounts for holidays, events, oil prices, promotions, and store information.

Built in **Google Colab** with Python, Pandas, Matplotlib, Seaborn, and Scikit-learn.

---

## 📌 Problem Statement

Develop a time series forecasting model that predicts future sales for stores based on historical sales data. The model should identify sales patterns and trends over time and consider factors such as holidays, events, store information, and other influencing factors.

## 📂 Dataset

Kaggle competition: [Store Sales - Time Series Forecasting](https://www.kaggle.com/competitions/store-sales-time-series-forecasting) (Corporación Favorita, Ecuador).

| File | Description |
|------|-------------|
| `train.csv` | Daily sales per store and product family, with promotions |
| `test.csv` | Future dates to forecast |
| `stores.csv` | Store city, state, type, and cluster |
| `oil.csv` | Daily oil prices |
| `holidays_events.csv` | National/regional/local holidays and events |
| `transactions.csv` | Daily transactions per store |

> The dataset is **not included** in this repo. Download it from Kaggle (link above).

## 🔄 Project Workflow

1. Import libraries
2. Load dataset (auto-detects files in Colab, extracts the zip if needed)
3. Data understanding
4. Data cleaning (datetime conversion, duplicates, missing oil prices, transferred holidays)
5. Feature engineering (year, month, day, day of week, week of year, weekend, holiday/event flags, label encoding)
6. Exploratory data analysis
   - Sales trend over time
   - Monthly and weekday patterns
   - Sales by store and store type
   - Effect of holidays and events
   - Correlation heatmap
7. Model building (chronological split, last 90 days as test set)
8. Model evaluation (MAE, MSE, RMSE, R²)
9. Actual vs predicted sales
10. Future sales forecast
11. Final results tables

## 🧠 Model

- **Algorithm:** Random Forest Regressor (`n_estimators=100`, `max_depth=15`, `min_samples_leaf=2`)
- **Split:** Chronological, not random, so the model never sees the future during training
- **Target:** Daily sales per store

## 📊 Results

Fill these in after running the notebook:

| Metric | Value |
|--------|-------|
| MAE | _your value_ |
| MSE | _your value_ |
| RMSE | _your value_ |
| R² Score | _your value_ |

Add screenshots of your graphs to an `images/` folder and link them here:

```markdown
![Sales Trend](images/sales_trend.png)
![Actual vs Predicted](images/actual_vs_predicted.png)
![Forecast](images/forecast.png)
```

## 🚀 How to Run

**Option 1: Google Colab (recommended)**
1. Open `store_sales_forecasting.ipynb` in Google Colab.
2. Upload the dataset zip (or the CSV files) to the Colab session.
3. Run all cells (`Runtime → Run all`). The code detects the files automatically.

**Option 2: Locally**
```bash
git clone https://github.com/<your-username>/store-sales-forecasting.git
cd store-sales-forecasting
pip install -r requirements.txt
jupyter notebook
```
Place the dataset CSVs in a `data/` folder and update the path in the loading section if needed. The Colab-only upload code can be skipped.

## 🗂️ Repository Structure

```
store-sales-forecasting/
├── store_sales_forecasting.ipynb   # Main notebook with code and outputs
├── requirements.txt
├── README.md
├── LICENSE
├── .gitignore
└── images/                         # Graph screenshots for the README
```

## 🔮 Future Improvements

- Add lag and rolling-mean features
- Try XGBoost / LightGBM
- Compare with Prophet or ARIMA
- Forecast per product family
- Hyperparameter tuning with time series cross-validation

## 🛠️ Tech Stack

Python · Pandas · NumPy · Matplotlib · Seaborn · Scikit-learn · Google Colab

## 👩‍💻 Author

**Lalithanjali**
B.Tech Computer Science Engineering (Data Science), GITAM Deemed University, Visakhapatnam

- GitHub: [[@lalithanjalivavilapalli-ops](https://github.com/your-username](https://github.com/lalithanjalivavilapalli-ops))
- LinkedIn: _add your link_

## 📄 License

This project is licensed under the MIT License. See [LICENSE](LICENSE) for details.
