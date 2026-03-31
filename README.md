# 📈 IBOVESPA Predictive Modeling

## 🧠 Overview

This project focuses on building a **predictive model for the IBOVESPA index (Brazilian stock market)** using time series analysis and machine learning techniques.

The objective is to forecast the **daily closing price** of the index and compare multiple models to identify the most accurate approach.

The project combines:

* 📊 Statistical models (SARIMAX, ARIMA-based)
* 🤖 Machine Learning models (XGBoost, LSTM)
* 📈 Time series decomposition and analysis

---

## 🎯 Objective

* Predict IBOVESPA closing prices
* Achieve high predictive accuracy (>70%)
* Compare different modeling approaches
* Identify the best-performing model

---

## 📊 Data Source

The dataset is dynamically retrieved using the `yfinance` API.

* Source: Yahoo Finance
* Ticker: `^BVSP` (IBOVESPA)
* Period: 1994 – 2024
  
<img width="1621" height="636" alt="image" src="https://github.com/user-attachments/assets/fc5e597f-0d1e-435b-9445-7a0bb46832f5" />

No local dataset is stored in this repository.
All data is fetched programmatically at runtime, ensuring reproducibility and up-to-date information.

Example:

```python
import yfinance as yf

data = yf.download("^BVSP", start="1994-01-02", end="2024-10-10")
```

> ⚠️ This project does not include static datasets. All data is fetched directly from the Yahoo Finance API.

---

## 🧪 Methodology

### 1. Data Collection

* Data retrieved using `yfinance`
* Selection of relevant columns (`Open`, `Close`)
* Datetime conversion

---

### 2. Exploratory Data Analysis (EDA)

* Missing values and duplicates check
* Descriptive statistics
* Outlier detection using IQR
* Visualizations:

  * Boxplots
  * Time series evolution

---

### 3. Time Series Analysis

#### 🔹 Decomposition

* Additive and multiplicative decomposition
* Components analyzed:

  * Trend
  * Seasonality
  * Residuals

#### 🔹 Stationarity

* Augmented Dickey-Fuller (ADF) test
* Differencing applied to achieve stationarity

#### 🔹 Autocorrelation

* ACF (AutoCorrelation Function)
* PACF (Partial AutoCorrelation Function)

Used to determine parameters for ARIMA-based models.

---

## 🤖 Models Implemented

### 1. XGBoost

* Feature engineering:

  * Year, Month, Day, Day of Week
* Tabular approach applied to time series

---

### 2. Prophet

* Time series model developed by Meta
* Captures:

  * Trend
  * Seasonality
* Uses `Open` as external regressor

---

### 3. SARIMAX

* Seasonal ARIMA with exogenous variables
* Incorporates:

  * Autoregression
  * Differencing
  * Moving average
  * Seasonality
  * External variable (`Open`)

---

### 4. LSTM (Deep Learning)

* Recurrent Neural Network
* Captures long-term dependencies
* Data normalized using MinMaxScaler
* Sliding window approach

---

## 📏 Evaluation Metrics

The following metrics were used:

* **MAE (Mean Absolute Error)**
* **MSE (Mean Squared Error)**
* **MAPE (Mean Absolute Percentage Error)**

```python
def calculate_metrics(y_true, y_pred):
    mae = mean_absolute_error(y_true, y_pred)
    mse = mean_squared_error(y_true, y_pred)
    mape = mean_absolute_percentage_error(y_true, y_pred) * 100
    return mae, mse, mape
```

---

## 📊 Results

<img width="533" height="240" alt="image" src="https://github.com/user-attachments/assets/9ae35bd3-6473-4735-aca1-13a8d2148724" />

Based on the results obtained and analyzing the graphs above, the SARIMAX model showed the best performance among the evaluated models, with the lowest MAE (1089.07), MSE (1.495393e+06), and MAPE (0.8085) values, achieving greater accuracy in predicting the daily closing of the IBOVESPA. The Prophet model, despite capturing seasonality well, presented significantly higher errors, with a MAE of 1831.26 and a MAPE of 1.3576. LSTM and XGBoost had inferior performances, with higher predictive errors, with XGBoost standing out, presenting the highest MAPE of 1.5748.

Therefore, SARIMAX is shown to be the most suitable model for this time series, being the most efficient in capturing the characteristics of the data and providing more precise specifications. Thus, it would be the recommended choice for predicting the daily closing of the IBOVESPA index, meeting the criteria of accuracy and reliability.


| Model   | Performance         |
| ------- | ------------------- |
| SARIMAX | 🥇 Best performance |
| Prophet | Strong performance  |
| LSTM    | Good performance    |
| XGBoost | Lower performance   |

### 🏆 Best Model: SARIMAX

* Lowest MAE
* Lowest MSE
* Lowest MAPE (~0.8%)

---

## 📈 Visualizations

* Boxplots for outlier detection
* Time series trends (30 years)
* Seasonal decomposition plots
* Model comparison charts

---

## 🧠 Key Insights

* IBOVESPA shows a long-term upward trend
* Major drops observed during:

  * 2008 financial crisis
  * 2020 COVID-19 pandemic
* Time series models outperform pure ML approaches
* SARIMAX best captures temporal dependencies

---

## 🛠 Tech Stack

* Python
* Pandas / NumPy
* Matplotlib / Plotly
* Statsmodels
* Scikit-learn
* XGBoost
* Prophet
* Keras (LSTM)
* yFinance
* pmdarima

---

## 📂 Project Structure

```
predictive_model_ibovespa/
│
├── predictive_model_ibovespa.ipynb
├── README.md
└── requirements.txt
```

---

## 🚀 How to Run

1. Clone the repository:

```bash
git clone https://github.com/beatrizrosacgomes/predictive_model_ibovespa.git
```

2. Create virtual environment (optional):

```bash
python -m venv venv
venv\Scripts\activate
```

3. Install dependencies:

```bash
pip install -r requirements.txt
```

4. Run the notebook:

```bash
jupyter notebook
```

---

## 📌 Future Improvements

* Hyperparameter tuning
* Real-time prediction pipeline
* Deployment (API or dashboard)
* Inclusion of macroeconomic indicators
* Ensemble modeling

---

## ⭐ Highlights

* End-to-end time series pipeline
* Multiple model comparison
* Financial data application
* Strong statistical + machine learning foundation
