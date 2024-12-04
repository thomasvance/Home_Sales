Home Sales Data Analysis Project
This project focused on analyzing home sales data using Big Data tools and SparkSQL. Key processes and methodologies employed in this analysis are outlined below:</br>

1. Setting Up the Environment:</br>
The analysis began with importing essential packages, including findspark for initializing Spark and pyspark.sql for utilizing SparkSQL functionalities.</br>

2. Initializing SparkSession:</br>
A SparkSession was instantiated via SparkSession.builder.appName("SparkSQL").getOrCreate() to establish a connection with Spark and enable SQL-based operations.</br>

3. Data Ingestion:</br>
The home sales dataset was retrieved from an AWS S3 bucket and loaded into a DataFrame using its URL.</br>

4. Temporary View Creation:</br>
A temporary SQL view named my_table was created from the DataFrame using the createOrReplaceTempView() method. This allowed SQL queries to be run directly on the DataFrame.</br>

5. Data Analysis through Queries:</br>
Various SQL queries were executed to extract insights, such as:</br>

   * Determining the average price of four-bedroom houses sold in each year.</br>
   * Analyzing average prices of homes based on different features like the number of bedrooms, bathrooms, and square footage.</br>
6. Caching Data for Performance Optimization:</br>
To improve query performance, the temporary table home_sales_df was cached in memory using the spark.catalog.cacheTable() method.</br>

7. Runtime Analysis:</br>
Query runtimes were evaluated by comparing execution times of cached queries with those executed on Parquet data. The start time was recorded with time.time() before running each query, and runtime differences were calculated.</br>

8. Writing Data to Parquet Format:</br>
The formatted data was saved in Parquet format with partitioning based on the date_built column. This was achieved using the partitionBy().parquet() method.</br>

9. Reading Parquet Data:</br>
The Parquet-formatted data was subsequently read into a new DataFrame to facilitate further analysis.</br>

10. SQL Queries on Parquet Data:</br>
A new temporary view, parquet_table, was created for the Parquet DataFrame using the createOrReplaceTempView() method. Queries were performed to identify homes with an average price of $350,000 or more, and their runtime was compared to cached query performance.</br>

11. Memory Management:</br>
After completing the analysis, the cached temporary table home_sales was uncached using the spark.catalog.uncacheTable() method to free up memory resources.</br>

12. Cache Status Validation:</br>
The caching status of the home_sales table was verified using spark.catalog.isCached() to confirm its uncached state.</br>

Key Takeaways:</br>
This project showcased the integration of SparkSQL for big data analytics, demonstrating effective workflows for data ingestion, querying, caching, performance benchmarking, and memory management. It provided valuable insights into home sales trends and optimized analysis through caching and Parquet data storage.</br>
