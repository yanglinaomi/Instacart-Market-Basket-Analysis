# Instacart-Market-Basket-Analysis
Use historical data on customer orders over time to predict which previously purchased products will be in a user’s next order. 
[based on this competition](https://www.kaggle.com/c/instacart-market-basket-analysis).

---
## Problem Statement

Instacart is an American company that operates a grocery delivery and pick-up service in the United States and Canada. The company offers its services via a website and mobile App. The service allows customers to order groceries from participating retailers with the shopping being done by a personal shopper. It offers same-day delivery and pickup services for retailers and consumers [[1]](https://en.wikipedia.org/wiki/Instacart).

As more and more grocery stores move online in recent years, Instacart would like to make effort to maintain customer retention rate. Customer retention is the best way to scale business at an affordable cost. High customer retention rates also increase profitability [[2]](https://www.lightspeedhq.com/blog/customer-retention-rate/). 

As data scientists of Instacart, we would like to utilize ordering historical data and apply machine learning to predict whether customers will make repeat purchase for some products in their next order. Based on the prediction result, we can make recommendations for strategies to improve customer retention rate. 

---
## Executive Summary
As online groceries stores increase rapidly,Instacart faces the challenge to maintain customer retention rate. They would like to promote customer experience when ordering from Instacart App. They expect their customer to search the products that they needs more easily and time-efficiently. 

In this project, we will explore datasets that include information about orders, products, aisles and department. We create intensive feature engineering about user, product, user-product and lastest orders for modeling. 

The models we use in this project includes basic model (Logistic Regression), boosting models (XGBoost and Lightgbm), bagging model (Random Forest). Amongst these models, random forest performances the best and can achieved f1 score as 0.368, which is much higher than baseline f1 score 0.178. 

Best model's important features indicates that certain latest orders features and user-product features were key features in predicting repeat purchase of products in customers' next order. Latest orders features indicates customers' recent preference. We can understand customers' long-term preference through user-product features. 

Based on the predicted results, we recommend strategies to Instacart to improve customer retention rate and hence increase sales.

---
## Dataset
We use datasets in the [same kaggle competition](https://www.kaggle.com/c/instacart-market-basket-analysis/data). 

---
## Predictive Models
| Classifier          | Hyperparams                                                                                                                                   | Optimal Threshold |   Train f1 score |   Val f1 score |   Test f1 score |
|:--------------------|:----------------------------------------------------------------------------------------------------------------------------------------------|:----------------|--------------:|---------------:|---------------:|
| Logistic Regression | {'logreg__C': 0.1}                                                           |            0.20 |          0.427 |           0.429  |0.363|
| XGBoost            | {'learning_rate': 0.02, 'max_depth': 6, 'n_estimators': 1000}                     |            0.21 |          0.434 |           0.433 |0.365|
| Lightgbm                 | {'learning_rate': 0.1, 'max_depth': 3, 'num_iterations': 500}                    |            0.22  |          0.431 |           0.432 |0.365|
| Random Forest       | {'max_depth': 12, 'n_estimators': 1000} |            0.21 |          0.437 |           0.431 |0.368|

Comparing the performance on the test data versus the performance on the training data, we do observe some overfitting. 

We can observe that amongst these models, random forest performances best. However, due to large dataset, it requests quite long time to train random forest model. The second best performance models are boost models, i.e. XGBoost and Lightgbm. They requires shorter time to train, especially Lightgbm model needs even shorter time than XGBoost. Not surprisedly, the third best performance model is Logistic Regression due to its naive nature.

The performance gap between Random Forest & Logistic Regression is not that much. If we would like to obtain rough result quickly, we can apply logistic regression model.

---
## Conclusion and Recommendations

In conclusion, we believe that our model can predict product reorder in next purchase effectively, with f1 score as 0.368. The prediction result can help increase sales and improve customer retention rate for Instacart. We suggest Instacart to utilize of data science to understand customers' short term and long term preference. For example, through customer latest orders, we can understand customers' recent preference. We also can understand customers' long term preference through more historical order data. 

As mentioned in previous section, customer retention rate is important to Instacart. 
With prediction results from our model, we can provide the following recommendations to improve customer retention rate. 
1. Offer personalized discounts and credits on products that customers may purchase repeatedly in their next orders.
2. Send engaging emails to customers based on the prediction result for repeating purchase.

---
