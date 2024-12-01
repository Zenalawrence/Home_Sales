# Home_Sales

## Overview

This project involved analyzing home sales data using SparkSQL, focusing on creating temporary views, partitioning data, and measuring query performance. The analysis provided insights into average home prices based on various criteria.

## Data Processing

1.  Importing and Reading the csv:
    -   Imported `pyspark` using `findspark`.
    -   Created a SparkSession to connect to Spark.
    -   Read the home sales data from the provided AWS S3 URL into a DataFrame.

2.  Created a temporary SQL view named home_sales for querying.

## Performed a few Queries

3.  **Query**: Calculated the average price of four-bedroom homes for each year.
    **Result**: The average price for four-bedroom homes sold from 2019 to 2022 was approximately $300,000.

    ![Query: Average price of 4 bdr.](https://github.com/Zenalawrence/Home_Sales/blob/main/Readme_IMAGES/4bdr%20query.png)

4.  **Query**: Averaged prices of homes having three bedrooms and three bathrooms, grouped by year built.
    **Result**: 2013 has the highest average of $295,962.27 for homes built. The lowest average price was $288,770.30 for homes built in 2015.

    ![Query: Average price of 3bdr 3 bath.](https://github.com/Zenalawrence/Home_Sales/blob/main/Readme_IMAGES/3bdr3b.png)

5.  **Query**: Kept the same conditions as step 4 but added requirements for two floors and a minimum of 2,000 square feet, grouped by year built.
    **Result**: The lowest average price was $276,553.81 for homes built in 2011, and the highest was $307,539.97 for homes built in 2012.

    ![Query: Average price of 3bdr 3 bath, 2000 sqft.](https://github.com/Zenalawrence/Home_Sales/blob/main/Readme_IMAGES/3bdr3bath2000sqft.png)

6.  **Query**: Analyzed average prices grouped by view ratings for homes priced at $350,000 or more.
    **Result**: Homes with more than 85 views averaged around $1,000,000.

    ![unchached data.](https://github.com/Zenalawrence/Home_Sales/blob/main/Readme_IMAGES/Uncached_data.png)   

## Performance Comparison
###  Cached vs Uncached vs Partitioned Query Runtime:

7.  The temporary table "home_sales_df" was cached using `spark.catalog.cacheTable()` method to improve query 6's performance.  The cached runtime was lower at around 0.106 seconds compared to the uncached run which was around 0.136 seconds

    ![chached data.](https://github.com/Zenalawrence/Home_Sales/blob/main/Readme_IMAGES/cached_data.png) 

10.  The formatted home sales data was partitioned based on the "date_built" using the `partitionBy().parquet()` method.  After writing the DataFrame to Parquet format, the runtime for queries on partitioned data was about 0.100 seconds.

![partitioned data results.](https://github.com/Zenalawrence/Home_Sales/blob/main/Readme_IMAGES/partitioned_data.png) 

## Conclusion
This project successfully demonstrated the use of SparkSQL for querying and analyzing home sales data. The system's performance was optimized using caching and partitioning techniques. 

