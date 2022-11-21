What issues will you address by cleaning the data?
ans: steps taken to ensure the data looks as clean as possible:
1) Null values were converted into 0 ( for integer datatypes).
2) Empty columns were dropped using Alter table> drop column ()
3) Changed the time from epoch to time stamp to have a better idea.
4) (Taken from the hint) unitprice was divided by 1000000 and rounded to two decimal places.
5) eliminated duplicate values by using distinct statements.


Queries:
Below, provide the SQL queries you used to clean your data.

Query 1: select visit_number,
                visitid, to_timestamp(visit_start_time) as visit_start_time,
                d_ate, full_visitor_id, channel_grouping, 
                social_engagement_type,
                page_views, bounces, 
                cast(unit_price as float)/ 1000000 as unitprice
 <html>               from analytics
<body>
<img src= <"C:\Users\kamini\Pictures\Screenshots\Screenshot_20221120_105439.png"/>
</body>
</html>

Explanation: query1 represents the usage of above mentioned 3) and 4).

Query 2: update products
         set sentiment_magnitude = 0
         where sentiment_magnitude is null

Explanation: This query will solve replace the null values with 0 and also update long undesirable strings with short, easily readable ones.
             
                  ex: update all_sessions
                  set city = replace(city, 'not available in demo dataset' , 'not available')
