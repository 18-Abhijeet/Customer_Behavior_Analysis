# Customer Shopping Behavior Analysis

## Overview
An end-to-end data analytics project examining retail customer purchasing patterns, demographic trends, product performance, and subscription engagement across 3,900 transactions. This project demonstrates a complete analytical workflow—from raw data cleaning and feature engineering in Python to relational querying in PostgreSQL, interactive dashboarding in Power BI, and executive storytelling via a Gamma presentation.

---

## Dataset
* **Source File:** `customer_shopping_behavior.csv`
* **Dimensions:** 3,900 rows × 18 columns
* **Key Attributes:**
  * **Customer Demographics:** `Customer ID`, `Age`, `Gender`, `Location`
  * **Transaction Details:** `Item Purchased`, `Category`, `Purchase Amount (USD)`, `Size`, `Color`, `Season`
  * **Behavioral & Engagement Metrics:** `Review Rating`, `Subscription Status`, `Shipping Type`, `Discount Applied`, `Promo Code Used`, `Previous Purchases`, `Payment Method`, `Frequency of Purchases`

---

## Tools & Technologies
* **Python (Pandas, SQLAlchemy, Psycopg2):** Data loading, exploratory data analysis (EDA), missing value imputation, feature engineering, and database ingestion.
* **PostgreSQL:** Relational data storage and SQL-based business intelligence querying (CTEs, window functions, aggregations).
* **Power BI:** Interactive dashboard development for KPI tracking and visual exploration.
* **Gamma:** Executive presentation deck summarizing findings and strategic recommendations.

---

## Project Workflow (Steps)

### 1. Data Loading & EDA (Python)
* Loaded the raw CSV dataset into a Pandas DataFrame and inspected structure, data types, and summary statistics (`df.info()`, `df.describe()`).
* Identified 37 missing values in the `Review Rating` column.

### 2. Data Cleaning & Feature Engineering (Python)
* **Missing Value Imputation:** Imputed missing `Review Rating` values using the median rating grouped by product `Category`.
* **Schema Standardization:** Standardized all column names to `snake_case`.
* **Redundancy Removal:** Verified that `discount_applied` and `promo_code_used` contained identical values across all records and dropped `promo_code_used`.
* **Feature Creation:**
  * `age_group`: Categorized customers into four quartile-based cohorts (`Young Adult`, `Adult`, `Middle-aged`, `Senior`).
  * `purchase_frequency_days`: Mapped text-based purchase frequencies (e.g., Weekly, Quarterly, Annually) into numerical day intervals.

### 3. Database Integration & SQL Analysis (PostgreSQL)
* Exported the cleaned DataFrame into a PostgreSQL database (`customer_behavior`, table: `customer`) using SQLAlchemy.
* Executed 10 analytical SQL queries (`Customer_Behavior_Queries.sql`) to answer core business questions regarding revenue drivers, customer segmentation, discount dependency, and top-performing products.

### 4. Data Visualization & Reporting (Power BI & Gamma)
* Connected Power BI to the dataset to build an interactive executive dashboard (`Customer_Behavior_Dashboard.pbix`).
* Synthesized insights and actionable business recommendations into a 10-slide presentation deck using Gamma (`Customer-Shopping-Behavior-Analysis.pptx`).

# Dashboard
<img width="1305" height="732" alt="Customer_Analysis_Dashboard" src="https://github.com/user-attachments/assets/885adc60-5997-462e-8f21-c16ccfd4c8a6" />

## Key Results & Insights
* **Customer Segmentation:** Out of 3,900 customers, **3,116** are *Loyal* (>10 previous purchases), **701** are *Returning* (2–10 purchases), and **83** are *New* (1 purchase).
* **Revenue by Demographics:**
  * Male customers generated **$157,890** in revenue compared to **$75,191** from female customers.
  * **Young Adults** and **Middle-aged** cohorts represent the highest revenue-generating age groups.
* **Subscription Impact:** Non-subscribers account for **$170,436** in total revenue (avg. spend `$59.87`), while subscribers contribute **$62,645** (avg. spend `$59.49`).
* **Discount Sensitivity:** **839** customers utilized a discount while still spending above the overall average purchase amount. Items with the highest discount application rates include **Hats (50.0%)**, **Sneakers (49.66%)**, and **Coats (49.07%)**.
* **Top-Rated Products:** **Gloves (3.86)**, **Sandals (3.84)**, and **Boots (3.82)** achieved the highest average customer review ratings.

### Strategic Recommendations
1. **Boost Subscriptions:** Promote exclusive member perks to convert repeat buyers into recurring subscribers.
2. **Retention Campaigns:** Target the 701 *Returning* customers with loyalty incentives to transition them into the *Loyal* tier.
3. **Optimize Discounting:** Re-evaluate promotional pricing on high-discount SKUs (Hats, Sneakers, Coats) to protect profit margins.
4. **Targeted Marketing:** Focus ad spend on high-performing Young Adult and Middle-aged segments and highlight top-rated footwear and accessories.
