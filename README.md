# 🛒 Zepto Data Analysis & Inventory Optimization Dashboard

A data analytics project focused on analyzing Zepto product catalog and inventory data to identify stock availability issues, evaluate pricing and discounts, and generate actionable business insights using **Power BI, Excel, and DAX**.

## 📌 Project Overview

Quick-commerce businesses like Zepto need to manage thousands of products while maintaining availability and competitive pricing. This project analyzes product-level data to understand inventory availability, out-of-stock products, category performance, and discount patterns.

The goal is to transform raw data into meaningful insights that can support better inventory planning, product availability, and pricing decisions.

## 🎯 Project Objectives

- Analyze product availability across different categories.
- Identify out-of-stock products and categories with higher stockout rates.
- Understand product pricing, MRP, selling prices, and discount percentages.
- Build KPI cards and interactive dashboard visuals.
- Highlight potential inventory management issues.
- Recommend data-driven actions to improve product availability.

## 🛠️ Tools & Technologies

| Tool | Purpose |
|---|---|
| Microsoft Excel | Data inspection and cleaning |
| Power BI | Dashboard design and visualization |
| DAX | KPI and calculated measure creation |
| Data Analytics | Identifying trends and business insights |
| GitHub | Project documentation and version control |

## 📂 Dataset Description

The dataset contains product-level information, including:

- `Category` — Product category
- `name` — Product name
- `mrp` — Maximum retail price
- `discountPercent` — Discount percentage
- `availableQuantity` — Available quantity field
- `discountedSellingPrice` — Discounted selling price
- `weightInGms` — Product weight in grams
- `outOfStock` — Product stock availability status
- `quantity` — Quantity-related field requiring source validation before interpreting it as units sold

**Dataset size:** 3,730 product records and 1,673 distinct product names in the analyzed dataset.

*Note: The dataset represents product/catalog information rather than a verified transaction history. Therefore, sales, profit, lost revenue, and demand trends cannot be confirmed without additional sales and time-based data.*

## 🧹 Data Cleaning & Preparation

The following data preparation steps were performed:

- Inspected the dataset for missing and inconsistent values.
- Cleaned product names while retaining the original `name` column.
- Standardized the `outOfStock` field into a consistent Boolean format.
- Reviewed numeric columns for appropriate data types.
- Prepared the cleaned dataset for analysis and visualization.
- Validated metric definitions to avoid confusing product records with actual sales transactions.

## 📊 Key Performance Indicators (KPIs)

The dashboard focuses on the following metrics:

1. **Total Products:** Number of distinct product names.
2. **Total Product Records:** Total rows available in the dataset.
3. **Out-of-Stock Rate:** Percentage of product records marked out of stock.
4. **Average Discount:** Average discount percentage across records.
5. **Category-Level Availability:** Comparison of stock availability between categories.
6. **Estimated Inventory Value:** An optional estimate using available quantity and selling price, subject to validating the dataset's product-level structure.

## 📈 Dashboard Features

- KPI cards for a quick business overview.
- Category-wise product analysis.
- In-stock versus out-of-stock comparison.
- Discount and pricing analysis.
- Product-level tables to identify availability issues.
- Interactive slicers for category, stock status, and discount range.
- Business insights and recommended actions.

## 🔍 Key Insights

The following findings were observed in the analyzed dataset:

- **Stock Availability:** Approximately 12.1% of product records were marked out of stock.
- **Category-Level Concern:** The Biscuits category showed an out-of-stock rate of approximately 28.6% in the analyzed records.
- **Pricing Opportunities:** Comparing MRP, selling price, and discount percentage can help identify products for further pricing review.
- **Inventory Planning:** Products marked out of stock can be prioritized for availability checks and replenishment review.

*These are snapshot-based observations, not proof of customer demand, lost sales, or the causes of stockouts.*

## 💡 Business Recommendations

### 1. Improve Product Availability
Review out-of-stock products regularly and prioritize replenishment based on business importance and verified demand data.

### 2. Monitor Category-Level Stockouts
Investigate categories with comparatively high out-of-stock rates to identify possible supply or inventory planning issues.

### 3. Review Discount Strategies
Compare discount levels and selling prices to evaluate pricing consistency. Use actual sales data before concluding whether a discount increases demand.

### 4. Strengthen Inventory Planning
Combine current stock information with sales history, lead times, and reorder levels to develop more reliable replenishment decisions.

### 5. Track Performance Over Time
Collect regular inventory snapshots and transaction-level sales data to monitor stockout trends, product movement, and the impact of business decisions.

## 🧮 Example DAX Measures

### Total Products

```dax
Total Products =
DISTINCTCOUNT('zepto_cleaned'[name])
```

### Total Product Records

```dax
Total Records =
COUNTROWS('zepto_cleaned')
```

### Out-of-Stock Rate

```dax
OOS Rate =
DIVIDE(
    CALCULATE(
        COUNTROWS('zepto_cleaned'),
        'zepto_cleaned'[outOfStock] = TRUE()
    ),
    COUNTROWS('zepto_cleaned'),
    0
)
```

Format `OOS Rate` as a percentage in Power BI. This measure calculates the share of records marked out of stock, not necessarily the percentage of distinct products out of stock.

### Average Discount

```dax
Average Discount =
AVERAGE('zepto_cleaned'[discountPercent])
```

If discount values are stored as numbers such as 10, 20, and 30, display the result with a `%` label without applying percentage formatting that multiplies the values by 100.

## 📁 Suggested GitHub Repository Structure

```text
zepto-data-analysis/
│
├── README.md
├── data/
│   └── zepto_cleaned.csv
├── dashboard/
│   └── zepto_dashboard.pbix
├── reports/
│   └── dashboard_screenshots/
└── docs/
    └── data_dictionary.md
```

Include only files that actually exist in your repository. If your dashboard is currently an Excel workbook, place it in the repository and update the structure accordingly. Avoid uploading confidential data or files you do not have permission to share.

## 🚀 How to Use This Project

1. Clone or download this repository.
2. Open the cleaned dataset in Excel or Power BI.
3. Check the data types and column definitions.
4. Load the dataset into Power BI.
5. Create the required DAX measures.
6. Build visuals for KPIs, stock availability, categories, and discounts.
7. Use the findings to develop practical inventory and pricing recommendations.

## 📌 Project Limitations

- The dataset is a snapshot and does not establish changes over time.
- The `quantity` column must be validated before using it to calculate units sold or revenue.
- Profitability cannot be determined without cost data.
- Lost sales and customer demand cannot be measured reliably without transaction-level data.
- Inventory value estimates require verification that product quantities are not duplicated across records.

## 🔮 Future Enhancements

- Integrate transaction-level sales data.
- Add time-series analysis of inventory and stockouts.
- Develop demand forecasting using historical sales.
- Introduce automated low-stock alerts.
- Build category-level replenishment recommendations.
- Track dashboard KPIs over time.

## 👨‍💻 Author

**Your Name**

Data Analytics | Power BI | Excel | DAX

Connect with me on [LinkedIn](YOUR_LINKEDIN_URL) or explore my other projects on [GitHub](YOUR_GITHUB_PROFILE_URL).

---

⭐ If you find this project useful, feel free to star the repository!
