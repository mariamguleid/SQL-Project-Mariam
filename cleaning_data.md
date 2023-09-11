Changed columns with string values 'not available in demo dataset' and '(not set)' to null instead

Removed products from sales_by_sku where total_ordered was 0 because the products should have been ordered atleast once.

Made productsku column in sales_by_sku a foreign key to link sales_by_sku and product tables. 

Dropped columns that had no values

Checked if columns made sense and had values in them.

Queries:


```sql
UPDATE all_sessions SET city = NULL WHERE city = 'not available in demo dataset'
UPDATE all_sessions SET city = NULL WHERE city = '(not set)'
UPDATE all_sessions SET country = NULL WHERE country = '(not set)'
UPDATE all_sessions SET productvariant = NULL WHERE productvariant = '(not set)'
```


```SQL
DELETE FROM sales_by_sku
WHERE total_ordered = 0
```


```SQL
ALTER TABLE sales_by_sku
ADD FOREIGN KEY (productSKU) REFERENCES products(SKU)
```


```sql
ALTER TABLE all_sessions
DROP COLUMN itemquantity
```


```sql
SELECT transactions FROM all_sessions
WHERE transactions IS NOT NULL
```


```sql
ALTER TABLE all_sessions
DROP COLUMN productrefundamount
```


```sql
ALTER TABLE all_sessions
DROP COLUMN itemrevenue
```


```sql
ALTER TABLE all_sessions
DROP COLUMN searchkeyword
```










