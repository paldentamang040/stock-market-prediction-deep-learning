# Stock Market Prediction Using Deep Learning and Time Series Models

## Progress of Week 8

## Overview
This project focuses on predicting stock market behavior using both traditional time-series forecasting and deep learning models. The notebook includes data collection, preprocessing, exploratory data analysis, feature engineering, sequence preparation, model development, and evaluation. The main goal is to compare how well models such as ARIMA, LSTM, and GRU can learn patterns from historical stock market data and generate useful predictions.

## Project Objectives
- Collect historical stock market data for selected companies.
- Preprocess and clean the dataset for analysis.
- Perform exploratory data analysis to understand trends, volatility, and return behavior.
- Build forecasting models using both statistical and deep learning approaches.
- Compare model outputs using visualizations and prediction results.
- Identify current model limitations and explore possible future improvements.

## Dataset
The project uses historical stock market data collected through the `yfinance` library. The selected companies in this notebook are:

- AAPL
- MSFT
- GOOGL
- AMZN
- NVDA

The dataset includes stock information such as closing price and derived indicators like daily returns, log returns, volatility, momentum, and moving averages.

## Workflow
The notebook follows these major steps:

1. **Data Collection**  
   Historical stock price data is downloaded for multiple companies using `yfinance`.

2. **Data Preprocessing**  
   The data is cleaned, missing values are handled, and target variables are created for forecasting.

3. **Exploratory Data Analysis**  
   Visualizations are created to study stock closing price trends, return distributions, volatility, moving averages, and cumulative returns.

4. **Feature Engineering**  
   Additional features such as log returns, rolling volatility, momentum, and exponential moving averages are generated to improve model learning.

5. **Sequence Preparation**  
   Time-series sequences are created for deep learning models so that historical observations can be used to predict future values.

6. **Model Development**  
   Different forecasting models are built, including ARIMA, LSTM, and GRU.

7. **Model Evaluation**  
   Predicted values are compared with actual values using visualizations and performance observations.

## Models Used
- **ARIMA (AutoRegressive Integrated Moving Average)**  
  A traditional statistical time-series forecasting model used as a baseline or comparison approach.

- **LSTM (Long Short-Term Memory)**  
  A deep learning model designed for sequential and time-series data.

- **GRU (Gated Recurrent Unit)**  
  A recurrent neural network model similar to LSTM but with a simpler architecture.

## Results
The project shows that the models are able to capture the overall trend or average movement of the target variable to some extent. However, the predictions are smoother than the actual values, which suggests that the current models are not yet capturing short-term market fluctuations effectively. This indicates that more feature engineering, tuning, or external information may be needed to improve prediction quality.

## Challenges
Some of the key challenges faced during the project include:
- Preparing time-series data correctly for forecasting models.
- Managing train, validation, and test splits properly.
- Handling noisy and highly volatile stock market behavior.
- Interpreting why predictions remain smoother than actual values.
- Identifying whether performance limitations come from the data, features, or model choice.

## Future Improvements
Possible future enhancements for this project include:
- Adding sentiment analysis using financial news or social media data.
- Improving feature engineering with more technical indicators.
- Tuning model hyperparameters for better performance.
- Comparing additional forecasting models.
- Evaluating results using more performance metrics and baseline comparisons.

## Requirements
The project uses the following Python libraries:

- pandas
- numpy
- matplotlib
- yfinance
- scikit-learn
- tensorflow
- statsmodels

## How to Run
1. Open the notebook in Jupyter Notebook or Google Colab.
2. Install the required libraries if they are not already installed.
3. Run the notebook cells in order from top to bottom.
4. Review the generated plots, model outputs, and final prediction comparison.

## File Structure
- `main.ipynb` — Updated and modified notebook
- `README.md` — Project description and usage guide

## Authors
- Palden
- Sagar