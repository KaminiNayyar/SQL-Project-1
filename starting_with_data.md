Question 1: which country will generate more revenue with referrals?

SQL Queries:

 select  country, channel_grouping, sum(total_transaction_revenue) as ttr
 from all_sessions
 group by country, channel_grouping, total_transaction_revenue
 having channel_grouping = 'Referral'
 and total_transaction_revenue >0


Answer: 



Question 2: in order to see the total number of unique products ordered  and the total number of quantities ordered from the data?

SQL Queries:

SELECT
  COUNT(*) AS product_views,
  COUNT(product_quantity) AS orders,
  SUM(product_quantity) AS quantity_product_ordered,
  v2_product_name
FROM all_sessions
WHERE t_ype = 'PAGE'
GROUP BY v2_product_name
ORDER BY product_views DESC
LIMIT 15;

Answer:



Question 3: in order to see the uniques visitors compared to the ecommerceaction_type?

SQL Queries:

SELECT 
  COUNT(DISTINCT full_visitor_id) AS number_of_unique_visitors,
  eCommerceAction_type
FROM all_sessions
GROUP BY eCommerceaction_type
ORDER BY eCommerceaction_type;

Answer:



