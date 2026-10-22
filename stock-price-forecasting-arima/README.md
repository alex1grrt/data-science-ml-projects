# Stock Price Forecasting with ARIMA

## Overview

This project analyzes historical stock market data and evaluates the performance of ARIMA time series models for stock price forecasting.

The project includes exploratory data analysis (EDA) across 491 stocks and a detailed case study of Meta Platforms (META). ARIMA predictions are compared with a naive baseline to assess forecasting performance.

## Dataset

The dataset contains historical stock market data for 491 companies over approximately five years.

The original dataset was obtained from Kaggle and downloaded using KaggleHub. To keep this repository lightweight, the CSV file is not included.

Please download the dataset from the original Kaggle source before running the notebook.

Dataset source: https://www.kaggle.com/datasets/iveeaten3223times/massive-yahoo-finance-dataset


The main features include:

### Original Features

- `Company`: Stock ticker symbol
- `Date`: Trading date
- `Close`: Closing stock price
- `Volume`: Daily trading volume

### Engineered Features (Feature Engineering)

- `Daily_Return`: Daily percentage change in closing price
- `Rolling_Volatility`: Rolling standard deviation of daily returns, measuring price volatility

The engineered features Daily_Return and Rolling_Volatility were used for exploratory data analysis. The ARIMA models were trained using historical closing prices (Close).

## Methodology

The following steps were performed:

1. Load and inspect the stock market dataset
2. Clean and preprocess the data
3. Perform exploratory data analysis (EDA) across all 491 stocks
4. Perform feature engineering
5. Fit and evaluate ARIMA models across the 491 stocks
6. Explore the META stock dataset
7. Test stationarity using the Augmented Dickey-Fuller (ADF) test
8. Examine ACF and PACF plots to investigate autocorrelation patterns
9. Fit and evaluate an ARIMA model for META
10. Compare actual and predicted stock prices
11. Evaluate forecasting performance using MAE, RMSE, and MASE


## Models

### ARIMA

ARIMA (AutoRegressive Integrated Moving Average) is a time series forecasting model defined by three parameters:

- `p`: Autoregressive order
- `d`: Degree of differencing
- `q`: Moving average order

The model was applied to historical stock prices, with differencing used where necessary to address non-stationarity.

### Naive Baseline

The naive baseline predicts the next closing price using the previous day's closing price. It provides a simple benchmark for evaluating whether ARIMA improves forecasting accuracy.

## Evaluation

Model performance was evaluated using the following metrics:

- **MAE (Mean Absolute Error):** Measures the average absolute difference between predicted and actual prices.
- **RMSE (Root Mean Squared Error):** Penalizes larger prediction errors more heavily.
- **MASE (Mean Absolute Scaled Error):** Scales forecasting errors relative to a naive in-sample benchmark.


### Evaluation Across 491 Stocks

Across the 491 stocks evaluated, ARIMA achieved a lower MAE than the naive baseline for approximately 29.33% of stocks. The median MASE was 0.98, and the mean MASE was approximately 1.01.

These results indicate that ARIMA did not consistently outperform the naive baseline across stocks.

### Evaluation on Meta (META) Case Study

For Meta, ARIMA achieved an MAE of approximately 3.90, compared with 3.91 for the naive baseline. The MASE was 0.96.

Although ARIMA performed slightly better in this evaluation, the improvement was very small.

## Visualizations

The project includes the following visualizations:

- Dataset preview and descriptive statistics
- Closing price distributions
- Top 10 gainers and losers
- Top 10 stocks by trading volume
- Normalized stock price performance
- META stock price performance
- META daily returns
- META 30-day rolling volatility
- ADF test results and ACF/PACF plots
- Actual vs. predicted stock prices
- Model performance metrics

## Technologies

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Statsmodels
- Scikit-learn
- Google Colab

## Conclusion

This project evaluated ARIMA forecasting performance across 491 stocks and in a detailed Meta case study. While ARIMA slightly outperformed the naive baseline for Meta, it achieved a lower MAE for only 29.33% of the stocks overall.

The results demonstrate that ARIMA's performance varies across stocks and that a more complex forecasting model does not necessarily outperform a simple baseline.
