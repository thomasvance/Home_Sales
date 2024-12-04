### Home Sales Data Analysis Project

This project focused on analyzing home sales data using Big Data tools and SparkSQL. Key processes and methodologies employed in this analysis are outlined below:

1. **Setting Up the Environment**  
   * The analysis began with importing essential packages, including `findspark` for initializing Spark and `pyspark.sql` for utilizing SparkSQL functionalities.

2. **Initializing SparkSession**  
   * A `SparkSession` was instantiated via `SparkSession.builder.appName("SparkSQL").getOrCreate()` to establish a connection with Spark and enable SQL-based operations.

3. **Data Ingestion**  
   * The home sales dataset was retrieved from an AWS S3 bucket and loaded into a DataFrame using its URL.

4. **Temporary View Creation**  
   * A temporary SQL view named `my_table` was created from the DataFrame using the `createOrReplaceTempView()` method. This allowed SQL queries to be run directly on the DataFrame.

5. **Data Analysis through Queries**  
   * Various SQL queries were executed to extract insights, such as:
     1. Determining the average price of four-bedroom houses sold in each year.
     2. Analyzing average prices of homes based on different features like the number of bedrooms, bathrooms, and square footage.

6. **Caching Data for Performance Optimization**  
   * To improve query performance, the temporary table `home_sales_df` was cached in memory using the `spark.catalog.cacheTable()` method.

7. **Runtime Analysis**  
   * Query runtimes were evaluated by comparing execution times of cached queries with those executed on Parquet data. The start time was recorded with `time.time()` before running each query, and runtime differences were calculated.

8. **Writing Data to Parquet Format**  
   * The formatted data was saved in Parquet format with partitioning based on the `date_built` column. This was achieved using the `partitionBy().parquet()` method.

9. **Reading Parquet Data**  
   * The Parquet-formatted data was subsequently read into a new DataFrame to facilitate further analysis.

10. **SQL Queries on Parquet Data**  
    * A new temporary view, `parquet_table`, was created for the Parquet DataFrame using the `createOrReplaceTempView()` method. Queries were performed to identify homes with an average price of $350,000 or more, and their runtime was compared to cached query performance.

11. **Memory Management**  
    * After completing the analysis, the cached temporary table `home_sales` was uncached using the `spark.catalog.uncacheTable()` method to free up memory resources.

12. **Cache Status Validation**  
    * The caching status of the `home_sales` table was verified using `spark.catalog.isCached()` to confirm its uncached state.

### Key Takeaways  

This project showcased the integration of SparkSQL for big data analytics, demonstrating effective workflows for data ingestion, querying, caching, performance benchmarking, and memory management. It provided valuable insights into home sales trends and optimized analysis through caching and Parquet data storage.
