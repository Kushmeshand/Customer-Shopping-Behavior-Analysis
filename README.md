# Customer Shopping Behavior Analysis: End-to-End Data Analytics Portfolio Project

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Python](https://img.shields.io/badge/Python-3.9%2B-blue.svg)](https://www.python.org/)
[![SQL](https://img.shields.io/badge/SQL-PostgreSQL%20%7C%20MySQL%20%7C%20MSSQL-orange.svg)](https://www.postgresql.org/)
[![Power BI](https://img.shields.io/badge/Power%20BI-Desktop-gold.svg)](https://powerbi.microsoft.com/)

An enterprise-grade, end-to-end customer shopping behavior data analytics project demonstrating data ingestion, exploratory data analysis (EDA), data cleaning, feature engineering, relational database modeling, complex SQL business analytics, interactive Power BI business intelligence reporting, and executive stakeholder presentation.

---

## Table of Contents

1. [Project Overview](#1-project-overview)
2. [Problem Statement](#2-problem-statement)
3. [Project Objectives](#3-project-objectives)
4. [Technologies and Tools Used](#4-technologies-and-tools-used)
5. [Repository Folder and File Structure](#5-repository-folder-and-file-structure)
6. [Dataset Description](#6-dataset-description)
7. [Prerequisites and Software Requirements](#7-prerequisites-and-software-requirements)
8. [Python Environment Setup](#8-python-environment-setup)
9. [Required Python Libraries and Installation Commands](#9-required-python-libraries-and-installation-commands)
10. [Instructions to Execute the Jupyter Notebook](#10-instructions-to-execute-the-jupyter-notebook)
11. [Database Setup and CSV Data Ingestion](#11-database-setup-and-csv-data-ingestion)
12. [Instructions to Execute SQL Queries](#12-instructions-to-execute-sql-queries)
13. [Key Business Questions Addressed (SQL Analysis)](#13-key-business-questions-addressed-sql-analysis)
14. [Actual Findings and Business Insights](#14-actual-findings-and-business-insights)
15. [Instructions to Open and Use the Power BI Dashboard](#15-instructions-to-open-and-use-the-power-bi-dashboard)
16. [Explanation of Dashboard Visualizations](#16-explanation-of-dashboard-visualizations)
17. [Expected Outputs and Deliverables](#17-expected-outputs-and-deliverables)
18. [Troubleshooting Guide](#18-troubleshooting-guide)
19. [Original Author Attribution and License](#19-original-author-attribution-and-license)

---

## 1. Project Overview

Understanding consumer purchasing patterns, demographic spending habits, customer retention, and subscription adoption is critical for retail businesses to optimize inventory, marketing budget allocation, and loyalty programs.

This repository hosts a complete analytical pipeline:
- **Python / Pandas**: Data extraction, statistical summary, median-based category imputation for missing values, snake_case normalization, categorical binning (`age_group`), frequency mapping, and redundant feature pruning.
- **SQL (PostgreSQL / MySQL / MS SQL Server)**: Relational schema ingestion and multi-dimensional querying answering 10 high-impact commercial business questions.
- **Power BI**: Interactive executive dashboard connecting to relational storage to visualize KPIs, categorical revenues, demographic cohorts, and subscription status with cross-filtering capabilities.
- **Documentation & Executive Decks**: Full business problem brief (`Business Problem Document.pdf`), comprehensive analytical report (`Customer Shopping Behavior Analysis.pdf`), and a 10-slide stakeholder presentation (`Customer-Shopping-Behavior-Analysis.pptx`).

---

## 2. Problem Statement

Retail management lacks actionable visibility into:
- The demographic drivers of product revenue across genders and age segments.
- The financial effectiveness of discount campaigns (identifying discount dependency vs. high-spending discount shoppers).
- The ROI of subscription programs: whether subscribers deliver higher customer lifetime value (CLV) or order frequency compared to non-subscribers.
- The logistical impact of shipping choices on basket size.
- Product satisfaction variance across retail merchandise categories.

Without answering these questions with verified transaction data, marketing campaigns remain untargeted and promotional discounts erode product profit margins.

---

## 3. Project Objectives

- Cleanse and standardize consumer transaction data while resolving missing data without introducing bias.
- Engineer domain-specific features (age cohorts, numerical purchase intervals).
- Ingest normalized transactional tables into a relational database management system (RDBMS).
- Formulate and execute analytical SQL queries utilizing window functions, Common Table Expressions (CTEs), case statements, and aggregations.
- Develop an executive Power BI dashboard with dynamic filtering across gender, subscription status, product categories, and shipping types.
- Deliver actionable strategic recommendations to increase subscriber conversion, optimize discount distribution, and maximize revenue.

---

## 4. Technologies and Tools Used

| Tool / Technology | Purpose |
| :--- | :--- |
| **Python 3.9+** | Data manipulation, statistical analysis, and pipeline scripting |
| **Pandas & NumPy** | Data cleaning, quantile binning (`qcut`), categorical encoding, and transformation |
| **SQLAlchemy** | Database abstraction layer and automated DataFrame ingestion |
| **PostgreSQL / pgAdmin 4** | Primary relational database storage and SQL query execution |
| **MySQL / MS SQL Server** | Alternative supported RDBMS backends |
| **Power BI Desktop** | Visual data modeling, DAX measures, and interactive executive reporting |
| **Jupyter Notebook** | Interactive exploratory data analysis and pipeline documentation |
| **Microsoft PowerPoint** | Executive slide presentation for stakeholder review |

---

## 5. Repository Folder and File Structure

```text
Customer-Shopping-Behavior-Analysis/
│
├── Business Problem  Document.pdf             # Executive business problem definition and framing
├── Customer Shopping Behavior Analysis.pdf    # Comprehensive end-to-end analytical project report
├── Customer-Shopping-Behavior-Analysis.pptx   # 10-slide stakeholder executive presentation
├── Customer_Shopping_Behavior_Analysis.ipynb  # Jupyter notebook containing complete Python pipeline
├── customer_behavior_dashboard.pbix           # Power BI interactive business intelligence dashboard
├── customer_behavior_sql_queries.sql          # 10 business SQL analytical queries (PostgreSQL dialect)
├── customer_shopping_behavior.csv             # Raw transactional dataset (3,900 customer records)
├── LICENSE                                    # MIT License (Original author: Amlan Mohanty)
└── README.md                                  # Complete project documentation and guide
```

---

## 6. Dataset Description

The analysis operates on `customer_shopping_behavior.csv`, which contains **3,900 records** and **18 initial features** detailing customer demographics, transactions, and feedback across 50 US locations:

| Column Name | Data Type | Description |
| :--- | :--- | :--- |
| `Customer ID` | Integer | Unique identifier for each shopper (1 to 3,900) |
| `Age` | Integer | Customer age (range: 18 to 70 years; Mean: 44.07) |
| `Gender` | Object | Shopper gender (`Male`: 2,652, `Female`: 1,248) |
| `Item Purchased` | Object | Name of the purchased product (25 distinct items) |
| `Category` | Object | Merchandise category (`Clothing`, `Accessories`, `Footwear`, `Outerwear`) |
| `Purchase Amount (USD)` | Integer | Transaction amount in USD (range: $20 to $100; Mean: $59.76) |
| `Location` | Object | US State of transaction (50 states represented) |
| `Size` | Object | Apparel size (`S`, `M`, `L`, `XL`) |
| `Color` | Object | Item color (25 unique colors) |
| `Season` | Object | Season of purchase (`Spring`, `Summer`, `Fall`, `Winter`) |
| `Review Rating` | Float | Customer rating (2.5 to 5.0; 37 missing values imputed) |
| `Subscription Status` | Object | Customer subscription enrollment (`Yes` / `No`) |
| `Shipping Type` | Object | Delivery method (`Free Shipping`, `Standard`, `Express`, `Next Day Air`, etc.) |
| `Discount Applied` | Object | Whether a discount was applied (`Yes` / `No`) |
| `Promo Code Used` | Object | Redundant field identical to `Discount Applied` (dropped during cleanup) |
| `Previous Purchases` | Integer | Total prior transactions (range: 1 to 50; Mean: 25.35) |
| `Payment Method` | Object | Payment instrument (`Credit Card`, `PayPal`, `Venmo`, `Cash`, `Bank Transfer`, etc.) |
| `Frequency of Purchases`| Object | Stated shopping cadence (`Weekly`, `Fortnightly`, `Monthly`, `Quarterly`, `Annually`, etc.) |

---

## 7. Prerequisites and Software Requirements

To reproduce the analysis locally, install the following software:

1. **Python**: Version 3.9 or higher (Python 3.10, 3.11, 3.12, 3.13, 3.14 supported).
2. **Jupyter Notebook or JupyterLab**: To run `.ipynb` files.
3. **Database Server** (choose any):
   - **PostgreSQL 12+** and **pgAdmin 4** (Recommended and native to `customer_behavior_sql_queries.sql`).
   - Alternatively: **MySQL 8.0+** or **Microsoft SQL Server 2019+**.
4. **Power BI Desktop**: Required to open and view `customer_behavior_dashboard.pbix` (available free on Windows).
5. **Git**: For version control.

---

## 8. Python Environment Setup

Create an isolated virtual environment to avoid dependency conflicts:

### Windows (PowerShell / Command Prompt):
```powershell
# Navigate to project directory
cd "Customer-Shopping-Behavior-Analysis"

# Create virtual environment
python -m venv venv

# Activate virtual environment
.\venv\Scripts\Activate.ps1
# Or in standard cmd.exe:
# .\venv\Scripts\activate.bat
```

### macOS / Linux:
```bash
cd Customer-Shopping-Behavior-Analysis
python3 -m venv venv
source venv/bin/activate
```

---

## 9. Required Python Libraries and Installation Commands

Install core data processing and database connectivity packages:

```bash
pip install --upgrade pip
pip install pandas numpy jupyter notebook
```

For database connectivity (install depending on your target database):

```bash
# For PostgreSQL (Default):
pip install psycopg2-binary sqlalchemy

# For MySQL:
pip install pymysql sqlalchemy cryptography

# For Microsoft SQL Server:
pip install pyodbc sqlalchemy
```

---

## 10. Instructions to Execute the Jupyter Notebook

1. Ensure your virtual environment is active.
2. Launch Jupyter Notebook from the project root:
   ```bash
   jupyter notebook
   ```
3. In the browser dashboard, open `Customer_Shopping_Behavior_Analysis.ipynb`.
4. Follow the notebook execution sequence:
   - **Cell 1–5**: Dataset import, shape inspection, and summary statistics (`df.describe(include='all')`).
   - **Cell 6–7**: Imputation of missing values in `Review Rating` using category-specific medians:
     ```python
     df['Review Rating'] = df.groupby('Category')['Review Rating'].transform(lambda x: x.fillna(x.median()))
     ```
   - **Cell 8–9**: Standardization of column names to lowercase snake_case and renaming `purchase_amount_(usd)` to `purchase_amount`.
   - **Cell 10–11**: Feature engineering of quartile age segments:
     ```python
     labels = ['Young Adult', 'Adult', 'Middle-aged', 'Senior']
     df['age_group'] = pd.qcut(df['age'], q=4, labels=labels)
     ```
   - **Cell 12–21**: Mapping purchase frequencies to numeric intervals in days:
     - `Weekly` &rarr; 7
     - `Fortnightly` / `Bi-Weekly` &rarr; 14
     - `Monthly` &rarr; 30
     - `Quarterly` / `Every 3 Months` &rarr; 90
     - `Annually` &rarr; 365
   - **Cell 22–25**: Verification that `(df['discount_applied'] == df['promo_code_used']).all()` is `True`, and dropping the redundant `promo_code_used` column.
   - **Cell 26–28**: Ingestion of the cleansed DataFrame into PostgreSQL using `df.to_sql('customer', engine, if_exists='replace', index=False)`.

---

## 11. Database Setup and CSV Data Ingestion

### Option A: PostgreSQL via Python / pgAdmin (Recommended)
1. Open pgAdmin 4 (or run via `psql`).
2. Create the target database:
   ```sql
   CREATE DATABASE customer_behavior;
   ```
3. Update connection credentials in `Customer_Shopping_Behavior_Analysis.ipynb`:
   ```python
   from sqlalchemy import create_engine

   username = "postgres"
   password = "your_actual_password"
   host = "localhost"
   port = "5432"
   database = "customer_behavior"

   engine = create_engine(f"postgresql+psycopg2://{username}:{password}@{host}:{port}/{database}")
   df.to_sql("customer", engine, if_exists="replace", index=False)
   ```
4. Verify table creation in pgAdmin:
   ```sql
   SELECT COUNT(*) FROM customer; -- Expected output: 3900
   ```

### Option B: MySQL
```sql
CREATE DATABASE customer_behavior;
```
```python
engine = create_engine("mysql+pymysql://root:your_password@localhost:3306/customer_behavior")
df.to_sql("customer", engine, if_exists="replace", index=False)
```

---

## 12. Instructions to Execute SQL Queries

1. Open pgAdmin 4, DBeaver, VS Code SQLTools, or command-line `psql`.
2. Connect to the `customer_behavior` database.
3. Open `customer_behavior_sql_queries.sql`.
4. Execute the queries sequentially to generate the business outputs documented below.

---

## 13. Key Business Questions Addressed (SQL Analysis)

The project formulates and answers 10 foundational commercial questions:

1. **Gender Revenue Generation**: What is the total revenue generated by male vs. female customers?
2. **High-Value Discount Users**: Which customers used a discount but still spent at or above the average purchase amount?
3. **Product Quality Ratings**: Which are the top 5 products with the highest average customer review rating?
4. **Logistics & Spend**: How does average purchase amount compare between Standard and Express shipping?
5. **Subscription Financial Value**: Do subscribed customers spend more on average and drive higher total revenue?
6. **Discount Penetration**: Which 5 products have the highest percentage of purchases with discounts applied?
7. **Customer Retention Segmentation**: How do customers segment into New (1 purchase), Returning (2–10), and Loyal (>10 purchases)?
8. **Category Product Leaders**: What are the top 3 most purchased items within each merchandise category?
9. **Repeat Buyer Subscription Propensity**: Are high-frequency repeat buyers (>5 previous purchases) currently subscribed?
10. **Demographic Revenue Contribution**: What is the revenue contribution of each age demographic cohort?

---

## 14. Actual Findings and Business Insights

Every metric below has been computed and verified directly from the dataset:

| Analysis Area | Key Findings & Metrics | Business Interpretation & Strategy |
| :--- | :--- | :--- |
| **1. Gender Revenue** | **Male**: \$157,890 (67.74% of revenue; 2,652 shoppers)<br>**Female**: \$75,191 (32.26% of revenue; 1,248 shoppers)<br>**Total Revenue**: \$233,081 | Male shoppers represent the primary revenue engine. Tailor male apparel marketing while crafting targeted campaigns to expand female market penetration. |
| **2. Discount Elasticity** | **839 customers** utilized promotional discounts while exceeding the average basket size of **\$59.76**. | These shoppers are high-value consumers who respond to price incentives without degrading overall order value. Use threshold discounts (e.g., "$10 off orders over $75") to protect margins. |
| **3. Top-Rated Products** | 1. **Gloves**: 3.86<br>2. **Sandals**: 3.84<br>3. **Boots**: 3.82<br>4. **Hat**: 3.80<br>5. **T-shirt**: 3.78 | Footwear and accessories dominate the highest customer satisfaction scores. Feature these items prominently as gateway products in customer acquisition funnels. |
| **4. Shipping Impact** | **Express Shipping**: \$60.48 average spend<br>**Standard Shipping**: \$58.46 average spend | Express shipping users exhibit slightly higher willingness to spend (+3.45%). Offer expedited shipping upgrades at checkout for orders nearing premium thresholds. |
| **5. Subscription Impact** | **Non-Subscribers**: 2,847 customers \| \$59.87 avg \| \$170,436 revenue<br>**Subscribers**: 1,053 customers \| \$59.49 avg \| \$62,645 revenue | Average order value between subscribers and non-subscribers is virtually identical (~$59.50 vs ~$59.87). The primary value of subscriptions must come from purchase frequency and retention rather than basket size. |
| **6. Discount Rates** | 1. **Hat**: 50.00%<br>2. **Sneakers**: 49.66%<br>3. **Coat**: 49.07%<br>4. **Sweater**: 48.17%<br>5. **Pants**: 47.37% | Nearly half of all sales for these 5 products occur under discounts. Review supplier margins on Hats and Sneakers to avoid margin dilution. |
| **7. Customer Segments** | **Loyal (>10 orders)**: 3,116 customers (79.90%)<br>**Returning (2–10 orders)**: 701 customers (17.97%)<br>**New (1 order)**: 83 customers (2.13%) | The retailer boasts an exceptionally loyal customer base (~80% loyal). Focus retention marketing on moving the 701 returning customers into the loyal tier. |
| **8. Category Top Sellers** | - **Accessories**: Jewelry (171), Sunglasses (161), Belt (161)<br>- **Clothing**: Pants (171), Blouse (171), Shirt (169)<br>- **Footwear**: Sandals (160), Shoes (150), Sneakers (145)<br>- **Outerwear**: Jacket (163), Coat (161) | Core inventory demand is concentrated in foundational daily essentials across apparel and accessories. |
| **9. Repeat Buyer Upsell** | Of customers with >5 previous purchases:<br>- **Non-Subscribed**: 2,518 customers (72.44%)<br>- **Subscribed**: 958 customers (27.56%) | **Massive growth opportunity**: 2,518 loyal, repeat buyers have not joined the subscription program. Converting just 20% would add 500+ subscribers. |
| **10. Age Revenue** | 1. **Young Adult**: \$62,143<br>2. **Middle-aged**: \$59,197<br>3. **Adult**: \$55,978<br>4. **Senior**: \$55,763 | Revenue is well distributed across age brackets, with Young Adults generating the largest share. |

---

## 15. Instructions to Open and Use the Power BI Dashboard

1. Install **Power BI Desktop** (Windows).
2. Double-click `customer_behavior_dashboard.pbix` or open Power BI Desktop and select **File &rarr; Open &rarr; Browse reports**.
3. If connected to a live database:
   - Click **Home &rarr; Transform Data &rarr; Data Source Settings**.
   - If prompted for credentials, configure your PostgreSQL database parameters (`localhost`, port `5432`, database `customer_behavior`).
   - Alternatively, change data source to import `customer_shopping_behavior.csv` directly.
4. Interact with the visual filters:
   - Click on the **Gender slicer** (e.g., Male vs. Female) to observe dynamic cross-filtering on category revenue.
   - Select **Subscription Status** (`Yes` / `No`) to view subscriber distribution across product categories.
   - Filter by **Shipping Type** to analyze logistical channel performance.

---

## 16. Explanation of Dashboard Visualizations

The Power BI report (`Page 1`) contains 19 visual containers engineered for executive decision-making:

- **Executive KPI Cards**:
  - `Number of Customers`: Displays the total analyzed cohort (**3,900**).
  - `Average Purchase Amount`: Highlights the storewide baseline basket size (**$59.76**).
  - `Average Review Rating`: Monitors customer brand sentiment (**3.75 / 5.0**).
- **Subscription Status Donut Chart**:
  - Displays the breakdown of subscribers (1,053) vs. non-subscribers (2,847), visualizing market penetration.
- **Revenue by Merchandise Category (Clustered Column Chart)**:
  - Compares aggregate revenue across `Clothing`, `Accessories`, `Footwear`, and `Outerwear`.
- **Customer Volume by Category (Clustered Column Chart)**:
  - Plots customer order volume per category, revealing volume vs. revenue dynamics.
- **Revenue by Age Cohort (Clustered Bar Chart)**:
  - Breaks down revenue performance across `Young Adult`, `Middle-aged`, `Adult`, and `Senior` segments.
- **Customer Count by Age Cohort (Clustered Bar Chart)**:
  - Tracks customer demographic representation across age groups.
- **Interactive Multi-Select Slicers**:
  - `Subscription Status` slicer
  - `Gender` slicer
  - `Category` slicer
  - `Shipping Type` slicer (Free Shipping, Standard, Express, Next Day Air, 2-Day Shipping, Store Pickup)

---

## 17. Expected Outputs and Deliverables

When running this repository end-to-end, you produce:
1. **Cleaned In-Memory Dataset**: Fully validated DataFrame (3,900 rows &times; 19 columns) with imputed ratings and engineered cohorts.
2. **Relational Database Table**: Production table `customer` created in PostgreSQL / MySQL.
3. **10 Structured SQL Result Sets**: Exact numerical outputs answering the core business questions.
4. **Interactive BI Dashboard**: `.pbix` report with working cross-filters and visual aggregations.
5. **Executive Strategy Decks**:
   - `Customer Shopping Behavior Analysis.pdf`: Detailed 10-page analytical report.
   - `Customer-Shopping-Behavior-Analysis.pptx`: 10-slide stakeholder slide deck with executive summaries.

---

## 18. Troubleshooting Guide

### 1. `psycopg2` Installation Error on Windows
- **Issue**: `error: Microsoft Visual C++ 14.0 or greater is required` during `pip install psycopg2`.
- **Fix**: Use the pre-compiled binary wheel:
  ```bash
  pip install psycopg2-binary
  ```

### 2. PostgreSQL Authentication Failure in Python
- **Issue**: `FATAL: password authentication failed for user "postgres"`.
- **Fix**: Ensure your PostgreSQL server service is running in Windows Services (`services.msc`), and verify that the password in your connection URI matches your pgAdmin superuser password:
  ```python
  engine = create_engine("postgresql+psycopg2://postgres:YOUR_PASSWORD@localhost:5432/customer_behavior")
  ```

### 3. Missing `customer_shopping_behavior.csv` Path Error
- **Issue**: `FileNotFoundError: [Errno 2] No such file or directory: 'customer_shopping_behavior.csv'`.
- **Fix**: Run Jupyter Notebook directly from the repository root folder where `customer_shopping_behavior.csv` resides, or provide the absolute path in `pd.read_csv()`.

### 4. Power BI Data Source Refresh Error
- **Issue**: Power BI reports an error refreshing data when opening `.pbix`.
- **Fix**: Power BI was designed using PostgreSQL connection settings. In Power BI, go to **File &rarr; Options and Settings &rarr; Data Source Settings &rarr; Change Source**, and update your server host and database name, or switch data source directly to the local CSV file.

---

## 19. Original Author Attribution and License

### Original Author Attribution
This project is an enhanced and verified distribution based on the original work by:
- **Amlan Mohanty**
  - **GitHub**: [@amlanmohanty1](https://github.com/amlanmohanty1)
  - **Original Repository**: [customer-trends-data-analysis-SQL-Python-PowerBI](https://github.com/amlanmohanty1/customer-trends-data-analysis-SQL-Python-PowerBI)
  - **YouTube**: [Amlan Mohanty](https://www.youtube.com/@amlanmohanty1)
  - **LinkedIn**: [Amlan Mohanty](https://www.linkedin.com/in/amlanmohanty1/)

### Maintained and Published By
- **Kush Meshand**
  - **GitHub**: [@Kushmeshand](https://github.com/Kushmeshand)
  - **Repository**: [Customer-Shopping-Behavior-Analysis](https://github.com/Kushmeshand/Customer-Shopping-Behavior-Analysis)

### License
This repository is licensed under the **MIT License**. See the full text in [LICENSE](file:///d:/Data%20analyst%20project%201/LICENSE).
You are free to use, modify, and build upon this project for educational, academic, portfolio, and commercial purposes with appropriate attribution to the original author.
