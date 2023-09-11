   
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

```sql
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
```




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

```sql
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
```




**Question 3: Is there any pattern in the types (product categories) of products ordered from visitors in each city and country?**



SQL Queries: 

```sql
SELECT country, COUNT(country) as count_of_countries, v2productcategory
FROM all_sessions
group by country, v2productcategory
ORDER BY count_of_countries DESC
```

Answer: I counted the occurances of a country per productcategory. Below I only shared the first 10 results I got.

```sql
COUNTRY                COUNT_OF_COUNTRIES              V2PRODUCTCATEGORY
United States          926                             "Home/Apparel/Men's/Men's-T-Shirts/"
United States          808                             "Home/Shop by Brand/YouTube/"
United States          563                             "Home/Electronics/"
United States          554                             "Home/Apparel/"
United States          497                             "Home/Shop by Brand/Google/"
United States          401                             "Home/Office/"
United States          400                             "Home/Apparel/Men's/Men's-Outerwear/"
United States          387                             "Home/Nest/Nest-USA/"
United States          315                             "Home/Drinkware/"
United States          289                             "Home/Bags/"
```






**Question 4: What is the top-selling product from each city/country? Can we find any pattern worthy of noting in the products sold?**


SQL Queries: 
```sql
SELECT num_of_transactions, country, v2productname
FROM
(SELECT country, v2productname, count(transactions) AS num_of_transactions
FROM all_sessions
GROUP BY country, v2productname
ORDER BY num_of_transactions DESC) counting_transactions
WHERE num_of_transactions != 0
ORDER BY num_of_transactions DESC
```




Answer: I was able to find the top selling product per country. I only showed the top 10 answers from my result for simplicity.
```sql
num_of_transactions            country                v2productname
7                              United States          "Nest® Learning Thermostat 3rd Gen-USA - Stainless Steel"
5                              United States          "Nest® Cam Outdoor Security Camera - USA"
3                              United States          "Nest® Cam Indoor Security Camera - USA"
3                              United States          "Nest® Learning Thermostat 3rd Gen-USA"
2                              United States          "Nest® Learning Thermostat 3rd Gen-USA - White"
2                              United States          "Google Men's 100% Cotton Short Sleeve Hero Tee Navy"
2                              United States          "Reusable Shopping Bag"
2                              United States          "Google Sunglasses"
2                              United States          "Nest® Protect Smoke + CO White Wired Alarm-USA"
2                              United States          "Nest® Protect Smoke + CO White Battery Alarm-USA"
```





**Question 5: Can we summarize the impact of revenue generated from each city/country?**

SQL Queries:
```sql
SELECT country, SUM(transactionrevenue) AS total_transaction_revenue
FROM all_sessions
WHERE country IS NOT NULL
GROUP BY country
ORDER BY total_transaction_revenue
```

Answer: From the answer, I was able to see that United States generated the most revenue and the other 
countries generated no revenue.

Top 10 from the answer:
```sql
COUNTRY                     TOTAL_TRANSACTION_REVENUE
United States               2390950000
Bangaladesh                 [null]
Vanezuela                   [null]
Luxembourg                  [null]
Sweden					    [null]
Montenegro					[null]
Uganda						[null]
Jordan						[null]
Dominican Republic			[null]
Cambodia					[null]
```









