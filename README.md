# [IEEE-CIS-Fraud-Detection](https://www.kaggle.com/c/ieee-fraud-detection)

## Competition Overview
The main goal is to identify whether each transaction is `fraudulent`. Among them, the `training set` sample is about **590,000** (3.5% of fraud), and the `test set` sample is about **500,000**. 

The data is mainly divided into 2 categories which are joined by `TransactionID`. Not all transactions have corresponding identity information.
- transaction data
- identity data.

## Data Description
**Transaction Features**:
- TransactionDT: timedelta from a given reference datetime (not an actual timestamp)
- TransactionAMT: transaction payment amount in USD
- ProductCD: product code, the product for each transaction
- card1-card6: payment card information, such as card type, card category, issue bank, country, etc.
- addr: address
- dist: distance
- P_ and (R__) emaildomain: purchaser and recipient email domain
- C1-C14: counting, such as how many addresses are found to be associated with the payment card, etc. The actual meaning is masked.
- D1-D15: timedelta, such as days between previous transaction, etc.
- M1-M9: match, such as names on card and address, etc.
- Vxxx: Vesta engineered rich features, including ranking, counting, and other entity relations.

**Identity Features**:
- DeviceType
- DeviceInfo
- id_12 - id_38

## Exploratoy Data Analysis (EDA)
- One of the first things we noticed when conducting EDA was the `sparsity of the dataset`.
- The distribution of target variable **'isFraud'** has `class imbalance` problem where it shows that 96.5% of data contains non-fraud transaction where as only 3.5% are fraud.
- Target variable 'isFraud' is more prevalent in the mobile **'DeviceType'** as well as more prevalent in the **'IP_PROXY:ANONYMOUS'** based on `'id_31'`.
- Another observation that was immediately apparent is the imbalanced nature of the data. This shows that 'TransactionDT' is a timedelta gap, not a timestamp.
- Dataset has a very high percentage of missing values, especially the V columns.
- Anonymized columns not only had a high amount of missing data, but their distributions also were not normally distributed.

## Missing Values
- Around 414 features contain missing values.
- Top features containing missing values.
- Drop columns with over 90% missing values
- Replace the numerical missing value with the mean of the columns. If there are outliers, impute with median.


## Model 
**Model**: 

**Performance Metric**: The evaluation index was AUC with imbalanced data with few isFraud = 1 data.

**Training and verification**: 


**Submissions & Leaderboard Scores**

|Model |Public score|Private score|Final rank| 
|------|--------|--------|---|
| LGBM |0.952586|0.928613|   |
| LGBM |0.952685|0.928222|   |
| LGBM |0.952711|0.928091|   |



**Challenges**:
- Sparsity of the dataset
- A lot Missing Values
- Imbalanced isFraud Variable
- Outliers

**The libraries used are**:  
- numpy
- pandas
- matplotlib, 
- seaborn
- sklearn
- lightgbm
- xgboost



