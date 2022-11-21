Answer the following questions and provide the SQL queries used to find the answer.

    
**Question 1: Which cities and countries have the highest level of transaction revenues on the site?**


SQL Queries:  

select time_on_site, city, country, max(transaction_revenue) as max_transaction_revenue from all_sessions 
group by country, city, time_on_site
having max(transaction_revenue) != 0
and time_on_site != 0
order by max(transaction_revenue) desc


Answer:




**Question 2: What is the average number of products ordered from visitors in each city and country?**


SQL Queries:

select  sesh.visitid, sesh.productsku, sesh.city, sesh.country, round(avg(pro.ordered_quantity)) as avg_orders
from all_sessions sesh
inner join products pro
on sesh.productsku = pro.sku
group by productsku, city, country, ordered_quantity, visitid
having pro.ordered_quantity is not null 
order by pro.ordered_quantity desc

Answer:





**Question 3: Is there any pattern in the types (product categories) of products ordered from visitors in each city and country?**


SQL Queries:

select  sesh.visitid,
sesh.v2_product_name,
sesh.v2_product_category,
sesh.city,
sesh.country, pro.ordered_quantity
from all_sessions sesh
inner join products pro
on sesh.productsku = pro.sku

group by city, country, ordered_quantity, visitid, v2_product_name, v2_product_category

having pro.ordered_quantity is not null 
order by pro.ordered_quantity desc


Answer:





**Question 4: What is the top-selling product from each city/country? Can we find any pattern worthy of noting in the products sold?**


SQL Queries:

select sesh.country, ski.productsku, sesh.v2_product_name, max(ski.total_ordered)
from all_sessions sesh
join sales_by_sku ski
on ski.productsku = sesh.productsku
group by country, v2_product_name, ski.productsku, total_ordered
order by total_ordered desc




Answer:





**Question 5: Can we summarize the impact of revenue generated from each city/country?**

SQL Queries:

select distinct(sesh.country), 
round(sum(pro.ordered_quantity * sesh.product_price)/1000000,2) as total_revenue
from all_sessions sesh
join products pro
on sesh.Productsku = pro.sku
group by country
order by total_revenue desc




Answer:







