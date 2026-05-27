
# Havana Mall Performance & Customer Intelligence Analysis

## Project Overview

This project presents a comprehensive Havana Mall business analysis conducted using SQL and Microsoft Excel. The objective of the analysis was to transform raw transactional retail data into actionable business intelligence capable of supporting strategic decision-making.

Using the Superstore dataset, the project explored sales performance, customer behavior, product profitability, regional performance, and discount impact analysis. The workflow combined advanced SQL querying with interactive Excel dashboard development to simulate a real-world business intelligence and reporting environment.

The analysis was designed to answer critical business questions such as:

- Which regions and customers drive the highest revenue?
- Which product categories contribute most to profitability?
- Which products negatively affect business performance?
- How do discounts influence overall profit margins?
- What operational and strategic improvements can be recommended?

This project demonstrates practical data analytics, business intelligence, and dashboard reporting skills commonly used in retail analytics environments.

---

# Business Need / Problem Statement

Retail organizations generate large volumes of transactional and operational data daily. However, without structured analysis, businesses struggle to identify profitability drivers, operational inefficiencies, customer value patterns, and financial risks.

The company required a data-driven analysis capable of:
- Monitoring revenue and profitability performance
- Evaluating customer purchasing behavior
- Identifying high-performing and underperforming product categories
- Understanding regional sales and profit distribution
- Measuring the impact of discounts on profit margins
- Detecting products contributing to profitability leakage

Despite generating strong sales across multiple product categories and regions, the business faced profitability inconsistencies caused by aggressive discounting strategies and low-margin products.

This project was developed to provide actionable insights that could support:
- Pricing optimization
- Profitability improvement
- Product portfolio management
- Customer retention strategies
- Regional performance optimization
- Executive-level reporting and decision-making

---

# Tools & Technologies Used

- SQL
- Microsoft Excel
- Pivot Tables
- Pivot Charts
- KPI Reporting
- Business Intelligence Reporting
- Data Visualization

---

# Dataset Description

The dataset contains transactional retail sales data including:

- Order information
- Shipping details
- Customer information
- Product categories and sub-categories
- Geographic and regional data
- Sales performance metrics
- Discounts and profitability metrics

### Key Dataset Features
- 9,994 transaction records
- Multiple product categories
- Multiple customer segments
- Regional sales distribution
- Profit and discount analysis fields

Dataset Source:
Havana Mall Database

---

# Project Structure

```text
havana mall performance-customer-intelligence-analysis/
│
├── data/
│   └── sample_havanaa-mall.csv
│
├── sql/
│   ├── 01_data_cleaning.sql
│   ├── 02_sales_analysis.sql
│   ├── 03_customer_analysis.sql
│   ├── 04_product_analysis.sql
│   ├── 05_profitability_analysis.sql
│   └── 06_advanced_business_insights.sql
│
├── dashboard/
│   ├── havana-mall_dashboard.xlsx
│   └── dashboard_screenshot.png
│
├── reports/
│   └── business_insights_report.pdf
│
├── images/
│   └── dashboard_preview.png
│
└── README.md
```

---

# SQL Analysis Performed

The analysis was divided into multiple business intelligence modules:

- Monthly Sales Trend Analysis
- Customer Performance Analysis
- Product Profitability Analysis
- Regional Sales & Profit Evaluation
- Discount Impact Analysis
- Category-Level Performance Analysis
- Loss-Making Product Identification
- Profit Margin Evaluation

---

# SQL Queries

## 1. Monthly Sales Trend Analysis

```sql
SSELECT
    month,
    AVG(sales::numeric) AS avg_sales
FROM superstore_dataset
GROUP BY month
ORDER BY month;
```

### Purpose
This query evaluates monthly revenue trends and identifies seasonal sales patterns across the business.

### Key Finding
March recorded the highest average monthly sales, indicating a strong seasonal demand period and peak business performance during that timeframe.

---

## 2. Customer Performance Analysis

```sql
SELECT
    customer_name,
    ROUND(SUM(sales), 2) AS total_sales
FROM superstore
GROUP BY customer_name
ORDER BY total_sales DESC
LIMIT 10;
```

### Purpose
This analysis identifies the highest-value customers based on total revenue contribution.

### Key Finding
Mitch Willingham emerged as the highest-value customer, demonstrating significant contribution to total company revenue.

---

## 3. Regional Performance Analysis

```sql
SELECT
    region,
    ROUND(SUM(sales),2) AS sales,
    ROUND(SUM(profit),2) AS profit
FROM superstore
GROUP BY region
ORDER BY profit DESC;
```

### Purpose
This query evaluates the financial performance of each region based on total sales and profitability.

### Key Findings
- The West region generated the highest overall sales and profit across all regions.
- The East region maintained a strong and sustainable profit structure relative to its sales performance.
- Regional performance differences suggest varying operational efficiencies and customer purchasing behaviors across geographic markets.

---

## 4. Category Performance Analysis

```sql
SELECT
    category,
    ROUND(SUM(sales),2) AS total_sales,
    ROUND(SUM(profit),2) AS total_profit
FROM superstore
GROUP BY category
ORDER BY total_sales DESC;
```

### Purpose
This query evaluates category-level revenue generation and profitability contribution.

### Key Findings
- The Technology category generated the highest total sales and demonstrated strong profitability performance.
- The Furniture category generated substantial sales volume but produced significantly lower profit margins compared to other categories.
- The imbalance between sales and profitability within Furniture indicates potential pricing inefficiencies and high operational costs.

---

## 5. Profit Margin Analysis

```sql
SELECT
    ROUND((SUM(profit) / SUM(sales)) * 100, 2) AS profit_margin
FROM superstore;
```

### Purpose
This query measures the overall profitability efficiency of the business.

### Key Finding
The analysis showed that high revenue generation alone does not necessarily translate into strong profitability, emphasizing the importance of margin-focused business strategies.

---

## 6. Discount vs Profit Analysis

```sql
SELECT
    discount,
    ROUND(AVG(profit),2) AS avg_profit
FROM superstore
GROUP BY discount
ORDER BY discount;
```

### Purpose
This analysis evaluates how discount strategies impact profitability.

### Key Findings
- A strong negative relationship was observed between discount levels and profitability.
- As discount percentages increased, average profit consistently declined.
- Excessive discounting emerged as one of the primary contributors to margin erosion and product-level losses.

---

## 7. Loss-Making Products Analysis

```sql
SELECT
    product_name,
    ROUND(SUM(profit),2) AS total_profit
FROM superstore
GROUP BY product_name
HAVING total_profit < 0
ORDER BY total_profit;
```

### Purpose
This query identifies products generating negative cumulative profit.

### Key Findings
- 302 products generated cumulative losses, representing significant profitability leakage across the product portfolio.
- The majority of loss-making products were concentrated within the Furniture category.
- Persistent losses across multiple products suggest deeper pricing, discounting, or operational inefficiencies requiring strategic review.

---

# Key Business Insights

## Sales & Revenue Insights

The analysis revealed clear variations in sales performance across different periods and regions. March recorded the highest average monthly sales, suggesting the existence of seasonal demand patterns and periods of increased customer purchasing activity.

Regional analysis showed that the West region consistently outperformed all other regions in both sales and profitability. This indicates strong market demand, efficient operations, and favorable customer purchasing behavior within the region.

Although the East region generated lower total sales than the West, it maintained a more sustainable profit structure relative to revenue. This suggests stronger operational efficiency and better margin management compared to other regions.

---

## Customer Insights

Customer analysis identified Mitch Willingham as the highest-value customer based on cumulative sales contribution. This highlights the importance of customer concentration analysis and demonstrates how a relatively small number of customers can contribute significantly to total business revenue.

The findings reinforce the importance of customer retention strategies, loyalty programs, and targeted relationship management for high-value customers.

---

## Product & Profitability Insights

Category-level analysis showed that Technology generated the highest total sales and delivered strong profitability performance, making it the most valuable category from both a revenue and margin perspective.

In contrast, the Furniture category generated substantial sales volume but significantly underperformed in profitability. Despite strong revenue generation, profit margins remained weak due to operational inefficiencies, pricing structures, and discount dependency.

One of the most significant findings from the analysis was the identification of 302 products generating cumulative losses. Most of these products belonged to the Furniture category, indicating serious profitability leakage within that segment.

This suggests that high sales volume alone cannot be used as a measure of business success if profitability is not maintained.

---

## Discount & Margin Insights

The discount analysis revealed a strong inverse relationship between discounts and profitability. As discount levels increased, average profit consistently declined.

This indicates that aggressive discount strategies may be driving short-term sales growth at the expense of long-term profitability and financial sustainability.

The findings suggest that the business may be over-relying on discounts to stimulate sales, particularly within underperforming product categories.

---

# Business Recommendations

## 1. Reevaluate Discount Strategies

The company should review its discounting policies, particularly within the Furniture category. Excessive discounting is significantly reducing profit margins and contributing to cumulative product losses.

A more controlled pricing and promotional strategy should be implemented to balance revenue generation with profitability preservation.

---

## 2. Optimize Product Portfolio Management

Products generating consistent cumulative losses should be reviewed for:
- Repricing
- Bundling opportunities
- Supplier renegotiation
- Inventory optimization
- Potential discontinuation

Reducing exposure to unprofitable products can significantly improve overall business profitability.

---

## 3. Strengthen High-Value Customer Retention

Since Mitch Willingham and other top customers contribute significantly to revenue generation, the business should implement:
- Loyalty programs
- Personalized marketing campaigns
- Retention incentives
- Customer relationship management strategies

Protecting high-value customer relationships is critical for long-term revenue stability.

---

## 4. Expand High-Performing Regional Strategies

The West region demonstrated exceptional performance in both sales and profitability. Business practices, operational structures, and market strategies from this region should be analyzed and replicated across lower-performing regions where applicable.

---

## 5. Improve Operational Efficiency Within Furniture Category

Given the concentration of loss-making products within Furniture, the company should:
- Review shipping and operational costs
- Evaluate supplier pricing
- Reduce excessive discount dependency
- Improve pricing models
- Focus on higher-margin furniture products

This would help improve profitability within the category.

---

# Excel Dashboard Features

The interactive Excel dashboard was developed to provide executive-level business reporting and includes:

## KPI Cards
- Total Sales
- Total Profit
- Profit Margin
- Customer Count
- Orders Count

## Interactive Visualizations
- Monthly Sales Trend
- Profit by Region
- Sales by Category
- Top 10 Products by Sales
- Discount vs Profit Scatter Plot
- Customer Segment Analysis

## Interactive Filters
- Region
- Category
- Segment
- Order Year

---

# Dashboard Preview

```markdown
![Dashboard Preview](havana-mall-analysis/images/havana-mall-dashboard.png)
```

---

# Conclusion

This project demonstrates how SQL and Microsoft Excel can be integrated to transform raw retail transactional data into actionable business intelligence and executive-level reporting.

The analysis uncovered critical business insights related to:
- Revenue performance
- Regional profitability
- Customer value concentration
- Product profitability
- Discount impact on margins
- Operational inefficiencies

One of the most important findings from the project was that strong sales performance does not automatically translate into strong profitability. The analysis revealed that aggressive discounting strategies and low-margin product categories — particularly Furniture — contributed significantly to profitability leakage across the business.

The identification of 302 loss-making products further emphasized the importance of margin-focused decision-making rather than revenue-focused reporting alone.

Through structured SQL analysis and interactive dashboard development, this project successfully demonstrated practical business intelligence workflows used in real-world analytics environments.

The project highlights practical skills in:
- SQL querying
- Business analysis
- Data visualization
- Dashboard design
- KPI reporting
- Profitability analysis
- Executive-level business storytelling

---

# Author

Idowu Abajingin — Data Analyst

## Skills Demonstrated
- SQL
- Microsoft Excel
- Business Intelligence
- Data Visualization
- Dashboard Development
- KPI Reporting
- Data Storytelling
- Profitability Analysis
