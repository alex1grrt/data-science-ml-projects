# Traffic Volume Prediction

## Overview

This project compares two machine learning approaches to predict traffic volume for four different vehicle categories: cars, bikes, buses, and trucks.

The goal is to develop regression models capable of forecasting traffic counts based on temporal patterns and other relevant features.
Random Forest and XGBoost are implemented and compared to evaluate their predictive performance.

## Dataset

The dataset is the Traffic Prediction Dataset from Kaggle (https://www.kaggle.com/datasets/hasibullahaman/traffic-prediction-dataset?utm_source=chatgpt.com&select=TrafficTwoMonth.csv). The dataset contains traffic observations recorded at 15-minute intervals over a period of approximately two months. 
It consists of 5,952 observations and 9 original columns, including weekdays, traffic counts, and traffic situation information.

The target variables are:

- `CarCount`
- `BikeCount`
- `BusCount`
- `TruckCount`

The features used for model training include:

**Temporal features:**

- `Hour_sin and Hour_cos`
- `Weekday_sin and Weekday_cos`
- `Is_weekend`
- `Is_monday`
- `Is_friday`

**Categorical features:**

- `Traffic Situation (one-hot encoded)`

The original date and time information is combined into a `Timestamp` column. Since the original year and month are not available, assumed values are used to construct the timestamps. 
The Timestamp column is retained for chronological ordering and splitting but is not directly used as a model feature.

## Methodology

The following steps were performed:

1. Load and inspect the dataset
2. Perform an initial exploratory data analysis (EDA)
3. Check for missing values and convert the time format from 12-hour to 24-hour notation
4. Visualize total traffic volume and individual vehicle categories
5. Create a combined timestamp using the provided date and time information
6. Generate cyclical temporal features for the hour of the day and the day of the week
7. Create additional binary features for weekends, Mondays, and Fridays
8. Define the four traffic count variables as target variables
9. Split the dataset chronologically into training (70%), validation (15%), and test (15%) sets
10. Apply one-hot encoding to categorical features
11. Train Random Forest and XGBoost regression models and optimize their hyperparameters using RandomizedSearchCV
12. Generate predictions on the validation and test sets
13. Evaluate and compare both models using R², RMSE, and MAE

## Models

Two machine learning models were implemented and compared:
- **Random Forest**: An ensemble learning algorithm that combines multiple decision trees. It supports multi-output regression natively and was optimized using randomized hyperparameter search

- **XGBoost**: A gradient boosting algorithm that builds decision trees sequentially to improve predictive performance. MultiOutputRegressor was used to predict all four target variables, and hyperparameters were optimized using randomized search.

Both models use the same chronological training, validation, and test splits to ensure a consistent comparison.

## Evaluation

Both models are evaluated using the coefficient of determination (R²), Root Mean Squared Error (RMSE), and Mean Absolute Error (MAE). 
The evaluation is performed on both the validation set and the independent test set to compare predictive performance and assess how well the models generalize to unseen data.

**Validation Set**
The validation results show that both models achieve similar predictive performance across the four vehicle categories.

| Target       | XGBoost R² | Random Forest R² |
| ------------ | ---------: | ---------------: |
| Car Counts   |      0.849 |            0.859 |
| Bike Counts  |      0.707 |            0.681 |
| Bus Counts   |      0.805 |            0.807 |
| Truck Counts |      0.725 |            0.733 |

Random Forest performs slightly better for car, bus, and truck counts, whereas XGBoost achieves better results for bike counts. Both models perform particularly well when predicting car and bus traffic.

**Test Set**

The final evaluation is performed on the independent test set, which was not used during model training or hyperparameter optimization.

| Target       | XGBoost R² | Random Forest R² |
| ------------ | ---------: | ---------------: |
| Car Counts   |      0.843 |            0.853 |
| Bike Counts  |      0.742 |            0.712 |
| Bus Counts   |      0.807 |            0.815 |
| Truck Counts |      0.729 |            0.711 |

The test results confirm the overall performance observed during validation. Random Forest achieves slightly better results for car and bus counts, while XGBoost performs better for bike and truck counts.

Both models achieve an average R² score of approximately 0.78 across the four target variables, indicating good overall predictive performance. Car and bus counts are predicted particularly well, whereas bike and truck counts remain somewhat more challenging.



## Technologies 
- Python
- NumPy
- Pandas
- Matplotlib
- scikit-learn
- Google Colab

## Conclusion 
This project compared Random Forest and XGBoost for predicting traffic volume across four vehicle categories. Both models achieved similar overall performance, with an R² score of approximately 0.78 on the test set.

Random Forest achieved the best results for car and bus counts, while XGBoost performed better for bike and truck counts. Both models achieved particularly strong results for car and bus predictions, with R² scores above 0.8.

Truck counts remained more challenging to predict due to the higher variability in the data. Nevertheless, both models captured the general traffic patterns reasonably well.

Overall, the results demonstrate that tree-based ensemble methods can effectively model traffic patterns and predict traffic volume across different vehicle categories.






