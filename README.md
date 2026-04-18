# 📈 Stock Price Forecasting System (Final Submission)

[![Python](https://img.shields.io/badge/Python-3.8%2B-blue.svg)](https://www.python.org/)
[![Status](https://img.shields.io/badge/Status-Cleaned%20Final%20Version-success.svg)]()
[![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626.svg)](https://jupyter.org/)

This repository contains a robust machine learning pipeline designed to forecast stock price behavior by integrating historical market data with financial sentiment analysis.

## 📑 Table of Contents
- [Overview](#-overview)
- [Key Improvements (Week 8)](#-key-improvements-week-8)
- [Project Objectives](#-project-objectives)
- [Methodology](#-methodology)
- [Models & Architecture](#-models--architecture)
- [Requirements](#-requirements)
- [Usage](#-usage)

## 📖 Overview
The project focuses on predicting stock market movements for major tech symbols (AAPL, MSFT, GOOGL, AMZN, NVDA). It goes beyond basic price prediction by incorporating sentiment analysis from financial news and evaluating models based on their ability to predict the *direction* of market movement.

## ✨ Key Improvements (Week 8)
This version (`main-8-fixed.ipynb`) includes critical updates to ensure academic and functional rigor:
- **Data Integrity Fix:** Resolved sentiment-scaler leakage to ensure completely blind out-of-sample testing.
- **Directional Accuracy:** Integrated metrics to track how often the model correctly predicts the "up" or "down" movement.
- **Naive Baseline:** Added a naive benchmark (Persistence model) to verify the predictive alpha of the ML/DL models.
- **Consolidated Selection:** Automated the selection of the "Best Model" per symbol using a weighted scoring system (MAE, RMSE, and Directional Accuracy).
- **Zero-Sentiment Coverage:** Validated model stability during periods with no available news sentiment.

## 🎯 Project Objectives
* **Preprocess & Clean:** Handle highly volatile financial datasets and align them with sentiment scores.
* **Feature Engineering:** Generate technical indicators (Volatility, Momentum, EMA) without forward-looking bias.
* **Model Comparison:** Rigorously test Statistical (ARIMA) vs. Deep Learning (LSTM, GRU) approaches.
* **Performance Optimization:** Use a scoring framework to rank models dynamically.

## 🧠 Methodology
1. **Data Collection:** Automated fetching of historical data via `yfinance`.
2. **Sentiment Analysis:** Processing news text using `vaderSentiment` and `textblob`.
3. **Sequence Preparation:** Creating sliding window sequences for RNN-based models.
4. **Scoring & Selection:** Models are ranked by a final score that balances error magnitude (MAE/RMSE) and directional hits.

## 🤖 Models & Architecture
- **ARIMA:** A statistical baseline for time-series forecasting.
- **LSTM (Long Short-Term Memory):** Designed to capture long-term dependencies in sequential data.
- **GRU (Gated Recurrent Unit):** An efficient, simplified RNN architecture for time-series patterns.
- **Naive Baseline:** The "Yesterday-is-Today" benchmark to ensure model value.

## 🛠 Requirements
The following libraries are required: `matplotlib`, `numpy`, `pandas`, `requests`, `sklearn`, `statsmodels`, `tensorflow`, `textblob`, `vaderSentiment`, `yfinance`

## 🚀 Usage
1. Open `main-8-fixed.ipynb` in a Jupyter environment or Google Colab.
2. Ensure all dependencies are installed.
3. **Run All Cells:** The notebook is designed to execute from top-to-bottom.
4. **Review Results:** The final cell generates the `best_models_df`, which displays the top model, feature set, and accuracy score for each stock symbol.

---
**Authors:** Palden & Sagar  
**Version:** 8.0 (Fixed & Consolidated)
