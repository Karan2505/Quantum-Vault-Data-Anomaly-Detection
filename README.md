# Data Anomaly Detection Model

## Overview
This project focuses on analyzing transactional data using **Pandas**, **NumPy**, and **Seaborn** for visualization. The dataset is processed to extract meaningful insights, detect null values, and analyze transaction patterns.

## Table of Contents
- [Installation](#installation)
- [Dataset Overview](#dataset-overview)
- [Data Preprocessing](#data-preprocessing)
- [Exploratory Data Analysis (EDA)](#exploratory-data-analysis-eda)
- [Transaction Type Classification](#transaction-type-classification)
- [Visualization](#visualization)
- [Results and Insights](#results-and-insights)
- [Future Enhancements](#future-enhancements)

---

## Installation
Ensure you have Python installed along with the required dependencies:
```bash
pip install pandas numpy seaborn
```

---

## Dataset Overview
The dataset consists of transactional details, including:
- **Date**: Transaction date
- **Account ID**: Unique identifier for each account
- **Type**: Transaction type (Credit, Withdrawal, etc.)
- **Amount**: Transaction amount
- **Transaction ID**: Unique ID per transaction
- **Balance**: Account balance after the transaction

### Loading the Dataset
```python
import pandas as pd
import numpy as np

df = pd.read_csv('updated_trans.csv')
df.head(20)
```

---

## Data Preprocessing
### Checking for Null Values
```python
df.info()
df.describe()
df.isnull().sum()
```
This step helps identify missing values and data inconsistencies.

### Data Transformation
- Convert the `date` column to DateTime format.
```python
df_trans = df[['date', 'account_id', 'type', 'amount', 'trans_id', 'balance']]
df_trans['date'] = pd.to_datetime(df_trans['date'], format='%y%m%d')
```

---

## Exploratory Data Analysis (EDA)
### Basic Statistical Insights
```python
df_trans.describe()
df_trans.count()
```
This step gives a summary of the numerical attributes in the dataset.

---

## Transaction Type Classification
The transaction types are updated for better readability.
```python
to_replace = {'PRIJEM': 'CREDIT', 'VYDAJ': 'WITHDRAWAL', 'VYBER': 'NOT SURE'}
df_trans['type'] = df_trans['type'].replace(to_replace)
```
### Checking Unique Account IDs
```python
updated_trans = df_trans.head()
updated_trans['account_id'].unique()
```

---

## Visualization
### Distribution of Transaction Amounts
```python
import seaborn as sns
sns.distplot(df_trans['amount'], bins=50)
```

### Count of Transaction Types
```python
sns.countplot(x='type', data=df_trans)
```
These visualizations help in understanding transaction patterns.

---

## Results and Insights
- The dataset provides clear trends in transaction behavior.
- **Majority transactions** fall into specific categories such as `CREDIT` and `WITHDRAWAL`.
- The balance trends over time reveal patterns in account activity.

---

## Future Enhancements
- Implement machine learning models for fraud detection.
- Optimize large-scale data processing.
- Explore additional visualization techniques for deeper insights.

---

## Conclusion
This project successfully demonstrates data analysis techniques on transactional data. By utilizing Pandas and Seaborn, we gain valuable insights into customer spending and deposit patterns.

---

## References
- [Pandas Documentation](https://pandas.pydata.org/)
- [Seaborn Documentation](https://seaborn.pydata.org/)
