# [IEEE-CIS-Fraud-Detection](https://www.kaggle.com/c/ieee-fraud-detection)

## Competition Overview
The main goal is to identify whether each transaction is `fraudulent`. Among them, the `training set` sample is about **590,000** (3.5% of fraud), and the `test set` sample is about **500,000**. 

The data is mainly divided into 2 categories: 
- transaction data
- identity data.

## Model 
**Model**: 

**Performance Metric**: The evaluation index was AUC with imbalanced data with few isFraud = 1 data.

**Training and verification**: 


**Submission & LB score**

|Model|Public score|Private score|Final rank| 
|---|---|---|---|
| LGBM |0.952586|0.928613| |
| LGBM |0.952685|0.928222| |
| LGBM |0.952711|0.928091| |





**The libraries used are**:  
- numpy
- pandas
- matplotlib, 
- seaborn
- sklearn
- lightgbm
- xgboost



