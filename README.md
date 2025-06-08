# Retail Orders Analysis

Analyze, Clean, Store, and Query Retail Data with Python, SQL, and MySQL

---

## Project Summary

This project simulates a real-world **retail analytics pipeline** — from raw CSV ingestion to full SQL-based reporting. It showcases how to:

* Clean and transform retail data with **Pandas**
* Store and manage data in a **MySQL database**
* Run insightful **SQL business queries**
* Build **reproducible pipelines** using Python and SQLAlchemy

Whether you're a data analyst, backend engineer, or business stakeholder, this repo demonstrates how structured data workflows drive decisions in commerce.

---

## Tech Stack

| Area                    | Tools & Technologies                                                                  |
| ----------------------- | ------------------------------------------------------------------------------------- |
| Data Processing      | Python, Pandas                                                                        |
| Database Layer     | MySQL, SQLAlchemy Core                                                                |
| API Integration      | Kaggle API                                                                            |
| Credentials Handling | dotenv, Environment Variables                                                         |
| Dataset Source       | [Kaggle - Retail Orders](https://www.kaggle.com/datasets/ankitbansal06/retail-orders) |

---

## Dataset Overview

The dataset contains retail transactions, including:

* `order_id`, `customer_id`, `product_id`
* Product attributes: category, sub-category, list price, cost, discount
* Shipping & delivery: ship mode, region, state, city
* Transactional data: selling price, profit, order date

---

## Business Goals

This analysis answers key business questions such as:

* What are the **most profitable products and cities**?
* Which **states underperform** in terms of sales?
* What are the **average discounts by category**?
* What **shipping methods are most used**?
* What is the **sales growth over time**?

---

## Workflow Overview

### 1. Environment Setup

* Install packages (`kaggle`, `sqlalchemy`, `pymysql`, `dotenv`, `pandas`)
* Securely load `KAGGLE_USERNAME` and `KAGGLE_KEY` via `.env`

### 2. Data Loading & Inspection

* Download dataset from Kaggle
* Load into Pandas and explore structure and missing data

### 3. Data Cleaning & Transformation

* Replace invalid values and nulls
* Standardize column names
* Create new metrics: `discount`, `selling_price`, `profit`
* Convert `order_date` to datetime

### 4. Data Persistence

* Export cleaned DataFrame to PostgreSQL `orders` table
* Verify with SQL queries and result previews

### 5. SQL Business Analysis

A series of advanced SQL queries answer 25+ real-world business questions using:

* Aggregation (`SUM`, `AVG`)
* Time functions (`YEAR`, `MONTH`)
* Grouping and ranking
* Subqueries and conditional filtering

> All queries and outputs are implemented in the notebook: `orders.ipynb`

---

## 📂 Repository Structure

```bash
.
├── orders.ipynb          # Jupyter notebook with full data analysis
├── README.md             # Project overview and guide
├── .env                  # Environment variables (not tracked in Git)
└── orders/               # Extracted dataset folder
```

---

## Test Questions (Explained)

This project includes a complete test case walkthrough with over 40 data and SQL-focused questions. Below are the tasks and what each question is designed to assess:

🧪 1. Environment Setup

1.1. Library Installation: Validates your ability to install essential Python libraries for data handling (pandas), API usage (kaggle), and database interaction (sqlalchemy, pymysql). This ensures the environment is set up for data-driven workflows.

1.2. Environment Variables: Assesses your understanding of securely handling API credentials. Using .env files with python-dotenv avoids hardcoding sensitive data like KAGGLE_USERNAME and KAGGLE_KEY.

🧪 2. Data Loading and Inspection

2.1. Read CSV: Ensures you can import the dataset (orders.csv) into a Pandas DataFrame and verify the contents with .head() to understand structure and format.

2.2. Shape & Missing Values: Tests your ability to explore data quality. Shape reveals dataset size, and isnull().sum() highlights fields requiring cleaning.

🧪 3. Data Cleaning and Transformation

3.1. Categorical Exploration: Focuses on extracting unique values from object columns to detect issues like inconsistent categories or misspellings.

3.2. Replace Invalids: Practice cleaning dirty data by replacing entries like 'Not Available' or 'unknown' with NaN, prepping for null handling.

3.3. Rename Columns: Encourages using a naming convention (e.g., snake_case) to standardize column names — a crucial step in building clean, consistent data pipelines.

3.4. Create Derived Columns: Tests your ability to engineer features such as discount, selling_price, and profit, which are essential business KPIs derived from raw fields.

3.5. Drop Unneeded Columns: Asks you to remove intermediary fields (like list_price, cost_price) after transformation — a common best practice for efficient data storage and clarity.

3.6. Datetime Conversion: Requires converting order_date to a proper datetime64 format, enabling time-based analysis like monthly or yearly aggregations.

🧪 4. Database Operations

4.1. Connection String: Validate your ability to securely build a SQLAlchemy URI using environment variables (HOST, DATABASE, USER, etc.).

4.2. Establish Connection: Test your ability to connect to MySQL using SQLAlchemy and handle common errors like incorrect credentials or network issues.

4.3. Write to SQL: Push your cleaned DataFrame into MySQL’s orders table. Required to set if_exists='append' and index=False, reflecting real-world data ingestion.

4.4. Read All Rows: Retrieve all data from the table using SQLAlchemy — a vital step for validation and downstream use in dashboards or reports.

🧪 5. SQL Business Analysis

5.1. Revenue by category.

5.2. Top 3 profitable cities.

5.3. Profit margins per product.

5.4. Order count by shipping method.

5.5. Month with highest order volume.

5.6. Products with highest discounts.

5.7. Top cities by sales.

5.8. Average 2023 profit.

5.9. Sub-category sales ranking.

5.10. Average selling price per category.

5.11. Most ordered products.

5.12. Most profitable products.

5.13. Best-performing year.

5.14. Region with lowest discount.

5.15. Yearly sales growth.

5.16. Profit contribution by category.

5.17. Most common shipping mode.

5.18. Region with highest average order value.

5.19. Sales per (category, sub-category) pair.

5.20. Top 3 profitable products per sub-category.

5.21. Monthly order count for 2023.

5.22. States with lowest sales.

5.23. Top 5 states by revenue.

5.24. Average discount per sub-category.

5.25. Top 10 products by revenue.

All answers are implemented in the notebook: `orders.ipynb`

---

## 📬 Contact

**Author:** \[Lucy Joan]
**Email:** \[(mailto:lucyjoanwere2@gmail.com)]

If you're interested in data-driven retail analytics, feel free to connect!
