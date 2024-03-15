# BikeStores-Dataset-Analysis

### Table of Content 

- [Project Overview](#project-verview)
- [Data Source](#data-source)
- [Tools](#tools)
- [Key Insights](#key-insights)
- [Data manipulation](#data-manipulation)
- [Results](#results)
- [Recommendation](#recommendation)

### Project Overview

The BikeStores dataset used for this project comprises nine tables: Brands, Category, Customers, Order_Items, Orders, Products, Staffs, Stocks, and Stores.
Each table contains key fields relevant to its respective domain, such as product details, customer information, and sales order data.


![Screenshot (12)](https://github.com/DENNIS-SHANANA/BikeStores-Dataset-Analysis/assets/163293088/528a32ef-6ea4-40f8-a568-16b3cd8b6632)

### Data Source
Dataset Source: Kaggle [Download here](https://www.kaggle.com/BikeStores)

### Tools
- Excel -Data cleaning
- SQL server -Data querying and manipulation
- Tableau -Data nalysis and visualization

### Key Insights
- Revenue Trends Over Time
- Regional Revenue Variations
- Store Performance
- Product Category Analysis
- Customer Insights
- Sales representative performance

### Data manipulation
```sql
SELECT
ord.order_id,
CONCAT(cus.first_name,' ',cus.last_name) AS 'customers',
cus.city,
cus.state,
ord.order_date,
SUM(ite.quantity) AS 'total_units',
SUM(ite.quantity*ite.list_price) AS 'revenue',
pro.product_name,
cat.category_name,
sto.store_name,
CONCAT(sta.first_name,' ',sta.last_name)AS 'sales_rep'
FROM sales.orders ord
JOIN sales.customers cus
ON ord.customer_id=cus.customer_id
JOIN sales.order_items ite
ON ord.order_id=ite.order_id
JOIN production.products pro
ON ite.product_id=pro.product_id
JOIN production.categories cat
ON pro.category_id=cat.category_id
JOIN sales.stores sto
ON ord.store_id=sto.store_id
JOIN sales.staffs sta
ON sta.staff_id=ord.staff_id
GROUP BY
ord.order_id,
CONCAT(cus.first_name,' ',cus.last_name),
cus.city,
cus.state,
ord.order_date,
pro.product_name,
cat.category_name,
sto.store_name,
CONCAT(sta.first_name,' ',sta.last_name)
```

### Results
The finding afteranalysis and vizualization using Tableau is as follow [view here](https://public.tableau.com/app/profile/dennis.shanana/viz/BikeStoresDashboard2/Dashboard1?publish=yes) and the analysis results are summarized as follows;
1. The revenue was high during the year order 2017 followed by 2016 then 2018
2. The state New York was leading in revenue 
3. Baldwin Bikes store generates most revenue with 67.91% of the total revenue
4. Mountain bikes is the category that leads by generating the revenue with 35.335% children bicycles generating the least income
5. Pamelia Newman is the customer leading 
6. Marcelene Boyer is the sale representative that genarates the most revenue

### Recommendation
1. Focus on Historical Revenue Trends. Given the fluctuating revenue trend over the years, it's essential to analyze what factors contributed to the high revenue in 2016 and 2017 and why there was a decrease in 2018
2. Target New York Market. Since New York led in revenue, consider allocating more resources and marketing efforts towards this region. 
3. Leverage Baldwin Bikes Store. With Baldwin Bikes generating the majority of revenue, consider further investment in this store.
4. Promote Mountain Bikes Category. Given that Mountain Bikes generate the highest revenue, consider focusing marketing campaigns and product development efforts on this category
5. Engage with Pamelia Newman. Pamelia Newman, being the leading customer, presents an opportunity for personalized engagement and loyalty-building strategies
6. Learn from Marcelene Boyer's Success
7. Continuous Improvement and Adaptation

