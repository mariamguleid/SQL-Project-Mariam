Question 1: Show the total amount in which different products were ordered. Include the name for the product.
and only show the top ten.

SQL Queries: 
```SQL
SELECT sbs.productSKU, p.name, sbs.total_ordered
FROM sales_by_sku sbs
JOIN products p ON sbs.productSKU = p.SKU
ORDER BY total_ordered DESC
LIMIT 10
```
Answer: 

PRODUCTSKU          NAME                                            TOTAL_ORDERED
"GGOEGOAQ012899"	"Ballpoint LED Light Pen"	                    456
"GGOEGDHC074099"	" 17oz Stainless Steel Sport Bottle"	        334
"GGOEGOCB017499"	"Leatherette Journal"	                        319
"GGOEGOCC077999"	" Spiral Journal with Pen"	                    290
"GGOEGFYQ016599"	"Foam Can and Bottle Cooler"	                253
"GGOEGOCB078299"	" Leather Journal-Black"	                    250
"GGOEGHPJ080310"	" Blackout Cap"	                                189
"GGOEADHH073999"	"Android 17oz Stainless Steel Sport Bottle"	    167
"GGOEGAAX0037"	    "Sunglasses"	                                146
"GGOENEBQ078999"	" Cam Outdoor Security Camera - USA"	        112



Question 2: What is the most expensive product? Include name, category, and the total page views for each.

SQL Queries:
```sql
SELECT productprice, v2productname, v2productcategory, pageviews
FROM all_sessions
ORDER BY productprice DESC
LIMIT 1
```

Answer:

PRODUCTPRICE    V2PRODUCTNAME                                               V2PRODUCTCATEGORY
298000000	    "Nest® Learning Thermostat 3rd Gen-USA - Stainless Steel"	"Nest-USA"

Question 3: List only the products that have a sentiment score and sentiment magnitude. 

SQL Queries: 
```sql
SELECT name, sentimentscore, sentimentmagnitude
FROM products
WHERE sentimentscore > 0
AND sentimentmagnitude > 0
```

Answer:

NAME                                            SENTIMENTSCORE     SENTIMENTMAGNITUDE
" Women's Colorblock Tee White"	                0.8	               2
" Men's Quilted Insulated Vest Black"	        0.8	               2
" Sunglasses"	                                0.5	               0.5
"Red Shine 15 oz Mug"	                        0.3	               0.5
"Recycled Paper Journal Set"	                0.3	               0.5
" Women's Scoop Neck Tee Black"	                0.3	               0.5
" Onesie Green"	                                0.3	               0.5
" Learning Thermostat 3rd Gen-USA - White"	    0.3	               0.5
"Android Stretch Fit Hat"	                    0.3	               0.5
" Men's Quilted Insulated Vest Battleship Grey"	0.3	               0.5


Question 4: Get the the amount of page views by year. 

SQL Queries: 
```sql
SELECT EXTRACT (year FROM date) AS year, SUM(pageviews) AS totalpageviews
FROM all_sessions
GROUP BY EXTRACT (year FROM date)
ORDER BY year
```

Answer:

```sql
YEAR    TOTALPAGEVIEWS
2016	35018
2017	33461
```


Question 5: Which country and city spent the most time on a site?

SQL Queries: 
```SQL
SELECT country, city, time
FROM all_sessions
ORDER BY time DESC
LIMIT 1
```

Answer: 

COUNTRY           CITY          TIME
"United States"	  "San Jose"	3192410