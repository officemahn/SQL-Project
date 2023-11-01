What are your risk areas? Identify and describe them.
While I was cleaning the data. My two big fears was   data loss and data inconsistency.

Data Loss: During the data cleaning process, one of my primary concerns was the risk of unintentionally deleting essential columns and rows. This risk could result in the loss of valuable information. 

Data Inconsistency: Another significant concern revolved around data inconsistency. To address this, I had to convert data types to ensure they were suitable for their intended use. However, altering data types could introduce errors and inconsistencies if not done correctly. 


QA Process:
Describe your QA process and include the SQL queries used to execute it.

- Data validation was a crucial step to confirm the completeness and accuracy of the cleaned data. I achieved this by comparing the cleaned data to reference tables that contained similar information or the previously used table to ensure values were not lost.
  SELECT COUNT(*) - COUNT(fullvisitorid) AS missing_values_count
  FROM allsessions;

- I checked for null values after the data transformation to ensure they were appropriately handled.
  SELECT COUNT(*) - COUNT(fullvisitorid) AS missing_values_count
  FROM allsessions;
  
- I conducted thorough testing by executing sample queries where I wrote the answers down and compared it to the results.
  SELECT DISTINCT city, country
  FROM alsessions
  WHERE COUNTRY is null;
  
- Additionally, I used COUNT queries to verify that the number of records in the cleaned data was consistent with expectations.
  
