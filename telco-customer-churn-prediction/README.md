# Telco Customer Churn Prediction

## Overview

This project compares three machine learning approaches to predict customer churn in the telecommunications industry: Deep Learning, Random Forest, and XGBoost.

The goal is to identify customers who are likely to leave a telecommunications provider and compare the performance of the three models.

## Dataset

The dataset is the Telco Customer Churn dataset from Kaggle. It contains 7,043 observations and customer information related to demographics, services, contracts, payment methods, and billing.


The features used for model training include:

**Categorical features:**
- `gender`
- `Partner`
- `Dependents`
- `PhoneService`
- `PaperlessBilling`
- `MultipleLines`
- `InternetService`
- `OnlineSecurity`
- `OnlineBackup`
- `DeviceProtection`
- `TechSupport`
- `StreamingTV`
- `StreamingMovies`
- `Contract`
- `PaymentMethod`

**Numerical features:**
- `SeniorCitizen`
- `tenure`
- `MonthlyCharges`
- `TotalCharges`

The target variable is `Churn`, which indicates whether a customer left the company (`Yes`) or stayed (`No`). The `customerID` column is excluded from model training.

## Methodology

The following steps were performed:

1. Load and inspect the dataset
2. Explore customer characteristics and churn patterns using Exploratory Data Analysis (EDA)
3. Clean the data and convert TotalCharges to a numeric format
4. Split the data into training, validation, and test sets
5. Apply one-hot encoding to categorical features
6. Standardize numerical features using StandardScaler
7. Train a Deep Learning model using TensorFlow/Keras
8. Optimize Random Forest and XGBoost using RandomizedSearchCV
9. Generate predictions on the test set
10. Evaluate and compare the models using accuracy, precision, recall, F1-score, and confusion matrices


## Models

Three models were implemented and compared:

- Deep Learning: A feedforward neural network built with TensorFlow/Keras
- Random Forest: An ensemble learning model optimized using randomized hyperparameter search
- XGBoost: A gradient boosting model optimized using randomized hyperparameter search

The same training, validation, and test splits were used to ensure a consistent comparison between the models.

## Evaluation

The models were evaluated on the test set using accuracy, precision, recall, and F1-score for the churn class.

| Model | Accuracy | Churn Precision | Churn Recall | Churn F1-Score |
|---|---:|---:|---:|---:|
| Deep Learning | 81% | 0.67 | 0.58 | 0.62 |
| Random Forest | 81% | 0.71 | 0.51 | 0.59 |
| XGBoost | 82% | 0.70 | 0.53 | 0.60 |


## Visualizations

The project includes the following visualizations:

- Customer churn distribution
- Customer tenure distribution by churn status
- Churn rate by contract type
- Churn rate by internet service
- Monthly charges by churn status
- Training and validation loss over epochs for the Deep Learning model
- Confusion matrices comparing all three models

The loss plot illustrates how the Deep Learning model's training and validation loss change during training. It helps assess learning progress and identify potential overfitting when the training loss continues to decrease while the validation loss starts to increase.

## Technologies

- Python
- NumPy
- Pandas
- Matplotlib
- Seaborn
- scikit-learn
- TensorFlow/Keras
- Google Colab

## Conclusion

This project compared Deep Learning, Random Forest, and XGBoost for predicting customer churn. All three models achieved similar overall accuracy, ranging from 81% to 82%.

XGBoost achieved the highest accuracy, while Deep Learning achieved the highest recall and F1-score for the churn class. Random Forest achieved the highest precision for churn predictions.

Overall, Deep Learning was better at identifying customers who actually churned, while XGBoost achieved the best overall accuracy. However, all three models missed a considerable proportion of actual churn cases, indicating potential for further improvement.
