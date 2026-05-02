# Financial Risk Analysis: Data Cleaning, Transformation, and Visualization

## 📋 Project Overview
This project analyzes financial transaction data to understand user behavior, transaction patterns, and associated risk levels. By merging transaction records with economic indicators (market volatility, interest rates, etc.), the analysis identifies patterns and anomalies to support effective financial decision-making.

---

## 👤 Student Information
| Field | Details |
| :--- | :--- |
| **Name** | Akash. P |
| **Batch** | DA-ANB11 |
| **Mail Id** | akashraj894@gmail.com |
| **Project Domain** | Finance |
| **Tools Used** | Python, Power BI |
| **Mentor** | Kumaran. M |
| **Submission Date** | 01-05-2026 |

---

## 🔗 Quick Links
- **Raw Dataset:** [GitHub Link](https://github.com/akashraj894-hub/Main-Project-Python/blob/main/dirty%20financial%20dataset.csv)
- **Cleaned Dataset:** [GitHub Link](https://github.com/akashraj894-hub/Main-Project-Python/blob/main/cleaned%20data%20final.xlsx)
- **Source (Kaggle):** [Kaggle Dataset](https://www.kaggle.com/datasets/txtpwsss/dirty-financial-risk-dataset)
- **Power BI Dashboard:** [Download .pbix](https://github.com/akashraj894-hub/Main-Project-Python/blob/main/Power%20BI%20Finance.pbix)

---

## 🛠️ Tools & Techniques
*   **Python:** Data cleaning, handling missing values, and feature engineering.
*   **Power BI:** Interactive dashboards and advanced KPI visualizations.
*   **Analysis Types:** Descriptive, Diagnostic, Predictive (trend analysis), and Prescriptive recommendations.

---

## 📊 Derived Features for Enhanced Analysis
To deepen the insights, the following columns were engineered:
*   **Net Transaction Amount:** Validates actual money flow based on transaction type.
*   **Transaction Month/Year:** Extracted from timestamps for trend analysis.
*   **Risk Category:** Classified based on credit scores and assigned risk levels.
*   **Market Condition Index:** Derived from volatility, inflation, and interest rates.
*   **User Activity Level:** Grouped by frequency and volume of transactions.

---

## 🧪 Stage 1: Problem Definition & Initial EDA
The goal is to detect high-risk behavior and understand how market conditions impact spending.
```python
import pandas as pd
import numpy as np

# Load the data
df = pd.read_csv('dirty_financial_dataset.csv')

# Dataset Shape
# (3275, 14) -> 3275 rows and 14 columns
