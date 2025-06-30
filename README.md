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
# Data Understanding and Preparation
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

#Data Cleaning and Transformation
Prior to analysis, the following data preparation steps are assumed:

1. Handling Missing Values: In most real-world datasets, missing or erroneous entries are
common. Techniques such as imputation for missing shipping cost values or removal of
records with critical missing elds are applied.

2. Data Type Conversion: Date elds (e.g., order date) are converted to the appropriate
date format, and any currency or numeric elds are standardized.

3. Normalization: The data has been normalized to avoid redundancy. For example, product
categories are stored in a separate lookup table and linked via foreign keys.

4. Aggregation Calculations: New elds such as “prot” for each order line (computed as
unit price minus cost price, multiplied by quantity) are calculated to support protability
analyses.

By standardizing the structure and cleaning the dataset, the subsequent SQL queries can
run efciently, and the output can be relied upon for further business insights.
