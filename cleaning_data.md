What issues will you address by cleaning the data?
1. Moving irrelevant data and inserting into appropriate table
2. Deleting irrenlevant data and null values
3. Altering the table and updating empty table values
4. Data type validation
5. Caste stetements to populate column based on criterion set
   
- Removing irrelveant data and empty Columns:




- CONVERTING TO THE APPROPRIATE DATA TYPES
ALTER TABLE analytics
ALTER COLUMN timeonsite TYPE interval USING timeonsite * interval '1 second';

ALTER TABLE analytics
ALTER COLUMN date TYPE DATE USING to_date("date"::text, 'YYYYMMDD');

ALTER TABLE alsessions
ALTER COLUMN "time" TYPE TIME USING (make_time("time" / 3600, ("time" % 3600) / 60, "time" % 60));


- Data type validation
UPDATE alsessions
SET v2productcategory = NULL
WHERE v2productcategory = '(not set)' or v2productcategory = 'not available in demo dataset';

UPDATE alsessions AS a
SET timeonsite = al.timeonsite
FROM analytics AS al
WHERE a.fullvisitorid = al."fullvisitorId";




Queries:
Below, provide the SQL queries you used to clean your data.

-Getting rid of irrelevant data and moving it to appropriate data table
ALTER TABLE allsessions DROP COLUMN transactionid
ALTER TABLE allsessions DROP COLUMN itemrevenue
ALTER TABLE allsessions DROP COLUMN searchkeyword
ALTER TABLE allsessions DROP COLUMN totaltransactionrevenue
ALTER TABLE allsessions DROP COLUMN transactions
ALTER TABLE allsessions DROP COLUMN productrevenue
ALTER TABLE allsessions DROP COLUMN productrefundamount
ALTER TABLE allsessions DROP COLUMN itemquantity
ALTER TABLE allsessions DROP COLUMN productquantity
ALTER TABLE allsessions DROP COLUMN transactionrevenue
ALTER TABLE allsessions DROP COLUMN sessionqualitydim


- Fixing "(not set)" in the city column. I cleaned it by identififying the countires and using a case statement to update the city based on the country

UPDATE alsessions
SET country = NULL
WHERE country = '(not set)' or country = 'not available in demo dataset';

DELETE FROM alsessions
WHERE city IS NULL or country is NULL;
