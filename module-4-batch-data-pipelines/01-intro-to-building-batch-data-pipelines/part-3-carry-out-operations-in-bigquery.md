# Operations Available for Each Quality Problem

- use Views to filter out rows that have quality issues

## Validity

- For example, we can remove quantities less than zero using a WHERE clause. After we do a GROUP BY, we can discard groups whose total number of records is less than 10 using the HAVING clause.
- Consider if we are trying to filter out both NULLS and BLANKS or only NULLs or only BLANKs. We can easily count non-null values using COUNTIF and use the IF statement to avoid using specific values in computations.

## Accuracy

- For example, if we have an order, we could compute the sub_total from the quantity_ordered and item_price and make sure the math is accurate.
- Similarly, we can check if a value that is being inserted belongs to a canonical list of acceptable values. We can do that with a SQL IN.

## Completeness

- Identify any missing values and either filter out, or replace them with something reasonable. If the missing value is NULL, SQL provides functions like NULLIF, COUNTIF, COALESCE, etc. to filter missing values out of calculations.
- We might be able to do a UNION from another source to account for missing months of data. The automatic process of detecting data drops and requesting data items to fill in the gaps is called “backfilling”.

## Consistency

- COUNT provides the number of rows in a table that contain a non-null value. COUNT DISTINCT provides the number of unique values. If they are different, then it means that you have duplicate values. Similarly, if you do a GROUP BY, and any group contains more than one row, then we know we have two or more occurences of that value.
- For example, we may be getting timestamps, some of which may include a timezone. Or we have strings that are padded. Use string functions to clean such data before passing it on

## Uniformity

- If we are storing some value in centimeters, and suddenly, we start getting the value in millimeters? Our data warehouse will end up with non-uniform data. Use SQL cast to avoid issues with data types changing within a table. Use the SQL FORMAT() function to clearly indicate units.
