# Final-Project-Transforming-and-Analyzing-Data-with-SQL

## Project/Goals
In this project, I am loading data from a csv file into pgAdmin, cleaning the data, answering questions using queries, and coming up with my own questions.
My goal is to understand the data well, clean it, and be able to extract meaningful data from the dataset to answer the questions I have.

## Process
I imported data from csv files into the database tables I created.

Then, I looked at some questions I have about the dataset and cleaned the data based on the questions I had.

Lastly I answered the questions using queries.

## Results
After analyzing the data I was able to get meaningful information from it such as the country and city that spent the most time on a site which is San Jose, United States. 
The most expensive product (Nest® Learning Thermostat 3rd Gen-USA - Stainless Steel), the total amount of page views per year (2016 = 35018, 2017 = 33461), the countries and cities with the highest level of transaction revenues and so on (Kharagpur, India ...).

## Challenges 
I was not able to link some tables together because some of the tables (all_sessions, analytics) lacked any unique identifiers.
I also was not able to link 'all_sessions' table to 'products' table due to the 'productsku' column having values not existing in the 'sku' column in products. 
Therefore, 'all_sessions' table contains products that we don't even have listed in the 'products' table. The 'all_sessions' table should've had a primary key (visitid contained duplicates). A lot of the values in various columns were left 'null',
making it hard to get important information aswell as values '(not set)' and 'not available in demo dataset' were put to indicate the absence of a value. 
The table 'all_sessions' consisted of information unnecessary to be in the table, such as 'productprice' which should have been in the 'products' table.

Also, the 'productrevenue', 'transactionrevenue' and 'productquantity' times 'productprice' doesn't match which indicates we are dealing with inaccurate data.



## Future Goals
I would make sure the tables are all linked, ensure the data has good formatting, there are no unnecessary columns, any incorrect data be removed.