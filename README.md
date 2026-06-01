# 🛍️ Customer Behavior Analysis

A data analytics project exploring customer purchasing patterns, demographics, and behavioral trends across 3,900 retail/e-commerce transactions. The pipeline covers data cleaning, feature engineering, PostgreSQL integration, and Power BI visualization.

---

## 📁 Project Structure
Customer-Behavior-Analysis/
├── customer_shopping_behavior.csv               # Raw dataset (3,900 rows, 18 features)
├── Customer_Shopping_Behavior_Analysis.ipynb    # Main analysis notebook
├── Customer_Behavior_Dashboard.pbix             # Power BI dashboard
└── README.md

---

## 📊 Dataset Overview

| Attribute | Detail |
|---|---|
| Records | 3,900 customers |
| Features | 18 columns |
| Purchase Range | $20 – $100 USD |
| Age Range | 18 – 70 years |
| Categories | Clothing, Accessories, Footwear, Outerwear |

**Key columns:** `Age`, `Gender`, `Category`, `Purchase Amount (USD)`, `Season`, `Review Rating`, `Subscription Status`, `Shipping Type`, `Discount Applied`, `Payment Method`, `Frequency of Purchases`, `Previous Purchases`

---

## ⚙️ Pipeline Overview

### 1. Data Cleaning
- Imputed 37 missing `Review Rating` values using **category-level median**
- Standardized all column names to `snake_case`
- Dropped `Promo Code Used` — confirmed 100% identical to `Discount Applied`

### 2. Feature Engineering
- **`age_group`** — quartile-based segmentation: `Young Adult`, `Adult`, `Middle-Aged`, `Senior`
- **`purchase_frequency_days`** — mapped textual labels to numeric days (e.g. `Weekly → 7`, `Annually → 365`)

### 3. Database Integration
- Loaded cleaned DataFrame into **PostgreSQL** via SQLAlchemy + psycopg2
- Table: `customer` | Database: `customer_behavior`

---

## 🔍 Key Findings

- **Clothing** is the most purchased category (44.5% of transactions)
- **Senior customers (55–70)** are the largest age segment (28.3%)
- Average purchase value is consistent across all categories (~$59–$60)
- **Discounts have minimal impact** on average order value ($60.13 no discount vs $59.28 with discount)
- Purchase frequency is evenly spread — no single dominant buying cadence
- All 6 payment methods used near-equally; PayPal leads marginally (17.4%)
- **Fall** generates the highest seasonal revenue ($60,018); Summer the lowest ($55,777)

---

## 🚀 Getting Started

### Prerequisites

```bash
pip install pandas sqlalchemy psycopg2-binary jupyter
```

### Running the Notebook

```bash
git clone https://github.com/FixMyCodeNow/Customer-Behavior-Analysis.git
cd Customer-Behavior-Analysis
jupyter notebook Customer_Shopping_Behavior_Analysis.ipynb
```

### PostgreSQL Setup

Create the database first:

```sql
CREATE DATABASE customer_behavior;
```

Then update credentials in the notebook:

```python
username = 'your_username'
password = 'your_password'
host     = 'localhost'
port     = '5432'
database = 'customer_behavior'
```

---

## 📈 Power BI Dashboard

Open `Customer_Behavior_Dashboard.pbix` in Power BI Desktop. The dashboard includes:

- Sales KPIs (total revenue, avg. purchase, transaction count)
- Category & seasonal revenue breakdown
- Customer demographics (age group, gender)
- Payment method distribution
- Subscription vs. non-subscriber comparison
- Purchase frequency distribution

> **Note:** Update the PostgreSQL connection string in Power BI's data source settings to match your local credentials.

---

## 🛠️ Tech Stack

| Tool | Purpose |
|---|---|
| Python 3 + Pandas | Data cleaning & feature engineering |
| Jupyter Notebook | Exploratory data analysis |
| PostgreSQL | Relational data storage |
| SQLAlchemy + psycopg2 | Python–PostgreSQL connectivity |
| Microsoft Power BI | Interactive dashboard |

---

## 📄 License

This project is for educational and analytical purposes.
