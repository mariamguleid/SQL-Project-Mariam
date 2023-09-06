What issues will you address by cleaning the data?

Changed city and country column string values 'not available in demo dataset' and '(not set)' to null instead

Removed products from sales_by_sku where total_ordered was 0 because the products should have been ordered atleast once.

Made productsku column in sales_by_sku a foreign key to link sales_by_sku and product tables. 



Queries:
Below, provide the SQL queries you used to clean your data.

```sql
UPDATE all_sessions set city = NULL where city = 'not available in demo dataset'
UPDATE all_sessions set city = NULL where city = '(not set)'
UPDATE all_sessions set country = NULL where country = '(not set)'
```


```SQL
DELETE FROM sales_by_sku
WHERE total_ordered = 0
```


```SQL
ALTER TABLE sales_by_sku
ADD FOREIGN KEY (productSKU) REFERENCES products(SKU)
```



