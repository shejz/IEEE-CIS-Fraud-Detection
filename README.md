# [IEEE-CIS-Fraud-Detection](https://www.kaggle.com/c/ieee-fraud-detection)

## Competition Overview
The main goal is to identify whether each transaction is `fraudulent`. Among them, the `training set` sample is about **590,000** (3.5% of fraud), and the `test set` sample is about **500,000**. 

The data is mainly divided into 2 categories which are joined by `TransactionID`. Not all transactions have corresponding identity information.
- transaction data
- identity data.

## Data Description
**Transaction Features**:
- **TransactionDT**: Timedelta from a given reference datetime (not an actual timestamp), but the time difference in seconds from a certain time.
- **TransactionAMT**: Transaction payment amount in USD, the decimal part is worth paying attention to.
- **ProductCD**: Product code, the product for each transaction. It may not necessarily be an actual product but may also refer to a service.
- **card1-card6**: Payment card information, such as card type, card category, issue bank, country, etc.
- **addr1-addr2**: Address, billing region and billing country
- **dist**: Distances between (not limited) billing address, mailing address, zip code, IP address, phone area, etc.
- **P_ and (R__) emaildomain**: Purchaser and recipient email domain, some transactions do not require the recipient, and the corresponding Remaildomain is empty
- **C1-C14**: Counting, such as how many addresses are found to be associated with the payment card, etc. 
- **D1-D15**: Timedelta, such as days between previous transaction, etc.
- **M1-M9**: Match, such as names on card and address, etc.
- **Vxxx:** Vesta engineered rich features, including ranking, counting, and other entity relations. Some V features are missing in different proportions.

**Identity Features**:
- id_01 - id_11:  Numerical features for identity, which is collected by Vesta and security partners such as device rating, ip_domain rating, proxy rating, etc. Also it recorded behavioral fingerprint like account login times/failed to login times, how long an account stayed on the page, etc. 
- DeviceType, DeviceInfo and id_12 - id_38: Categorical Features

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
- Impute all missing values with -999 first which is very fast and model can still find some pattern instead of losing information by dropping them.


## Model 
**Model**
- LightGBM
- CatBosst
- XGBoost

**Performance Metric**: The evaluation index was AUC with imbalanced data with few isFraud = 1 data.

**Training and verification**: 


**Submissions & Leaderboard Scores**

|Model |Public score|Private score|Final rank| 
|------|--------|--------|---|
| LGBM     |0.961445|0.938790|   |
| XGBoost  |0.959627|0.935022|   |
| CatBoost |0.958433|0.933450|   |
| Ensemble |0.963487| 0.941655|  |



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
- catboost



