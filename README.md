# Capstonedata2


# Sales Data Analysis Report

## Overview

This repository contains a comprehensive analysis of sales data to provide insights into overall sales performance, top products, regional trends, and monthly seasonality. The report outlines key insights, actionable steps, and strategic recommendations based on findings from the dataset.

### Dataset Contents
The dataset includes the following fields:
- **OrderID**: Unique identifier for each order
- **CustomerID**: Unique identifier for each customer
- **Product**: Product name or ID
- **Region**: Geographic region of the sale
- **Order Date**: Date of the order
- **Quantity**: Quantity of items sold
- **Unit Price**: Price per item

---

---

### *. Analysis Approach*

#### *Data Collection*
The dataset for the analysis was provided by the incubator Hub,an orgainization built to train and support women in technology.The data was provided in excel workbook format for easy accessibility.
#### *Data manipulation*
- *Data Cleaning*:
   .Removed duplicates entry in excel and checkedfor speling errors and blank cells to ensure data quality.
- *Data Transformation*
   .Ensured all data fields were assigned correctly with the date field formatted to date formats.
   . Created new columns:
     - Sales Price:By deriving the product of multiplying the quantity column  by the unit price column.
       
### *Tools Used*
- Microsoft Excel for data cleaning and analysis using pivot table.[Download Here](https://www.microsoft.com)
- SQL For querying of data.
- POWERBI for data visualization.

### *Dashboard And Tables Overview*

#### EXCEL TABLE

![pivot tabledata](https://github.com/user-attachments/assets/1a7bde05-9e90-4e41-a528-9fb6c2919669)

![pivot table salesdatas](https://github.com/user-attachments/assets/c2c4cba0-e04f-475a-9e8e-0cb3477f07bb)


![pivot tab sales](https://github.com/user-attachments/assets/f9db6a6a-7cbd-4c3d-91f6-2564c94184b2)


![pivotable sales](https://github.com/user-attachments/assets/74eeddad-09d4-4ba3-b23e-256070d3562d)


#### SQL TABLE
```sql
Create database CapstoneProjectdb

select * from [dbo].[Capstone sql]

.....Total Sales For Each Product......

SELECT Product, SUM(Sales_Price) AS TotalSales
FROM dbo.[Capstone sql]
GROUP BY Product

.......Number of Sales Transactions in Each Region...

SELECT Region, COUNT(OrderID) AS No_of_SalesTransactions
FROM dbo.[Capstone sql]
GROUP BY Region

......Highest Selling Product By totalsales Value...

SELECT Top (1) Product, SUM(Sales_Price) AS TotalSales
FROM dbo.[Capstone sql]
GROUP BY Product
ORDER BY TotalSales DESC

.....Total Revenue Per Product.......

SELECT Product, SUM(Sales_Price) AS Totalrevenue
FROM dbo.[Capstone sql]
GROUP BY Product

.....monthly sales totals for the current year......

SELECT Month(OrderDate) AS Month,
SUM(Sales_Price) AS Monthly_SalesTotal
FROM dbo.[capstone sql] WHERE YEAR(OrderDate) = 2024
GROUP BY Month(OrderDate)
ORDER BY month(orderDate)

......Top 5 customers by total purchase amount.....

SELECT Top (5) Customer_Id,
 SUM(Sales_Price) AS TotalPurchaseAmount FROM dbo.[Capstone sql]
GROUP BY Customer_Id
ORDER BY TotalPurchaseAmount DESC

...Percentage of total sales contributed by each region....

SELECT Region, SUM(sales_price) AS RegionTotalSales,
FORMAT(ROUND((SUM(Sales_price) / CAST((SELECT SUM(Sales_price) FROM dbo.[Capstone sql]) AS DECIMAL(10,2)) * 100), 1), '0.#') 
AS PercentageOfTotalSales
FROM dbo.[Capstone sql]
GROUP BY Region
ORDER BY PercentageOfTotalSales DESC

...Products with no sales in the last quarter....

SELECT Product FROM dbo.[Capstone sql]
GROUP BY Product
HAVING SUM(CASE 
WHEN OrderDate BETWEEN '2024-06-01' AND '2024-08-31' 
THEN 1 ELSE 0 END) = 0

```
#### POWER BI

![powerbi dashboard](https://github.com/user-attachments/assets/10f693d9-fcfb-4609-aebd-b651e7895679)


#### Report Section

### 1. Sales Overview
 
 ### Yearly Sales Performance

 ## Year  2023

- **Total Revenue**: 1105330
- **Total Quantity sold**: 38681
- **Total Unit Price**: 161170
- **Average Sales Price**: 186

## YEAR 2024

- **Total Revenue**:995760
- **Total Quantity sold**: 29780
- **Total Unit Price**: 129090
- **Average Sales Price**: 250

#### Insights
- Significant revenue was generated in year2023 compared to year 2024,  yearly variability indicates potential seasonality or other external factors affecting sales flow.

#### Actions
- **Increase Average Order Value**: Encourage upselling or bundling of products to increase the order size.
- **Address Sales Variability**: Investigate the low-revenue  for potential gaps in marketing, promotions, or supply issues.

#### Recommendations
- **Cross-Selling and Upselling**: Implement checkout recommendations to boost order sizes.
- **Seasonal Campaigns**: Plan promotions to counterbalance low-revenue months.

---

### 2. Top-Performing Products

## Revenue Generated Per Product
-- **SHOES**-336,000
--**HAT**:229,080
--**SHIRT**:198,400
--**GLOVES**:148,200
--**JACKET**:44,640
--**S0CKS**:39,440
- **Top Product by Revenue**: *SHOES* - 336,000

## Quantity sold Per Product
--**HAT**:15,929
--**SHOES**:14,402
--**SHIRT**:12,388
--**GLOVES**:12,369
--**SOCKS**:7,921
--**JACKET**:5452
- **Top Product by Quantity Sold**: *HAT* - 15,929units

#### Insights
- The Product 'SHOES'drove the highest revenue, while the Product 'HAT' was the most frequently purchased item, showing demand for both high-value and popular products.

#### Actions
- **Promote High-Revenue Products**: Increase marketing efforts around high-value items like Product A.
- **Bundle Volume Leaders**: Offer Product B as part of a bundle with other items to boost sales of additional products.

#### Recommendations
- **Product Bundling**: Bundle high-volume products with other items to increase cross-sales.
- **Targeted Advertising**: Focus advertisements around top-selling products to attract similar customers.

---

### 3. Regional Breakdown
TOTAL REVENUE BY REGION
EAST:485,925
NORTH:387,000
SOUTH:927,820
WEST:300,345

- **Highest Sales Region**: EAST - 485,925
- **Top Product in EAST**: *HAT* - 54780

#### Insights
- East region contributed the most revenue,but the top product that generated  the highest revenue overall was shoes with an amount of 336,000 this indicates Product preferences varied by region, particularly with Hat being a favorite in East.

#### Actions
- **Localized Campaigns**: Highlight region-specific popular products to better engage customers in each area.
- **Optimize Marketing Spend**: Allocate more resources to east regions for higher return on investment.

#### Recommendations
- **Region-Specific Promotions**: Customize promotions to align with regional preferences.
- **Expansion Opportunities**: Expand product offerings in high-order regions like Europe by exploring similar products to local favorites.

---

#### Recommendations
- **Seasonal Planning**: Adjust inventory and staffing to meet expected seasonal demand.
- **Off-Season Marketing Campaigns**: Use discounts and incentives during low-demand months to boost sales.

---

## Conclusions

This analysis highlights key areas for improving sales performance:
- **Sales Performance**: Stable revenue, though seasonal and regional trends indicate opportunities for growth.
- **Product Strategy**: Prioritize promoting both high-revenue and high-volume products through targeted marketing.
- **Regional Customization**: Tailor promotions by region to align with customer preferences and maximize engagement.
- **Seasonal Planning**: Prepare for seasonal trends by aligning inventory and staffing with anticipated demand spikes and dips.

Implementing these strategies will help enhance revenue, optimize product marketing, and adapt to customer preferences. This data-driven approach forms a solid foundation for future sales and marketing strategies.

---

