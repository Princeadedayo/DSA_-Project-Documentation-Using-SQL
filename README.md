# DSA_-Project-Documentation-Using-SQL
## Kultra Mega Stores InventoryCase
# Table Of Content 
1. Introduction
2. Data Understanding and Preparation
3. Exploratory Data Analysis
4. SQL Analysis and Query Development
5. Visualizations and Findings
6. Business Insights and Recommendations
7. Conclusion

# Introduction
The purpose of this report is to demonstrate a comprehensive business intelligence (BI)
analysis of inventory and order data for Kultra Mega Stores (KMS), a leading supplier of
ofce supplies and furniture headquartered in Lagos, Nigeria. The analysis spans the period
from 2009 to 2012 and focuses on drawing actionable insights using SQL-based techniques.
Given that the customer base of KMS includes individual consumers as well as small
businesses (retail) and large corporate clients (wholesale), this report examines several
essential business questions such as product category performance, regional sales
variation, the impact of shipping costs on protability, and customer protability
segmentation. These insights are particularly intended to aid the decision-making process
for the Abuja division.

The analysis process is divided into several stages: understanding the data, cleaning and
preparing the dataset, performing exploratory data analysis (EDA), writing SQL queries to
extract key performance metrics, and nally, visualizing the results to inform business
recommendations. Although the actual dataset for KMS is assumed to be available in the
company’s relational database, this report illustrates the methodology using hypothetical
examples and sample SQL queries.
### Data Understanding and Preparation
Before any meaningful analysis can begin, it is essential to understand the underlying
dataset and how it is structured. For this case study, we assume that the inventory and
order data have been stored in a normalized relational database with the following key
tables:

1. Product: Contains details about each product including a unique product identier,
product name, category (e.g., ofce supplies, furniture), supplier information, retail price,
cost price, and available stock.

2. Orders: Holds records of each order placed, including order identier, customer
identier, order date, shipping cost, and total amount.

3. OrderDetails: Contains line items for each order with columns for product identier,
quantity ordered, unit price, and any discount applied.

4. Customers: Provides details on each customer with attributes such as customer
identier, customer segment (retail vs. wholesale), and regional information.

5. Regions: A table that details the geographical regions (e.g., Lagos, Abuja, Port Harcourt)
where KMS serves its customer base.

6. Shipping: Contains records related to shipping costs and logistical details that can affect
prot margins.

# Data Cleaning and Transformation Prior to analysis, the following data preparation steps are assumed:

### Handling Missing Values:
In most real-world datasets, missing or erroneous entries are
common. Techniques such as imputation for missing shipping cost values or removal of
records with critical missing elds are applied.

### Data Type Conversion:
Date elds (e.g., order date) are converted to the appropriate
date format, and any currency or numeric elds are standardized.

### Normalization:
The data has been normalized to avoid redundancy. For example, product
categories are stored in a separate lookup table and linked via foreign keys.

### Aggregation Calculations:
New elds such as “prot” for each order line (computed as
unit price minus cost price, multiplied by quantity) are calculated to support protability
analyses.

By standardizing the structure and cleaning the dataset, the subsequent SQL queries can
run efciently, and the output can be relied upon for further business insights.

# Exploratory Data Analysis

Exploratory Data Analysis (EDA) is a crucial step in comprehending trends, anomalies, and
patterns inherent in the data. This stage informs the development of precise SQL queries
and guides the construction of visualizations that reveal business driving factors.
# Key Areas of Focus in EDA

 ### Product Category Trends:
An initial investigation into total sales by product category over the 2009–2012 period is
performed. This helps identify if particular categories (e.g., ofce supplies versus
furniture) are driving overall revenue. A preliminary aggregation of sales numbers and
trends by month or quarter is carried out.

### Regional Sales Analysis:  
While KMS is headquartered in Lagos, the report pays special attention to regional
performance trends, particularly comparing the Lagos region with the Abuja division.
Variations in sales volume and revenue across different geographical areas provide
insights on market penetration and area-specic factors.

### Shipping Cost Impact:
Shipping costs can have a major inuence on the prot margins of a business. By
exploring the distribution of shipping costs against overall sales across different orders,
the analysis identies if shipping expenses are disproportionately affecting certain
customer segments or regions.

### Customer Protability:
Distinguishing between retail and wholesale customers, the analysis examines the
protability per customer segment. For instance, certain customer types may yield
higher margins despite lower volume orders, an insight that is critical for targeted
marketing and customer retention strategies.
