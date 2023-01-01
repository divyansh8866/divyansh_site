# Connect to database - JDBC


<!--more-->

# Connect to database - JDBC

This code assumes that you have a MySQL database running on localhost with a database named "database" and a table named "table". It also assumes that you have the MySQL JDBC driver in your classpath.

You can modify this code to use a different database and table, or to apply different mappings and execute different SQL commands.

```jsx
# Import necessary modules
from pyspark.sql import SparkSession
from pyspark.sql.functions import *

# Create a SparkSession
spark = SparkSession.builder \
    .appName("Insert into DB using JDBC") \
    .getOrCreate()

# Set JDBC connection properties
jdbc_url = "jdbc:mysql://localhost:3306/database"
jdbc_driver = "com.mysql.jdbc.Driver"
connection_properties = {
    "user": "user",
    "password": "password",
    "driver": jdbc_driver
}

# Read the data from a table in the database
df = spark.read \
    .jdbc(jdbc_url, "table", properties=connection_properties)

# Apply a mapping to the data
df = df.withColumn("new_column", lower(col("column")))

# Truncate the destination table
spark.read \
    .jdbc(jdbc_url, "TRUNCATE TABLE table", properties=connection_properties)

# Write the transformed data to the database
df.write \
    .jdbc(jdbc_url, "table", mode="overwrite", properties=connection_properties)

# Commit the data to the database
spark.read \
    .jdbc(jdbc_url, "COMMIT", properties=connection_properties)

# Stop the SparkSession
spark.stop()
```
