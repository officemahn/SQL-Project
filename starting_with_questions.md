Answer the following questions and provide the SQL queries used to find the answer.

    
**Question 1: Which cities and countries have the highest level of transaction revenues on the site?**


SQL Queries:



Answer:




**Question 2: What is the average number of products ordered from visitors in each city and country?**


SQL Queries:
SELECT
 	a.city,
    a.country,
    AVG(p."orderedQuantity") AS avg_ordered_quantity
FROM alsessions AS a
JOIN products AS p ON a.productsku = p."SKU"
GROUP BY a.city, a.country;


Answer:





**Question 3: Is there any pattern in the types (product categories) of products ordered from visitors in each city and country?**


SQL Queries:



Answer:





**Question 4: What is the top-selling product from each city/country? Can we find any pattern worthy of noting in the products sold?**


SQL Queries:



Answer:





**Question 5: Can we summarize the impact of revenue generated from each city/country?**

SQL Queries:



Answer:







