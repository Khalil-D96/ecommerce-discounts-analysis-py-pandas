# Eniac Discount Strategy Analysis

This project analyzes internal sales data from **Eniac**, an e-commerce company, to explore whether discounting is associated with better sales performance.

The business question behind the project is simple but important:

> Are discounts helping Eniac grow, or are they reducing revenue quality and weakening the company’s premium positioning?

The analysis was completed as part of a data analytics training project using Python and Pandas.

---

## Business context

Eniac has an internal debate about its discount strategy:

- The Marketing team believes discounts can increase orders, customer acquisition, and long-term growth.
- The Board is concerned that aggressive discounting may reduce revenue and push the company away from a quality-focused market position.

The goal of this project is to use available sales, product, and order data to provide a careful, data-based view of this debate.

---

## Main questions

The project focuses on these questions:

1. How many products are being discounted?
2. How large are the realized discounts as a percentage of product prices?
3. How do seasonality and special dates, such as Black Friday and Christmas, affect sales?
4. How can products be classified into useful business categories?
5. What is the distribution of product prices across categories?
6. What data quality issues limit the analysis?
7. How could data collection be improved in the future?

---

## Dataset

The project uses four CSV files:

| File | Description |
|---|---|
| `orders.csv` | Order-level data, including order status, creation date, and total paid |
| `orderlines.csv` | Transaction-level product lines, including SKU, quantity, unit price, and date |
| `products.csv` | Product catalog data, including product name, description, price, promo price, stock, and type |
| `brands.csv` | Brand reference table |

---

## Workflow

### 1. Data cleaning and quality checks

The first notebook prepares the raw data for analysis. The main steps are:

- Load the raw CSV files.
- Keep only completed orders.
- Filter order lines so they match completed orders only.
- Convert date and price columns into usable formats.
- Check duplicates, missing values, and table relationships.
- Clean malformed price values where possible instead of immediately dropping them.
- Remove or flag records that cannot be reliably used.
- Export cleaned datasets for the analysis notebook.

A conservative cleaning approach was used where possible: suspicious values were investigated and corrected when the pattern was clear, instead of removing all unusual records automatically.

### 2. Discount and sales analysis

The second notebook uses the cleaned data to analyze sales performance, discount exposure, seasonality, and product categories.

The main discount metric is **discount**, calculated as:

```text
discount = catalog price - actual unit price paid
```

This means the analysis compares the product catalog price with the transaction price in the order line.

Important note: this should not be interpreted as the exact promotional discount offered to the customer, because catalog prices may not be fully historical.

---

## Key findings

### 1. Discounts are very common

Discounts appear across most of the dataset:

- Around **95% of sold products** were discounted at least once.
- Around **92% of valid order lines** were discounted.
- Around **95% of product revenue** came from discounted order lines.

This shows that discounting is deeply embedded in Eniac’s sales activity. However, because discounts are so common, it becomes difficult to compare discounted and non-discounted sales fairly.

### 2. Most revenue does not come from extreme discounts

Most revenue comes from low-to-moderate discount.

Very aggressive discounts account for only a small share of total product revenue.

This suggests that heavy discounting is not the main driver of revenue in the dataset.

### 3. Seasonality is important

Revenue increases strongly around special periods such as **Black Friday**, **Christmas**, and the winter shopping season.

These periods also include high discount activity, but the analysis cannot separate the effect of discounts from seasonal demand, campaign timing, product mix, or customer behavior.

### 4. The relationship between discount size and revenue is not clearly causal

The analysis does not provide strong evidence that larger discounts directly create higher revenue.

Discounts are associated with high-sales periods, but association is not the same as causation.

### 5. Product categories matter

Discount decisions should therefore not be made at company level only. Different product categories may need different pricing and promotion strategies.

---

## Final conclusion

The analysis does **not** prove that discounts are the main cause of higher sales.

A more careful conclusion is:

> Discounts are a major part of Eniac’s sales strategy and are strongly present during high-sales periods. However, the current data does not prove that discounts caused the higher sales. Eniac should avoid aggressive across-the-board discounting and instead test targeted discounts by product category, season, and campaign type.

---

## Business recommendations

1. **Avoid aggressive company-wide discounts.**  
   Very high discounts contribute only a small share of revenue and may reduce margins.

2. **Treat Black Friday separately.**  
   Black Friday behavior should not be generalized to normal sales periods.

3. **Run controlled experiments.**  
   A/B tests or controlled campaigns are needed to measure the real causal effect of discounts.

4. **Include profitability in future decisions.**  
   Revenue alone is not enough. Cost and margin data are necessary to know whether discounts are profitable.

---

## Limitations

- Product catalog prices may not be historical.
- `promo_price` is a product-level field and may not represent the promotion active at the time of each order.
- Cost and margin data are not available.
- Customer-level data is not available, so acquisition, retention, and lifetime value cannot be measured.
- March 2018 is incomplete and should not be compared directly with full months.
- Discounts are very common, which makes the non-discounted comparison group small.
- Seasonality, product mix, stock availability, and marketing campaigns may affect revenue.

---

## Data collection improvements

To answer the business question more confidently, Eniac should improve collection of:

- Historical product prices by SKU and date.
- Promotion ID, campaign name, and discount rule.
- Acquisition channel and campaign source.
- Clean product category taxonomy.
- Shipping fees and tax separation from product revenue.
- Clear distinction between catalog price, promotional price, coupon discount, and final transaction price.

---

## Tools used

- Python
- Pandas
- NumPy
- Matplotlib
- Jupyter Notebook

---

## How to run the project

1. Open `data_cleaning_quality` notebook in `notebooks/` and run all cells.
2. Confirm that the cleaned CSV files are exported successfully.
3. Open `data_analysing` notebook and run all cells.
4. Review the charts, conclusions, limitations, and recommendations.

---

## Note

This is a learning project. The focus is not only on producing charts, but also on practicing a realistic data analysis workflow: understanding the business problem, checking data quality, building reliable metrics, and translating results into careful business recommendations.
