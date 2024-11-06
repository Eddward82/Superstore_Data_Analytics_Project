# Superstore_Data_Analytics_Project

### Table of Contents
- [Project Overview](#project-overview)
- [Data Source](#data-source)
- [Tech Stack](#tech-stack)
- [Data Analysis](#data-analysis)
- [Key Findings](#key-findings)

###  Project Overview
---
The project aims to gain insights from the data by investigating the sales performance of the Superstore, their profitability performance, customer segmentation, and order trends. 
For sales performance, the project analyses the total sales by region, product category, and segment. For profitability analysis, the project identifies the most profitable products or regions. For customer segmentation, the project investigates the customers with the highest lifetime value. Lastly, for order trends, the project analyses sales trends over time (monthly)

###  Data Source:
---
The dataset used in this project is the Superstore Sales Dataset. It is a publicly available dataset. It was downloaded from Kaggle.com. The dataset is a retail dataset of a global superstore that span between 2015 to 2018. The dataset is a CSV format that includes several columns including Row ID, Order ID, Order Date, Ship Date, Ship Mode, Customer ID, Customer Name, Segment, Country, City, State, Postal Code, Region, Product ID, Category, Sub-Category, Product Name and Sales. 
###  Tech Stack: 
---
The tools used in the project include the following: 
- EXCEL for normalization;
- Power Query Editor for data cleaning and preparation;
- SQL Server to write queries and for analysis.
### Data Analysis
---
The following are some of the codes used in the analysis:

- Total Sales by Region
```
select 
	Region,
	Sum(Sales) AS TotalSales
from 
	OrdersDetails OD
	join Location L ON OD.Customer_ID = L.Customer_ID
group by
	Region;
```
- Total Sales by Category
```
select
	P.Category,
	sum(OD.Sales) AS TotalSales
from 
	OrdersDetails OD
	join Products P ON OD.Order_ID = P.Product_ID
group by
	P.Category;
```

- Total Sales by Product Name
```
select
	P.Product_Name,
	sum(OD.Sales) AS TotalSales
from 
	OrdersDetails OD
	join Products P ON OD.Order_ID = P.Product_ID
group by
	P.Product_Name
order by 
	TotalSales Desc;
```

- Total Sales By Region
```
select
	L.Region,
	sum(OD.Sales) AS TotalSales
from 
	OrdersDetails OD
	join Location L ON OD.Customer_ID = L.Customer_ID
group by
	L.Region
order by 
	TotalSales Desc;
```
- Customers with the Highest Lifetime Value

```
select
	C.Customer_ID,
	C.Customer_Name,
	sum(OD.Sales) AS LifetimeValue
from
	OrdersDetails OD
	join Customers C ON OD.Customer_ID = C.Customer_ID
group by 
	C.Customer_ID, C.Customer_Name
Order BY
	LifetimeValue DESC;
```
- Yearly and Monthly sales between 2015 to 2018
```
select 
	YEAR(O.Order_Date) AS Year,
	MONTH(O.Order_Date) As Month,
	Sum(OD.Sales) AS TotalSales
from 
	Order_2 O
Join
	Ordersdetails OD on O.Order_ID = OD.Order_ID

group by
	YEAR(O.Order_Date), 
	MONTH(O.Order_Date)
Order by 
	Year,
	Month;
```
###  Key Findings: 
---
The key findings from the analysis include the following:

- The Central region has the highest sales value, followed by East, West and South. This indicate a higher demand for products for the central region. Also the region has a larger customer base, and could mean that the region has more effective sales efforts.
-  Technology category has the highest sales followed by furniture and office supplies. This indicates technology products are in the highest demand due to its highest sales value. As a result of this, the technology category may warrant further investment in inventory, marketing, and product development.
-  The consumer segment has the total sales, followed by home office and corporate. Since the consumer segment drives the most sales, focusing marketing and promotions on individual consumers might yield the highest returns.
- Cubify CubeX 3D Printer Triple Head Print has the highest sales value followed by Samsung Galaxy Mega 6.3, Logitech G19 Programmable Gaming Keyboard, Canon Imageclass D680 Copier / Fax etc. The 3D printer's high sales suggest strong demand for premium, high-ticket items, which could indicate that the customer base values specialized or innovative technology products. Leveraging this trend, the company might expand its range of high-value tech products or accessories to capture similar demand.
- Nathan Mautz has the highest lifetime value, followed by Trudy Brown, Harold Pawlan, Ken Lonsdale etc. Since these customers have high lifetime values, focusing on retention strategies for them is crucial. Retention tactics like exclusive offers, loyalty programs, or personalized service could help keep these valuable customers engaged and loyal to the brand. Nathan Mautz and other high-lifetime-value (LTV) customers can provide insights into valuable customer segments. Understanding their demographics, purchasing behavior, and preferences allows the company to identify and target similar high-potential customers through tailored marketing strategies.
- Lastly, the analysis reveals that sales trends over time has taken an upward trajectory. This indicates positive performance and shows that factors such as growing demand, effective marketing strategies, and improved product offerings. 
