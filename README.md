💰 Financial Expense Tracker

A data analytics project for cleaning, transforming, and visualizing financial transaction data using Python, Pandas, NumPy, and Microsoft Power BI.

The project takes raw expense/income transaction data, performs data cleaning and validation, creates useful time-based fields and outlier indicators, and presents the results through an interactive Power BI dashboard.

---

📊 Dashboard Preview

"Financial Expense Tracker Dashboard" (Screenshot%202026-09-17%20155927.png)

The Power BI dashboard provides an interactive view of financial performance for FY 2024–25, including income, expenses, savings, expense categories, monthly trends, and payment modes.

---

🚀 Project Overview

Managing transaction data manually can make it difficult to understand spending patterns and financial performance.

This project provides a simple analytics workflow:

Raw Transaction Data
        ↓
Data Cleaning & Preprocessing
        ↓
Data Validation & Feature Engineering
        ↓
Cleaned Dataset
        ↓
Power BI Dashboard
        ↓
Financial Insights

The Python/Jupyter Notebook workflow prepares the data, while Power BI is used to build an interactive dashboard for analysis.

---

✨ Key Features

🧹 Data Cleaning

- Handles missing values in important categorical fields.
- Removes currency symbols and commas from monetary values.
- Converts transaction amounts into numeric values.
- Standardizes category names.
- Removes records with missing dates.
- Removes duplicate transactions.
- Fills missing budget limits with "0".

📅 Date & Time Features

The cleaned dataset includes:

- Year
- Month
- Month Name
- Quarter
- Weekday

These fields make monthly, quarterly, and yearly analysis easier in Power BI.

🔎 Data Validation

The preprocessing workflow checks that:

- Transaction amounts are non-negative.
- Transaction IDs are unique.
- The cleaned dataset is generated successfully.

📈 Outlier Detection

Expense transactions are evaluated using the 99th percentile of expense amounts.

Transactions above this threshold are flagged using:

Is_Outlier = True

This allows unusually large expenses to be identified during analysis.

📊 Interactive Power BI Dashboard

The dashboard includes:

- Total Income
- Total Expense
- Net Savings
- Savings %
- Expense by Category
- Monthly expense breakdown
- Income vs. expense trend
- Expense by Payment Mode
- Year filter
- Category filter
- Payment Mode filters

---

🛠️ Technologies Used

Technology| Purpose
Python| Data processing and cleaning
Pandas| Data manipulation and transformation
NumPy| Numerical operations
Jupyter Notebook| Data-cleaning workflow
Microsoft Power BI| Interactive data visualization
CSV| Input and processed datasets

---

📁 Project Structure

Financial-Expense-Tracker/
│
├── Finance_Expense_Tracker.pbix
├── expense.py
├── expense_cleaning.ipynb
├── Untitled.ipynb
│
├── raw_expense_data_v2.csv
├── cleaned_expense_data_v2.csv
│
├── Screenshot 2026-09-17 155927.png
│
└── README.md

File Description

"Finance_Expense_Tracker.pbix"
Power BI report containing the interactive financial dashboard.

"expense_cleaning.ipynb"
Main Jupyter Notebook containing the data-cleaning and preprocessing workflow.

"expense.py"
Python dependency/setup note for the data-processing environment.

"raw_expense_data_v2.csv"
Original transaction dataset before preprocessing.

"cleaned_expense_data_v2.csv"
Processed dataset containing cleaned values and additional analytical fields.

"Untitled.ipynb"
Empty Jupyter Notebook retained from the original project files.

---

🔄 Data Cleaning Process

The notebook performs the following operations:

1. Load the Dataset

df = pd.read_csv("raw_expense_data_v2.csv")

2. Convert Amount to Numeric

Currency symbols and commas are removed before converting the "Amount" column to floating-point numbers.

df["Amount"] = (
    df["Amount"].astype(str)
    .str.replace("₹", "", regex=False)
    .str.replace(",", "", regex=False)
    .astype(float)
)

3. Standardize Categories

df["Category"] = df["Category"].str.strip().str.title()

4. Handle Missing Values

Missing values are replaced with meaningful defaults for fields such as:

- Category
- Subcategory
- Payment Mode
- Merchant
- Tags
- Necessity
- Budget Limit

5. Remove Invalid Dates

Transactions without a valid date are removed.

6. Create Date Features

df["Year"] = df["Date"].dt.year
df["Month"] = df["Date"].dt.month
df["MonthName"] = df["Date"].dt.strftime("%b")
df["Quarter"] = "Q" + df["Date"].dt.quarter.astype(str)
df["Weekday"] = df["Date"].dt.day_name()

7. Remove Duplicates

Duplicate transactions are removed from the dataset.

8. Detect Outliers

The 99th percentile of expense amounts is calculated and unusually high expenses are flagged.

9. Validate the Dataset

The notebook verifies that amounts are non-negative and transaction IDs are unique.

10. Export Cleaned Data

df.to_csv("cleaned_expense_data_v2.csv", index=False)

---

📦 Dataset Information

The project contains two CSV datasets.

Raw Dataset

- Rows: 2,538
- Columns: 14

Main fields include:

Transaction ID
Date
Type
Category
Subcategory
Amount
Payment Mode
Account
Recurring
Necessity
Merchant
Budget Limit
Description
Tags

Cleaned Dataset

- Rows: 2,444
- Columns: 20

Additional analytical columns include:

Year
Month
MonthName
Quarter
Weekday
Is_Outlier

The difference in row count is primarily due to preprocessing operations such as removing records with missing dates and duplicate transactions.

---

📊 Dashboard Metrics

The Power BI dashboard presents high-level financial KPIs such as:

- Total Income
- Total Expense
- Net Savings
- Savings %

It also allows the data to be explored using filters such as Year, Category, and Payment Mode.

The dashboard visualizes expense distribution across categories including areas such as Food, Entertainment, Shopping, Transport, Groceries, Rent, Subscriptions, Utilities, Healthcare, Education, Insurance, and Uncategorized transactions.

---

💻 How to Run the Python/Jupyter Workflow

Prerequisites

Install Python 3.x and the required libraries:

pip install pandas numpy jupyter

Run the Notebook

Start Jupyter Notebook:

jupyter notebook

Open:

expense_cleaning.ipynb

Make sure "raw_expense_data_v2.csv" is in the same directory as the notebook.

Run the cells in order.

The cleaned dataset will be generated as:

cleaned_expense_data_v2.csv

---

📊 Open the Power BI Dashboard

To explore the dashboard:

1. Install Microsoft Power BI Desktop.
2. Open:
   Finance_Expense_Tracker.pbix
3. If Power BI asks for the data source location, update the CSV file path to the location of:
   cleaned_expense_data_v2.csv
4. Refresh the report if required.
5. Use the available filters and visualizations to explore the financial data.

---

🎯 Learning Outcomes

This project demonstrates practical skills in:

- Data cleaning
- Data preprocessing
- Missing-value handling
- Duplicate detection
- Data validation
- Feature engineering
- Outlier detection
- Exploratory data analysis
- Data visualization
- Power BI dashboard development
- Python and Pandas
- Working with CSV datasets

---

🔮 Future Improvements

Possible future enhancements include:

- Add automated monthly budget alerts.
- Add spending forecasts using machine learning.
- Add recurring-expense analysis.
- Add personal savings goals.
- Add year-over-year comparison.
- Add category-level budget vs. actual analysis.
- Automate the data-cleaning pipeline.
- Connect Power BI directly to a database.
- Add more advanced financial KPIs.

---

⚠️ Data Privacy

This repository contains transaction-style data for project and analytics purposes.

If the dataset is based on real financial information, sensitive personal or financial details should be removed or anonymized before making the repository public.

Do not upload:

- Bank account credentials
- Passwords
- API keys
- Card numbers
- Personally identifiable financial information

---

👨‍💻 Author

Mohammad Akhil K A

MCA Student | Data Analytics & Software Development

GitHub: "@mohammadakhil-arch" (https://github.com/mohammadakhil-arch)

---

⭐ Project

If you find this project useful for learning data analytics, Python, or Power BI, feel free to explore the repository and build upon it.
