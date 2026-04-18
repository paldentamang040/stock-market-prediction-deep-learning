# 📈 Stock Price Forecasting System

[![Python](https://img.shields.io/badge/Python-3.8%2B-blue.svg)](https://www.python.org/)
[![Status](https://img.shields.io/badge/Status-Final%20Version-success.svg)]()
[![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626.svg)](https://jupyter.org/)

This repository contains a machine learning pipeline that forecasts daily stock return direction by combining historical market data with financial news sentiment. Models are evaluated on both error magnitude and directional accuracy against a naive baseline.

## 📑 Table of Contents
- [Overview](#-overview)
- [Project Objectives](#-project-objectives)
- [Methodology](#-methodology)
- [Models & Architecture](#-models--architecture)
- [Evaluation](#-evaluation)
- [Requirements](#-requirements)
- [Usage](#-usage)

## 📖 Overview
The project predicts next-day **returns** (not raw prices) for five major tech stocks: AAPL, MSFT, GOOGL, AMZN, and NVDA. Sentiment scores from the Marketaux financial news API are incorporated as lagged features alongside price and return history, ensuring no future information leaks into training.

## 🎯 Project Objectives
- **Predict return direction** — frame the task as return forecasting rather than price level forecasting, making the naive baseline harder to beat
- **Leakage-free pipeline** — fit all scalers on training data only, apply to validation and test
- **Sentiment integration** — align lagged Marketaux sentiment scores to trading days without look-ahead bias
- **Fair model comparison** — compare LSTM and GRU against a zero-return naive baseline using consistent train/val/test splits across all symbols

## 🧠 Methodology
1. **Data collection** — historical OHLCV data fetched via `yfinance` (2-year window, daily interval)
2. **Sentiment pipeline** — financial news fetched from Marketaux API, entity-level sentiment scores aggregated daily, lagged by 1 day, and smoothed with a 5-day rolling mean (`sentiment_ma_5`) to avoid leakage
3. **Feature engineering** — features used: `Close`, `returns`, `sentiment_ma_5`
4. **Sequence preparation** — sliding window sequences (window = 60 days) created for LSTM and GRU inputs
5. **Leakage-free scaling** — `MinMaxScaler` fit on training split only, transformed on val/test
6. **Scoring & selection** — models ranked per symbol using a weighted score: 45% RMSE, 35% MAE, 20% directional accuracy (inverted)

## 🤖 Models & Architecture

| Model | Architecture | Notes |
|---|---|---|
| **ARIMA** | Grid search over 5 orders, best selected on val RMSE | Statistical baseline on price levels |
| **LSTM** | `LSTM(50) → Dropout(0.3) → Dense(1)` | Trained on returns with early stopping (patience=10) |
| **GRU** | `GRU(50) → Dropout(0.3) → Dense(1)` | Same architecture and training setup as LSTM |
| **Naive baseline** | Predict zero return every day | Random walk assumption — DA reflects how often the market actually moves up |

## 📊 Evaluation
Three metrics are reported for every model and symbol:

- **MAE** — mean absolute error on predicted returns
- **RMSE** — root mean squared error on predicted returns
- **Directional accuracy (DA)** — percentage of days where the model correctly predicts up vs. down movement

Directional accuracy is the primary metric of interest for trading relevance. The naive baseline (zero return) sets the floor — any model beating it on DA is providing genuine signal.

## 🛠 Requirements
```
matplotlib
numpy
pandas
requests
scikit-learn
statsmodels
tensorflow
yfinance
```

Install all dependencies by running the first cell of the notebook, which handles installs automatically.

## 🚀 Usage
1. Open `main.ipynb` in Jupyter or Google Colab
2. Add your Marketaux API key to the `MARKETAUX_API_KEY` variable in Section 4
3. **Run all cells top-to-bottom** — the notebook is fully sequential with no hidden state dependencies
4. Final outputs are in **Section 8** (consolidated comparison table) and **Section 9** (best model per symbol)

---
**Authors:** Palden & Sagar
