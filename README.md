# SALES-DATA
My documentation for my LITA sales Data capstone project

---

#PROJECT TITLE: SALES DATA ANALYSIS

---

## DATA COLLECTED
The data set includes the following key columns
- customer ID
- order date
- order ID
- Products
- Revenue
- quantity
- region
- unit price

---

## PROJECT OBJECTIVE
- To assess product performance
- To analyze Regional Sales Trends
- To understand Monthly Sales Variability
- To Identify High-Value Customers
- To evaluate Overall Sales Contribution by Region
- To identify Non-Performing Products

---

## TOOLS USED
This data was worked on using:
- Ms.Excel for data cleaning and data analysis, using the pivot tables to organize and summarize.
- SQL(structured Query Language) for data querying, to ensure the integrity and quality of data
- PowerBi for data visualization, to represent the key insights visually.

---

## DATA CLEANING AND PREPARATION
- Data loading and inspection
- Data cleaning
- Removal of duplicates

---

## EXPLORATORY DATA ANALYSIS
The EDA involved was focused on answering the follwowing questions:
- What is the total sales for each product category.
- What is the number of sales transactions in each region.
- What is the highest-selling product by total sales value.
- What is the total revenue per product.
- What is the monthly sales totals for the current year.
- who are the top 5 customers by total purchase amount.
- What is the percentage of total sales contributed by each region.
- what products with no sales in the last quarter.

---

## DATA ANALYSIS
This shows and includes the formulars, basic lines of codes used and DAX expressions used during the analysis.

#### SQL for data querying

```
PROJECT 1:SALES DATA SQL QUERIES
SELECT *
FROM[dbo].[Sales Data]
---Q1 Retrieve the total sales for each product category.---
SELECT Product,SUM(Quantity*UnitPrice) as Total_Sales
FROM [dbo].[Sales Data]
GROUP BY Product
---Q2 Find the number of sales transactions in each region.--
SELECT Region,SUM(Quantity*UnitPrice) as Total_Sales
FROM [dbo].[Sales Data]
GROUP BY Region
--- Q3 Find the highest-selling product by total sales value.
SELECT Product, SUM(Quantity*UnitPrice) as Total_Sales
FROM[dbo].[Sales Data]
GROUP BY Product
--- Q4 Calculate total revenue per product--
SELECT Product,Sum(Revenue) As Total_Revenue 
FROM[dbo].[Sales Data]
GROUP BY Product
--ALTER TABLE [dbo].[Sales Data]
--ADD OrderMonth nvarchar(50)
--UPDATE [dbo].[Sales Data]
--SET OrderMonth = DATENAME(MONTH, OrderDate)
--ALTER TABLE[dbo].[Sales Data]
--ADD OrderYear int
--UPDATE [dbo].[Sales Data]
--SET OrderYear = Year(OrderDate)
--- Revenue Column---
---ALTER TABLE[dbo].[Sales Data]
--ADD Revenue int
---UPDATE [dbo].[Sales Data]
---SET Revenue = (Quantity*UnitPrice)
SELECT *
FROM [dbo].[Sales Data]
--Q5 Calculate monthly sales totals for the current year(2024)--
SELECT OrderMonth,
SUM(Quantity*UnitPrice) as Total_Sales
FROM[dbo].[Sales Data]
WHERE OrderYear = 2024
GROUP BY OrderMonth
--- Q6 find the top 5 customers by total purchase amount
SELECT Top 5 Customer_Id,SUM(Quantity) AS Total_Purchase
FROM[dbo].[Sales Data]
GROUP BY Customer_Id
ORDER BY Total_Purchase DESC
---Q7 calculate the percentage of total sales contributed by each region.
SELECT Region, SUM(Revenue)/SUM(Quantity*UnitPrice)*0.1 AS Percebtage_of_Total_Sales
FROM [dbo].[Sales Data]
GROUP BY Region
ORDER BY Percebtage_of_Total_Sales
--Q8 Identify products with no sales in the last quarter
SELECT Product,SUM(Quantity) AS Sales
FROM [dbo].[Sales Data]
WHERE MONTH(OrderDate) BETWEEN 10 AND 12 -- Months 10, 11, and 12 (October to December)
GROUP BY Product
HAVING SUM(Quantity)=0
SELECT*
FROM[dbo].[Sales Data
```

---

## DATA VISUALIZATIONS





![Screenshot (23)](https://github.com/user-attachments/assets/54c777c1-77d2-4b44-816d-58b22f98594a)









![Screenshot (24)](https://github.com/user-attachments/assets/b50feba2-fbe5-4c0f-9afe-5a9202ab83dc)





---



## FINAL ANALYSIS OUTCOME

1. Problem Identification
2.Key Insights
3. Recommendations


#### 1. problem Identification
The organization has experienced inconsistent sales performance across regions, products, and months, with noticeable variations in product demand. This raises concerns regarding product-specific strategies, customer targeting, and regional sales optimization. Identifying patterns in sales data will enable the organisation to make data-driven decisions, optimize inventory, and improve overall revenue by focusing on high-performing products and region.

#### 2.key insights

**Monthly Sales Trends:**
Sales vary significantly by month, peaking in July and October (both at 50,000 units) and dipping in February and December (under 20,000 units). These fluctuations indicate potential seasonality and suggest that demand is not consistent year-round. Peaks in sales may be tied to seasonal events, promotions, or holidays, while the low periods could represent off-seasons.

**Top-Selling Products:**
Hats lead in total sales with 80,000 units sold, followed closely by Shoes (73,000), Gloves (63,000), and Shirts (53,000). Socks and Jackets have lower sales, suggesting these items may be less popular or face competition.

**Regional Sales Distribution:**
The South region stands out with 4.7 million in revenue, representing 35.5% of total revenue. In contrast, the West region is the least performing, generating only 2.0 million (about 18.7% of revenue). The South is a key market for LITA, and efforts should be made to understand and replicate its success in other regions.

**Revenue by Product:**
The highest revenue comes from Hats (3.1 million), with Shirts (2.5 million) and Gloves (1.6 million) also contributing significantly. Jackets and Socks contribute less, indicating potential underperformance or lower profit margins. Focusing on Hats and Shirts will likely yield higher returns. Efforts to increase the popularity of low-selling products could improve revenue diversification.

**Top Customers:**
The five top customers account for a total purchase amount of 4,468 units, with Cus1151 leading with 911 units. These customers represent valuable relationships and should be nurtured. These high-value customers are crucial for repeat business and long-term profitability.

**There were no products with no sales in the last quarter**

#### Reccomendations
- Seasonal Promotions and Inventory Adjustments:
To address monthly sales fluctuations, the organization should implement targeted promotions during low-demand months (e.g., February and December) to stimulate sales.The organization should Prepare for higher demand in peak months (July and October) by adjusting inventory levels and ensuring popular items like Hats and Shoes are well-stocked.

- Focus on High-Performing Regions:
The South region's success should be leveraged. The organization should Conduct a deeper analysis to identify specific factors driving sales in the South (e.g., demographic preferences, economic conditions). This insight can guide similar strategies in underperforming regions, particularly the West, to boost sales.

-Enhance Product-Specific Strategies:
With Hats and Shoes generating the highest sales, the organization should prioritize these products in advertising, promotions, and inventory management. Experiment with bundle offers involving low-performing products (e.g., Jackets with Gloves) to increase overall sales and appeal to a broader customer base.

-Customer Retention and Engagement:
The organization should develop a loyalty program for their top customers to encourage repeat purchases and increase brand loyalty. Offering exclusive discounts, early access to new collections, or rewards for high purchase volumes can strengthen relationships with key customers and increase their lifetime value.

- Data-Driven Decision-Making:
The organization should regularly review and analyze sales data to adapt strategies based on current trends. Monitoring KPIs, such as monthly sales growth, regional sales performance, and product-specific revenue, will allow LITA to make informed decisions promptly and remain agile in a competitive market.


## CONCLUSION
By addressing the identified patterns and implementing the above recommendations,the organization can enhance its sales strategy, optimize product offerings, and improve customer loyalty. The insights reveal clear areas for growth, particularly in expanding successful regional strategies, focusing on top-selling products, and maintaining relationships with high-value customers. With these adjustments,they can maximize their revenue potential and achieve sustained growth.









