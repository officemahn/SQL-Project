Question 1: What is the average time visitors spend on the site in each channel group

SQL Queries:

SELECT
    channelgrouping,
    AVG(EXTRACT(epoch FROM timeonsite)) AS avg_time_on_site_seconds
FROM allsessions
GROUP BY channelgrouping
Answer: 

|"channelgrouping"	| "avg_time_on_site_seconds" |
|-------------------| ---------------------------|
|"Organic Search"	  | 169.1565483008781978       |
|"Display"	        | 196.4605263157894737       |
|"Referral"	        |189.8804585152838428        |
|"Paid Search"	    | 257.2245989304812834       |      
|"Affiliates"	      | 231.8380952380952381       |
|"Direct"	          | 177.5664280031821798       |
|"(Other)"	        |14.5000000000000000         |

Question 2: Who is the earliest and latest visitor based on their visit date

SQL Queries:

SELECT
    date AS latest_visit_date,
    fullvisitorid AS latest_visitor_id
FROM allsessions
ORDER BY date DESC
LIMIT 1;

SELECT
    date AS earliest_visit_date,
    fullvisitorid AS earliest_visitor_id
FROM allsessions
ORDER BY date
LIMIT 1;

Answer:

|"latest_visit_date" |	"latest_visitor_id"|
---------------------|---------------------|
|"2017-08-01"	       |7587649703008623514 |

|"earliest_visit_date" |	"earliest_visitor_id"|
---------------------|---------------------|
| "2016-08-01"       |4890176689513443468 |


Question 3: 

SQL Queries:
SELECT COUNT(DISTINCT fullVisitorID) AS total_unique_visitors
FROM allsessions;


Answer:
|"total_unique_visitors" |
|---------------------|
|5692|





