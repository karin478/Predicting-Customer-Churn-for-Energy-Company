# Predicting-Customer-Churn-for-Energy-Company
 This project involves performing exploratory data analysis and applying machine learning techniques to predict customer churn for an energy company. The dataset includes customer usage, sign up date, forecasted usage, pricing data, and churn indicators.


## Overview

This project involves performing exploratory data analysis and applying machine learning techniques to predict customer churn for an energy company. The dataset includes customer usage, sign up date, forecasted usage, pricing data, and churn indicators.

## Part 1: Exploratory Data Analysis

The initial exploratory data analysis revealed several key insights:

- The dataset is highly imbalanced, with the majority of customers not churning. This imbalance in the target variable will need to be addressed during the modeling phase.

- Certain features, such as 'cons_12m', 'cons_gas_12m', and 'cons_last_month', exhibit a highly skewed distribution. Log transformation might be necessary to handle the skewness.

- The features 'forecast_cons_12m' and 'forecast_meter_rent_12m' show a positive correlation with churn, suggesting that customers with higher electricity consumption and higher forecasted meter rental are more likely to churn.

- A new feature 'total_price' was engineered from the pricing data. The feature indicates the total price a customer has to pay for the energy. It is found that churned customers have a slightly higher total price on average.

## Part 2: Machine Learning Analysis and Recommendations

Following the initial exploratory data analysis, we proceeded with advanced machine learning techniques to delve deeper into the data and provide more sophisticated insights.

### Machine Learning Model

We trained a RandomForest Classifier, which is a robust and widely-used machine learning model for classification tasks. The model achieved the following performance on the test data:

- Accuracy: 90.66%
- Recall: 3.87%
- Precision: 100%
- F1 Score: 7.46%

The accuracy of the model is high, suggesting a good overall performance. However, the recall is quite low, meaning that the model missed a lot of actual churn cases. The F1 score, which is the harmonic mean of precision and recall, is also low, suggesting poor performance when considering both precision and recall.

This could be due to the imbalanced nature of our dataset, where most customers did not churn. In such cases, the model might be biased towards predicting the majority class, i.e., customers who did not churn. 

### Addressing Class Imbalance

To address the class imbalance, we attempted using class weights in the model, which led to a slight improvement in recall but overall performance remained similar. 

We also attempted to use the XGBoost model, which provides parameters for handling class imbalance. The XGBoost model showed a significant improvement in the recall score to 58.57%, indicating better identification of actual churn cases. However, precision dropped, indicating a higher rate of false positives. The F1 score improved to 33.30%, showing better balance between precision and recall. 

However, the model performance is still not optimal. Therefore, further steps should be taken to improve the model.

### Further Steps

1. **Parameter Tuning:** We attempted to tune the parameters of the XGBoost model using GridSearchCV. However, due to computational constraints, we were unable to perform an exhaustive search. This could be attempted in a more resourceful environment to find the optimal parameters for the model.

2. **Feature Importance:** It could be beneficial to delve deeper into the most important features contributing to customer churn. In our preliminary analysis, features related to net and gross power margin, electricity consumption, and total price stood out as significant. Further exploration and engineering of these features could potentially improve the model.

3. **Alternative Models:** If the class imbalance persists as a problem, other models known for handling class imbalance, such as LightGBM or CatBoost, could be tried.

4. **Additional Data:** The model could benefit from more data, especially more instances of churn cases to learn from. If possible, collecting additional data over time could improve the model's performance.

In conclusion, while we've made progress in analyzing the data and building a predictive model, there's still room for improvement. The steps outlined above should guide the continuation of this project towards a more accurate and robust churn prediction model. This will ultimately help the company take proactive measures to retain its customers and maintain a healthy customer base.
