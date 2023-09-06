What are your risk areas? Identify and describe them.

Tables were missing unique identifiers and therefore was unable to link some tables.
When importing data, I had to ensure the rows in my table matched the columns in the csv file.
Different formatting made it hard to filter the data with queries so that needed to be addressed.




QA Process:

Checking if a column has duplicates:  

```sql
SELECT fullvisitorid
FROM all_sessions
GROUP BY fullvisitorid
HAVING COUNT(fullvisitorid) > 1;
```

Changing format for better results:

```sql
For the city column:
UPDATE all_sessions set city = NULL where city = (not set);
UPDATE all_sessions set city = NULL where city = not available in demo dataset;
```
For the country column:

```sql
UPDATE all_sessions set country = NULL where country = (not set);
UPDATE all_sessions set country = NULL where country = not available in demo dataset;
```






