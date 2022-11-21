What are your risk areas? Identify and describe them.
Risk areas: 
1) Limited knowledge of the different platforms, leads to delays in getting the desired results.
2) time factor: at this early age of the course less time was a factor to complete this big project.


QA Process:
Describe your QA process and include the SQL queries used to execute it.
ans:
In my understanding the quality assurance process takes the highest priority. For exampe in a sales_by_sku table product sku is unique to one product but the product could repeat. So at first glance one can say there is 15k products ordered in a year but only after using certain statements like distinct one can make sure that the product is not getting repeated in our desired result.

Here is the Query for it:

select  distinct(productsku),
        sum(total_ordered) as sum_total_ordered 
		from sales_by_sku
group by productsku
having sum(total_ordered) != 0
order by sum(total_ordered)

