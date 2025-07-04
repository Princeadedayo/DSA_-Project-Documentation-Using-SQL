# DSA_-Project-Documentation-Using-SQL
## Kultra Mega Stores InventoryCase
# Table Of Content 
1. Introduction
2. Data Understanding and Preparation
3. Exploratory Data Analysis
4. SQL Analysis and Query Development and Visualizations and Findings
5. Business Insights and Recommendations
6. Conclusion
7. Tools used, [click here to download ](https://www.microsoft.com/en-us/sql-server/sql-server-downloads)

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

# SQL Analysis and Query Development
### In this section, we develop SQL queries to address the following key business questions:
## Case Scenario I
1. Which product category had the highest sales?
2. What are the Top 3 and Bottom 3 regions in terms of sales?
3. What were the total sales of appliances in Ontario?
4. Advise the management of KMS on what to do to increase the revenue from the bottom 10 customers
5. KMS incurred the most shipping cost using which shipping method?
## Case Scenario II
6. Who are the most valuable customers, and what products or services do they typically
purchase?
7. Which small business customer had the highest sales?
8. Which Corporate Customer placed the most number of orders in 2009 – 2012?
9. Which consumer customer was the most profitable one?
10. Which customer returned items, and what segment do they belong to?
11. If the delivery truck is the most economical but the slowest shipping method and
Express Air is the fastest but the most expensive one, do you think the company
appropriately spent shipping costs based on the Order Priority? Explain your answer

## Which product category had the highest sales?

To assess product category performance, we utilize a query that consolidates the total
sales and units sold per category. SQL query is as follows
SELECT Top 1
    Product_Category,
    SUM([Sales]) AS Total_Sales
FROM
    [KMS Sql Case Study]
GROUP BY
    Product_Category
ORDER BY
    Total_Sales DESC
    
### Visualization

![1](https://github.com/user-attachments/assets/624676a3-68b9-4c7f-a94e-277ac212f203)  

## Top 3

## What are the Top 3 and Bottom 3 regions in terms of sales?
SELECT top 3
    Region,
    SUM([Sales]) AS Total_Sales
FROM
    [KMS Sql Case Study]
GROUP BY
    Region
ORDER BY
    Total_Sales DESC
    
   ### Visualization 

 ![image](https://github.com/user-attachments/assets/83887a1a-f940-4378-b896-d86b197152e4)

## Bottom 3
SELECT top 3
    Region,
    SUM(Sales) AS Total_Sales
FROM
    [KMS Sql Case Study]
GROUP BY
    Region
ORDER BY
    Total_Sales ASC
    visulization
    ![image](https://github.com/user-attachments/assets/0051c6fc-8e0a-42d3-acb9-892f24a23298)
    
## What were the total sales of appliances in Ontario?
SELECT 
    SUM([Sales]) AS Total_Sales_Appliances_Ontario
FROM 
   [KMS Sql Case Study]
WHERE 
    Product_Category = 'Appliances'
    AND [Province] = 'Ontario';
     
### Advise the management of KMS on what to do to increase the revenue from the bottom 10 customers

SELECT TOP 10
    Customer_name,
    SUM(Sales)AS Total_sales
FROM
    [KMS Sql Case Study]
GROUP BY
    Customer_Name
ORDER BY
    Total_sales ASC;
   
   ## Visualization

   ![image](https://github.com/user-attachments/assets/a01e35a6-a300-42a9-ad8a-e8b30c60b3b1)

## KMS incurred the most shipping cost using which shipping method?

SELECT TOP 1
    Ship_Mode Mode,
    SUM([Shipping_Cost]) AS TotalShippingCost
FROM
    [KMS Sql Case Study]
GROUP BY
    [Ship_Mode]
ORDER BY
    TotalShippingCost DESC;
   
   ## Visualization

![image](https://github.com/user-attachments/assets/d68c9c54-3677-4e30-a285-f54aa57a3c57)

    
  # Case Scenario II

  ## Who are the most valuable customers, and what products or services do they typically
purchase?
## Step 1...... Top 3 Most valuable customer

SELECT top 3
    customer_Name,
    SUM([Sales]) AS Total_Sales,
    SUM([Profit]) AS Total_Profit
FROM
    [KMS Sql Case Study]
GROUP BY
    Customer_Name
ORDER BY
    Total_Sales DESC
    
  ## Visualization

  ![image](https://github.com/user-attachments/assets/a9e74786-da61-4bdf-a2cc-c5b76c60fde1)

  ## Step 2..... Product they purchased 
  
  SELECT product_category,SUM(sales) AS total_sales                
FROM [KMS Sql Case Study]

GROUP BY product_category 
ORDER BY total_sales DESC;

## Visualization

  ![image](https://github.com/user-attachments/assets/1fdacadd-da6d-479f-98ba-64880a8d88e5)

  ##  Which small business customer had the highest sales?
  
  SELECT top 1
    Customer_Name, 
    SUM(Sales) AS Total_Sales
FROM [KMS Sql Case Study]
WHERE Customer_Segment = 'Small Business'
GROUP BY [Customer_Name]
ORDER BY Total_Sales DESC

## Visualization

![image](https://github.com/user-attachments/assets/25217526-3277-4dfb-8f0d-0e2449806b7f)

 ## Which Corporate Customer placed the most number of orders in 2009 – 2012?
 SELECT top 1
    "Customer_Name",
    COUNT(DISTINCT "Order_ID") AS NumberOfOrders
FROM
   [KMS Sql Case Study]
WHERE
    "Customer_Segment" = 'Corporate'
    AND "Order_Date" BETWEEN '2009-01-01' AND '2012-12-31'
GROUP BY
    "Customer_Name"
ORDER BY
    NumberOfOrders DESC

## Visualization

![image](https://github.com/user-attachments/assets/273518e0-1930-41e3-ba72-2fa208b1ae13)

##  Which consumer customer was the most profitable one?

SELECT top 1
    "Customer_Name",
    SUM(Profit) AS TotalProfit
FROM
    [KMS Sql Case Study]
WHERE
    "Customer_Segment" = 'Consumer'
GROUP BY
    "Customer_Name"
ORDER BY
    TotalProfit DESC

## Visualization

![image](https://github.com/user-attachments/assets/9d2690e1-e1d1-4704-862b-8bb6701e5481)

## Which customer returned items, and what segment do they belong to?
SELECT DISTINCT 
    [Customer_Name], 
    'Segment'
FROM [dbo].[KMS Sql Case Study]
WHERE Sales < 0; 

select*from Order_Status

## Visualization

![image](https://github.com/user-attachments/assets/23afc067-a85b-4ae0-9323-3b6c6399953e)

## If the delivery truck is the most economical but the slowest shipping method and
Express Air is the fastest but the most expensive one, do you think the company
appropriately spent shipping costs based on the Order Priority? Explain your answer

SELECT order_priority, Ship_Mode, COUNT(*) AS order_count, AVG(shipping_cost) AS avg_shipping_c
FROM [KMS Sql Case Study] 
GROUP BY order_priority, ship_mode;

## Visualiztion 

![image](https://github.com/user-attachments/assets/5cbc98d6-1be4-4abf-a292-b09cc01cf722)

# Business Insights and Recommendations

## Based on the SQL analysis and visualizations, several key insights have emerged that can
help drive strategic improvements for Kultra Mega Stores, particularly for the Abuja division.

# Key Insights

## Product Category Dynamics:Shipping Costs Efciency:
– Technology, while showing the highest sales revenue, has a lower order volume,
suggesting higher per-unit pricing. In contrast, ofce supplies drive volume with slightly
lower margins.
## Recommendation:
 Adapt inventory management and promotional strategies tailored
to each category. For furniture, focus on high-value customer segments and post-sale
services, while for ofce supplies, implement bulk discount strategies to capture higher
volume purchases.

## Regional Sales Performance:
– West dominates the overall sales gures; however, Perie, with its signicant sales
contributions, shows potential for growth through targeted market initiatives.
## Recommendation:
Invest in localized marketing campaigns in perie, consider
regional pricing adjustments, and enhance customer service support in the area to
foster higher sales volumes.

## Shipping Costs Efciency:

– Shipping cost percentages are under control for both retail and wholesale segments.
However, continuous monitoring is crucial to ensuring that logistic expenses do not
erode prot margins as the business scales.

## Recommendation:
Negotiate better rates with logistics partners, explore in-house
delivery options for high-volume regions, and consider optimizing the packaging
process to reduce shipping costs further.

## Customer Protability:
– The protability analysis indicates that wholesale customers yield higher overall prot
margins compared to retail customers. Targeting and nurturing these relationships can
lead to sustained long-term protability.
## Recommendation:
Develop customer loyalty programs for wholesale clients, offer
customized pricing models, and invest in after-sales service enhancements to
reinforce protable customer relationships.

# Conclusion
This report has provided a detailed BI and SQL analysis of Kultra Mega Stores' inventory and
order data spanning 2009 to 2012. Through a structured approach that included data
understanding, rigorous SQL query development, and comprehensive visualizations, key
insights were generated regarding product category performance, regional sales dynamics,
shipping cost efciency, and customer protability.







 
	

  


   
    

    


    

    



  



