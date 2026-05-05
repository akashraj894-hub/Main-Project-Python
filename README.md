# 💰 Financial Risk Analysis Project

## 👨‍💻 Author

**Akash P**
📧 [akashraj894@gmail.com](mailto:akashraj894@gmail.com)

---

## 📌 Project Overview

This project focuses on analyzing financial transaction data to understand user behavior, transaction patterns, and associated risk levels.

The dataset includes:

* Transaction details (Deposit, Withdrawal, Transfer, Investment)
* Account balance and transaction amount
* Credit score and risk level
* Market indicators (Inflation, Interest Rate, Volatility)
* Device usage metrics

---

## 🎯 Objective

* Perform **data cleaning and preprocessing**
* Analyze financial risk patterns
* Understand relationship between **credit score & risk level**
* Identify **high-risk customers**
* Build **visual insights using Python & Power BI**

---

## 📂 Dataset Links

* 🔗 Raw Dataset:
  https://github.com/akashraj894-hub/Main-Project-Python/blob/main/dirty_financial_dataset.csv

* 🔗 Cleaned Dataset:
  https://github.com/akashraj894-hub/Main-Project-Python/blob/main/cleaned_data_final.xlsx

* 🔗 Power BI Dashboard:
  https://github.com/akashraj894-hub/Main-Project-Python/blob/main/Power%20BI%20Finance.pbix

* 🔗 Source: Kaggle Financial Risk Dataset

---

## ⚙️ Tools & Technologies

* Python
* Pandas
* NumPy
* Matplotlib
* Seaborn
* Power BI

---

## 🧠 Project Workflow

### 🔹 Stage 1: Data Loading & Understanding

```python
import pandas as pd

# Load dataset
df = pd.read_csv('dirty_financial_dataset.csv')

# Basic checks
df.head()
df.shape
df.info()
df.describe()

# Missing & duplicates
df.isnull().sum()
df.duplicated().sum()
```

---

### 🔹 Stage 2: Data Cleaning & Preprocessing

```python
# Remove duplicates
df = df.drop_duplicates(subset='user_id', keep='first')

# Remove USD symbol
df['transaction_amount'] = df['transaction_amount'].replace('USD', '', regex=True)

# Remove $ in balance
df['account_balance'] = df['account_balance'].replace('[$]', '', regex=True)

# Convert to numeric
cols = ['transaction_amount','account_balance','market_volatility_index',
        'interest_rate','inflation_rate','stock_index_change',
        'investment_duration_days','credit_score',
        'device_cpu_usage','device_memory_usage']

df[cols] = df[cols].apply(pd.to_numeric, errors='coerce')

# Fix transaction type inconsistencies
df['transaction_type'] = df['transaction_type'].str.upper()

# Replace invalid category
mode_val = df['transaction_type'].mode()[0]
df['transaction_type'] = df['transaction_type'].replace('INVALID_CATEGORY_DEFAULT', mode_val)

# Format user_id
df['user_id'] = df['user_id'].str.upper().str.replace('-', '')

# Convert timestamp
df['timestamp'] = pd.to_datetime(df['timestamp'])

# Extract date & time
df['Date'] = df['timestamp'].dt.date
df['Time'] = df['timestamp'].dt.time
```

---

### 🔹 Stage 3: Outlier Handling

```python
Q1 = df["transaction_amount"].quantile(0.25)
Q3 = df["transaction_amount"].quantile(0.75)

IQR = Q3 - Q1

lower = Q1 - 1.5 * IQR
upper = Q3 + 1.5 * IQR

# Filter outliers
df = df[(df["transaction_amount"] >= lower) & (df["transaction_amount"] <= upper)]
```

---

### 🔹 Stage 4: Exploratory Data Analysis (EDA)

#### 📊 Count Plot

```python
import seaborn as sns
import matplotlib.pyplot as plt

sns.countplot(data=df, x='transaction_type')
plt.title("Transaction Type Distribution")
plt.show()
```

---

#### 📊 Histogram

```python
sns.histplot(df['transaction_amount'], bins=30, kde=True)
plt.title("Transaction Amount Distribution")
plt.show()
```

---

#### 📊 Boxplot

```python
sns.boxplot(y=df['transaction_amount'])
plt.title("Transaction Amount Spread")
plt.show()
```

---

#### 📊 Scatter Plot

```python
sns.scatterplot(data=df,
                x='transaction_amount',
                y='credit_score',
                hue='risk_level')
plt.title("Transaction vs Credit Score")
plt.show()
```

---

#### 📊 Heatmap

```python
corr = df.corr(numeric_only=True)

sns.heatmap(corr, annot=True)
plt.title("Correlation Matrix")
plt.show()
```

---

## 📈 Key Insights

* 📉 Credit Score has **strong negative relation with Risk Level**
* 💸 High transaction variability seen in high-risk users
* 📊 Investment transactions show **higher average value & risk**
* 📉 Market downturn impacts financial behavior

---

## 📊 Power BI Insights

* Total Transaction Value: ₹60L+
* Investment category = Highest risk
* Credit score higher for investment users
* Market trend shows negative stock movement

---

## 🚀 Outcome

* Identified high-risk customers
* Improved financial pattern understanding
* Built strong business insights
* Created dashboard for decision-making

---

## 🔮 Future Scope

* Machine Learning model for risk prediction
* Real-time fraud detection system
* Advanced dashboard integration

---


