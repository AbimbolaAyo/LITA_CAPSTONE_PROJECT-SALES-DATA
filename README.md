# LITA_CAPSTONE_PROJECT-SALES-DATA
Referring to the Capstone Project Document, carry out the following exploratory process and tell a compelling story by building an interactive dashboard report to gather insight and make business decisions.

## OUTLINE

[ PROJECT OVERVIEW: ](project-overview)

[DATA DESCRIPTION:].(data-description)

[DASH BOARD REVIEW:].(dashboard-review)

[STATISTICS ABOUT THE DATASET:].(statistics about the dataset)

[METHODOLOGY:].(methodology)

[DATA ANALYSIS:].(data-analysis)

[DASHBOARD OVERVIEW WITH POWERBI:].(dashboard overview with powerbi)

[INSIGHTS GENERATION:].(insights generation)

[RECOMMENDATION:].(recommendation)

[CONCLUSION:].(conclusion)

## PROJECT OVERVIEW:

Making reference to the data and capstone project document shared earlier, by analyzing the sales performance of a retail store and carrying out the following exploratory process of the sales data to uncover key insights such as

- Top Selling Products
-  Regional Performances
-  Monthly Sales trends and By telling a compelling story and building an interactive dashboard Power BI report: To gather insight, Highlight findings And make business decisions.

## DATA DESCRIPTION:

This dataset includes the following Columns:

- Order Number
- Customer Id
- products
- region
- Order Date
- Quantity
- Unit Price

## DASH BOARD REVIEW:

- Customer Id
- products: Items sold in the store
- region: The other regional branches of the store ( North, South, East West)
- Order Date: The date the order was placed
- Quantity: The number of units of the product ordered in each transaction
- Unit Price: The acquisition cost per unit of the product

## STATISTICS ABOUT THE DATA:

- Number of Unique Customers: 50,000 
- Number of Products: 6
- Total Sales: 10,587,500
- Total Region: 4

## METHODOLOGY:

Data Collection

LITA_ The Incubator Hub provided the dataset for this analysis for learning and training purposes. The data was provided in an Excel sheet [download Here].(https://canvas.instructure.com/files/273182802/download?download_frd=1)
The Excel sheet made it accessible to analyze the Excel sheet The Excel sheet was further converted to CSV format for easy importing of files into:
- SQL to write various queries
- Power BI to create dashboards using various charts (PieChart and clustered Column Chart)

## DATA ANALYSIS: 

### Calculation in Excel
- Generating Total Sales (=F2*G2)
- ![Total Sales for Sales Data](https://github.com/user-attachments/assets/7e90ba29-a176-4cd1-8c8b-9d03c9361b0e)

- calculating average sales by product  =AVERAGEIF($C1:$C50001,$C2,$H1:$H50001)
- ![Project 4](https://github.com/user-attachments/assets/d20ff639-09ae-4d4d-a0aa-9525fa845a04)

- calculating total revenue by region  =SUMIF($D1:$D50001,$D12630,$H1:$H50001)
- ![Project 4](https://github.com/user-attachments/assets/7ceb8900-cb3f-409e-8c63-1b0f578998ef)

  ## Excel Chart
  
  ![project 2](https://github.com/user-attachments/assets/8838f738-42d1-488a-ab80-5b3d1cdf905f)
  ![Project 3](https://github.com/user-attachments/assets/cee8d208-0143-4d15-a4e0-195b3368c375)

  ## Pivot Table

  ![Project 1](https://github.com/user-attachments/assets/79365e24-f479-4f81-a0f5-b5682f081b48)

## Queries in SQL

``` SQL
  1. select product, sum (Quantity) as Quantity_Revenue from [dbo].[Sales data]
     Group by product
```
```
  2. select Region, count (customer_id) as sales_by_region from [dbo].[Sales data]
     Group by Region
```
```
  3. select product, sum (Total_sales) as product_total_sales from [dbo].[Sales data]
     Group by product
     order by product_total_sales desc
```
```
  4. select orderdate, sum (Total_sales) as Totalsales from [dbo].[Sales data]
     where orderdate >='2024-01-01'
     group by orderdate
```
```
  5. select customer_id, sum (Total_sales) as Totalsales from [dbo].[Sales data]
     group by customer_id
     order by Totalsales desc
```
```
  6. SELECT Region, SUM(Total_sales) AS RegionalSales, 
     (SUM(Total_sales) / CAST((SELECT SUM(Total_sales) FROM [dbo].[Sales data])
     AS DECIMAL(10, 2)) * 100) AS SalesPercentage
     FROM [dbo].[Sales data]
     GROUP BY Region
```
```
  7. SELECT DISTINCT  Product FROM [dbo].[Sales data]
     WHERE product Not In (select product from [dbo].[Sales data]
     Where OrderDate >= dateadd (quarter, -1, getdate ()) )
```
![Sql project 3](https://github.com/user-attachments/assets/76cc3fdd-50e5-4f4f-b42a-18f5e826f83b)
![Sql Project 2](https://github.com/user-attachments/assets/0cb67e3b-57f7-4984-a49c-9443b585c293)
![Sql project 1](https://github.com/user-attachments/assets/650e2889-d054-4043-a8ab-d5c14febe666)

## DASH BOARD OVERVIEW WITH POWER BI:

![Power BI Sales Data](https://github.com/user-attachments/assets/788c5fca-f08f-4ad5-bea1-8e8942c06c64)

## INSIGHTS GENERATION:

Insights on Total Sales (Revenue) In The Different Regions
- South Region: This region leads in Total sales and generates more revenue, with 4,675,000, which indicates potentially larger transaction values per sale.
- East Region: Close behind is the East region with total sales of 2,450,000 which is about 23.14% of the total Sales. This indicates a competitive market with strong transaction
- North Region: Shows great performance with 1,950,000 in sales and 18.42% of Total Sales (Revenue), showing consistent customer interest in the retail shop and the items stocked in it
- West Region: This region is equally good as it is actively competitive with the Northern market. Its close-range performance of 1,512,500 and 14.29% of the total revenue.

Indicates steady purchasing activity.
- Insights on the total revenue generated by each product
- Shoes: Leads in Total sales and generates more revenue with 3,087,500 which indicates a potentially higher priced item or a larger quantity of the item sold.
- Shirt: Close behind is shirt with total sales of 2,450,000 which is about 23.14% of the total Sales. This indicates a competitive market and is categorized as the second-best- 
  purchased product

## RECOMMENDATION:

- Region Comparison: Implement targeted marketing strategies, campaigns, or adverts to create more awareness in the North and West regions especially so as to curate more sales and generate more revenue

- Sales Optimization: Make the most effective use of the market trend by stocking more items with lead revenue-generating power which are (Shoes and Shirts)

## CONCLUSION:

The retail shops in the North and west region need more focus and attention on

- boosting revenue through marketing strategies
- studying market trends within the region to adequately decode the highest-selling product in the region, so as to stock more.
