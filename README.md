# Eniac Discount Strategy Analysis

This project is part of a data analysis case study for **Eniac**, an e-commerce company.  
The goal is to prepare and analyze internal order, product, and brand data in order to understand how discounts affect sales performance.

## Business context

Eniac has an ongoing debate about discounting:

- The Marketing team believes discounts can increase orders, customer acquisition, and long-term growth.
- The Board is concerned that aggressive discounts may reduce revenue and weaken Eniac’s quality positioning.

The analysis aims to provide data-based clarity before making business recommendations.

## Main questions

The project focuses on the following questions:

1. How many products are being discounted?
2. How large are the discounts as a percentage of product prices?
3. How do seasonality and special dates, such as Black Friday and Christmas, affect sales?
4. How can products be grouped into useful categories for reporting?
5. What is the distribution of product prices across categories?
6. How can data collection and data quality be improved?

## Dataset

The project uses four CSV files:

| File | Description |
|---|---|
| `orders.csv` | Order-level information, including order status, date, and total paid |
| `orderlines.csv` | Product-level order lines, including SKU, quantity, unit price, and date |
| `products.csv` | Product catalog information, including product name, description, price, promo price, stock, and type |
| `brands.csv` | Brand reference table |

## Project structure

```text
ENIAC - PANDAS/
│
├── Data_Cleaning_Quality/
│   ├── main.ipynb
│   ├── orders.csv
│   ├── orderlines.csv
│   ├── products.csv
│   └── brands.csv
│
└── Analysing/
    ├── main.ipynb
    ├── orders_new.csv
    ├── order_lines_new.csv
    ├── products_new.csv
    └── brands_new.csv
```

## Workflow

### 1. Data cleaning and quality checks

The first notebook focuses on preparing the data for analysis:

- Loading the raw CSV files.
- Keeping only completed orders.
- Converting date columns to datetime format.
- Checking duplicates and missing values.
- Cleaning or excluding problematic price values.
- Removing orders with products that cannot be matched to the product catalog.
- Checking consistency between order totals and order line totals.
- Exporting cleaned CSV files for the analysis notebook.

### 2. Analysis

The second notebook will use the cleaned data to answer the business questions around discounts, sales, seasonality, and product categories.

### 3. Final presentation

The final output will be a concise presentation for the company board, focused on the main findings and business recommendations.

## Current status

This repository is a work in progress.

Completed:

- Initial data cleaning notebook
- Cleaned datasets exported for analysis

Next steps:

- Review and improve the cleaning logic
- Build the main analysis notebook
- Create discount-related metrics
- Analyze seasonality and special dates
- Prepare final recommendations

## Tools

- Python
- Pandas
- NumPy
- Jupyter Notebook

## Notes

This is a learning project. The main focus is not only writing code, but also practicing a realistic data analysis workflow: understanding the business question, checking data quality, preparing reliable data, and translating results into business recommendations.
