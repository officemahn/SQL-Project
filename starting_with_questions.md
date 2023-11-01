Answer the following questions and provide the SQL queries used to find the answer.

    
**Question 1: Which cities and countries have the highest level of transaction revenues on the site?**
SQL Queries:
SELECT
    a.country,
    a.city,
    SUM(s.productrevenue) AS total_revenue
FROM public.allsessions a
JOIN public.analytics an ON a.visitid = an.visitid
JOIN public.products p ON a.productsku = p.productsku
JOIN public.salesreport s ON p.productsku = s.productsku
GROUP BY a.country, a.city
ORDER BY total_revenue DESC;

Answer:
Seattle United State has the highest level of transaction revenue on the site


**Question 2: What is the average number of products ordered from visitors in each city and country?**
SQL Queries:
SELECT
    a.country,
    a.city,
    AVG(p.orderedquantity) AS avg_ordered_products
FROM public.allsessions a
JOIN public.analytics an ON a.visitid = an.visitid
JOIN public.products p ON a.productsku = p.productsku
GROUP BY a.country, a.city
ORDER BY avg_ordered_products DESC;

Answer:
Seattle has an average of 102 products ordered
Chicago has an average number of 94 products ordered




**Question 3: Is there any pattern in the types (product categories) of products ordered from visitors in each city and country?**
SQL Queries:
WITH ranked_categories AS (
    SELECT
        country,
        city,
        v2productcategory,
        COUNT(*) AS order_count,
        RANK() OVER (PARTITION BY country, city ORDER BY COUNT(*) DESC) AS r
    FROM allsessions
    GROUP BY country, city, v2productcategory
)
SELECT
    country,
    city,
    v2productcategory,
    order_count
FROM ranked_categories
WHERE r = 1;

Answer:
From what I have observed the following categories seems to have the highest sales;
- Shopping by brand "Home/Shop by Brand/YouTube/"
- T-Shirts Category "Home/Apparel/Men's/Men's-T-Shirts/"




**Question 4: What is the top-selling product from each city/country? Can we find any pattern worthy of noting in the products sold?**
WITH ranked_products AS (
    SELECT
        a.country,
        a.city,
        p.productsku,
        p.name,
        SUM(p.orderedquantity) AS total_ordered
    FROM allsessions a
    JOIN products p ON a.productsku = p.productsku
    GROUP BY a.country, a.city, p.productsku, p.name
)
SELECT
    country,
    city,
    productsku AS top_selling_product_sku,
    name AS top_selling_product_name,
    total_ordered
FROM (
    SELECT
        country,
        city,
        productsku,
        name,
        total_ordered,
        RANK() OVER (PARTITION BY country, city ORDER BY total_ordered DESC) AS r
    FROM ranked_products
) ranked
WHERE r = 1;

Answer:
Leatherette Notebook Combo seems to be a popular seller. 



**Question 5: Can we summarize the impact of revenue generated from each city/country?**
SQL Queries:
SELECT
    a.country,
    a.city,
    SUM(an.revenue) AS total_revenue
FROM allsessions a
JOIN analytics an ON a.visitid = an.visitid
GROUP BY a.country, a.city
ORDER BY total_revenue DESC;

Answer:
United states New york seems to have the highest total revenue. I joined tha analytics table and allsessions  to calculate the total revenue for each unique city and country combination. 






