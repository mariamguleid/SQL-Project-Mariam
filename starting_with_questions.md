Answer the following questions and provide the SQL queries used to find the answer.

    
**Question 1: Which cities and countries have the highest level of transaction revenues on the site?**


SQL Queries: 

```sql
SELECT city, country
FROM all_sessions
WHERE city IS NOT NULL AND country IS NOT NULL
GROUP BY city, country, transactionrevenue
ORDER BY transactionrevenue DESC
LIMIT 10
```


Answer:

CITY             COUNTRY
"Kharagpur"	     "India"
"Stanford"	     "United States"
"Mexico City"    "Mexico"
"Hayward"	     "United States"
"Poznan"	     "Poland"
"San Salvador"	 "El Salvador"
"Coventry"	     "United Kingdom"
"Rome"	         "Italy"
"Berkeley"	     "United States"
"San Francisco"	 "France"




**Question 2: What is the average number of products ordered from visitors in each city and country?**


SQL Queries: 
```SQL
SELECT DISTINCT city, country, SUM(counts)/COUNT(counts) avg
FROM
(SELECT city, country, count(productSKU) counts
FROM all_sessions
GROUP BY city, country
 ) counting
 GROUP BY city, country
 ORDER BY city
 LIMIT 10
```


Answer:


CITY          COUNTRY          AVG
"Adelaide"	  "Australia"	   1.00000000000000000000
"Ahmedabad"	  "India"	       12.0000000000000000
"Akron"	      "United States"  1.00000000000000000000
"Alexandria   "Egypt"	       1.00000000000000000000
"Amã"	      "Jordan"	       1.00000000000000000000
"Amsterdam"	  "Netherlands"	   11.0000000000000000
"Amsterdam"	  "United States"  1.00000000000000000000
"Ann Arbor"	  "United States"  50.0000000000000000
"Antalya"	  "Turkey"	       1.00000000000000000000
"Antwerp"	  "Belgium"	       2.0000000000000000





**Question 3: Is there any pattern in the types (product categories) of products ordered from visitors in each city and country?**


SQL Queries: 

```sql
SELECT country, v2productcategory
FROM all_sessions
GROUP BY v2productcategory, country
ORDER BY country
```

Answer:


COUNTRY     V2PRODUCTCATEGORY
"Albania"	"Home/Shop by Brand/YouTube/"
"Albania"	"Home/Apparel/Men's/"
"Albania"	"Home/Shop by Brand/Google/"
"Algeria"	"Home/Electronics/"
"Algeria"	"Home/Shop by Brand/YouTube/"
"Algeria"	"Home/Apparel/Kid's/"
"Argentina"	"Home/Office/Notebooks & Journals/"
"Argentina"	"Home/Shop by Brand/Google/"
"Argentina"	"Home/Bags/Backpacks/"
"Argentina"	"Home/Shop by Brand/Android/"







**Question 4: What is the top-selling product from each city/country? Can we find any pattern worthy of noting in the products sold?**


SQL Queries:




Answer:





**Question 5: Can we summarize the impact of revenue generated from each city/country?**

SQL Queries:



Answer:







