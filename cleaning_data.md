What issues will you address by cleaning the data?
- Removing irrelveant data and empty Columns:
    First I need to make sure that the entire column has null values and I did so by using "WHERE' statement to check if there was a value that was not null in the column.
- Deleted Transactionid Column: After comparing the transactionID colunm I found only 6 columns without Null values it was therefore better to delete the entire column than rows with null values for transactionId
- Deleted totaltransactionrevenue: Had missing values for majority of the column
- Deleted transaction: Had missing values for majority of the column 
- Deleted ItemRevenue: ALL values were null and it had no significance to the table
- Deleted searchKeyword: ALL values in the column were null and it had no significance to the table
- Deleted productrevenue: Only had 4 values in the column
- SessionQualityDim: Had values for majority of the rows, so I deleted rows with no value in them
- Deleted itemquantity: ALL values were null and it had no significance to the table

CONVERTING TO THE APPROPRIATE DATA TYPES



Queries:
Below, provide the SQL queries you used to clean your data.
ALTER TABLE all_sessions DROP COLUMN "transactionId"

ALTER TABLE allsessions DROP COLUMN transactionid
ALTER TABLE allsessions DROP COLUMN itemrevenue
ALTER TABLE allsessions DROP COLUMN searchkeyword
ALTER TABLE allsessions DROP COLUMN totaltransactionrevenue
ALTER TABLE allsessions DROP COLUMN transactions
ALTER TABLE allsessions DROP COLUMN productrevenue
ALTER TABLE allsessions DROP COLUMN itemquantity



ALTER SESSIONQUALITYDIM
