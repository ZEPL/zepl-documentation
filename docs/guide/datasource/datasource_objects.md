# Data Source Objects and Libraries
This article will cover all of the data types that are returned by Zepl’s secure data source objects. In order to build a standard method for accessing any data source, Zepl has built data source connectors to support one or all of the four programming languages used by data scientists; Python, R, Scala, and SQL.

Zepl has created a simple, secure, and standard method for all users to access their data. Zepl’s data sources allow each user to securely store their user credentials through our encrypted keychain. 

Each programming language supports different access methods to each of these data sources. We will walk through what objects are returned upon connecting to each data source. This will give you the best insight to take advantage of our features and troubleshoot any errors that may arise.

* [Snowflake](#snowflake)
* [Amazon S3](#s3)
* [Google BigQuery](#google-bigquery)
* [MySQL](#mysql)
* [PostgreSQL](#postgresql)
* [Apache Cassandra](#cassandra)
* [SAP HANA](#sap-hana)
* [Alibaba MaxCompute](#alibaba-maxcompute)

----

# Snowflake

### Configure
* Account (required)
* Warehouse (optional - can be specified at the beginning of the session)
* Database (optional - can be specified in each query)
* Schema (optional - can be specified in each query)

>Note: If your Warehouse is not specified, the user will need to run the "USE WAREHOUSE <warehouse>" command in the language of their choice. I.e. if you are connecting through python, select warehouse in this way:


>
>`cur = z.getDatasource("<data source name>")` <br>
>`cur.execute("USE WAREHOUSE <warehouse>")`


### Read from Snowflake

[Open Examples in Zepl](https://app.zepl.com/viewer/notebooks/bm90ZTovL3pzaGFpbnNreUB6ZXBsLmNvbS81MDA5Y2QyNTY4NmI0MmE3ODBlMGU5MzhmYjRhOGViYy9ub3RlLmpzb24)

| Language | Code | Object Returned | Library |
|----------|------|-----------------|---------|
| Python   |`cur = z.getDatasource("<data source name>")` <br> <br>`conn = z.getDatasource("<data source name>_con")`  | <a href="https://docs.snowflake.com/en/user-guide/python-connector-api.html#object-cursor">Snowflake Cursor Object</a><br><br><a href="https://docs.snowflake.com/en/user-guide/python-connector-api.html#object-connection">Snowflake Connection Object</a> | Snowflake-connector-python - v2.0.3 |
| R / SparkR | `conn <- z.getDatasource("<data source name>")` | [DBIConnection object:](https://www.rdocumentation.org/packages/DBI/versions/0.5-1/topics/DBIConnection-class){:target="_blank"} Zepl function uses the `dbConnect()` function from the DPLYR library |  |
| Scala | ```val df = z.getDatasource("<data source name>").asInstanceOf[org.apache.spark.sql.DataFrameReader]``` | Spark SQL Dataframe: [org.apache.spark.sql.DataFrameReader](https://spark.apache.org/docs/2.3.1/api/java/org/apache/spark/sql/DataFrameReader.html){:target="_blank"} |
| SQL | `%datasource.<data source name>` | JDBC connection to Snowflake | |

> Note: Spark (Scala and Pyspark) require 'STAGE' permissions on the Snowflake database or else this exception may be thrown: `net.snowflake.client.jdbc.SnowflakeSQLException: SQL execution error: Creating stage on shared database 'SNOWFLAKE_SAMPLE_DATA' is not allowed`

### Write data to Snowflake
[Open Examples in Zepl](https://app.zepl.com/viewer/notebooks/bm90ZTovL3pzaGFpbnNreUB6ZXBsLmNvbS83ZGQzZWYwOTYxMmY0MzQ3YmRmMDA5Nzc5MDk2MzY2OS9ub3RlLmpzb24)

# Amazon S3
### Configure
* Bucket Name (required)


### Read data from Amazon S3
[Open Examples in Zepl](https://app.zepl.com/viewer/notebooks/bm90ZTovL3pzaGFpbnNreUB6ZXBsLmNvbS8yYWE1M2I1MjAzMzE0NGM4OWQ0NGYwMjNmNTRmOTAwMC9ub3RlLmpzb24)

| Language | Code | Object Returned | Library |
|---------|------|-----------------|---------|
|Python   | `s3_bucket = z.getDatasource("<data source name>")`| [Boto3 Bucket Object](https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/s3.html#bucket) | Boto3 - v1.10.9

### Write data to Amazon S3
[Open Examples in Zepl](https://app.zepl.com/OQ4NBK79S/notebooks/9fb05a846a394f8788a22f65796fb413)

# Google BigQuery
### Configure
* Google Cloud Project ID (required)


### Read data from BigQuery
[Open Examples in Zepl](https://app.zepl.com/viewer/notebooks/bm90ZTovL3pzaGFpbnNreUB6ZXBsLmNvbS9iNTk4MjBjMjg0YmQ0NDkzYjdkZmI1NjU5ZDY4NTNkYi9ub3RlLmpzb24)

| Language | Code | Object Returned | Library |
|----------|------|-----------------|---------|
| Python | `client = z.getDatasource("<data source name>")` | [BigQuery Client Object](https://googleapis.dev/python/bigquery/latest/reference.html#client)| google-cloud-bigquery - v1.21.0 |

### Write data to BigQuery
> Example coming soon!

# MySQL
### Configure
* Host (required)
* Port (required)
* Database (optional)


### Read data from MySQL
[Open Examples in Zepl](https://app.zepl.com/viewer/notebooks/bm90ZTovL3pzaGFpbnNreUB6ZXBsLmNvbS83YzY2MjkwMzIyMjY0OTk4OWM5YTgxNDA4YmQzOWRiYi9ub3RlLmpzb24)

| Language | Code | Object Returned | Library |
|----------|------|-----------------|---------|
| Python | `conn = z.getDatasource("<data source name>")` | [mysql.connector.connect](https://dev.mysql.com/doc/connector-python/en/connector-python-api-mysqlconnection-connect.html)|mysql-connector-python - v8.0.18 |
| SQL | `%datasource.<data source name>`| | |

### Write data to MySQL
>Example coming soon!

# PostgreSQL
### Configure
* Host (required)
* Port (required)
* Database (optional)

### Read data from PostgreSQL
[Open Examples in Zepl](https://app.zepl.com/viewer/notebooks/bm90ZTovL3pzaGFpbnNreUB6ZXBsLmNvbS8yMDc4ZWZmNjE0MDU0MzJlOTEyMWYwNjcxNjBlZjg4Ni9ub3RlLmpzb24)

| Language | Code | Object Returned | Library |
|----------|------|-----------------|---------|
| Python | `conn = z.getDatasource("<data source name>")` | [psycopg2.connect](https://www.psycopg.org/docs/connection.html) | psycopg2-binary - v2.8.4 |
| SQL | `%datasource.<data source name>`| | |

### Write data to PostgreSQL
> Example coming soon!

# Apache Cassandra
### Configure
* Host (required)
* Port (required)
* Keyspace (optional)


### Read data from Apache Cassandra
[Open Examples in Zepl](https://app.zepl.com/viewer/notebooks/bm90ZTovL3pzaGFpbnNreUB6ZXBsLmNvbS9kMmJjMWY5ZDlhZWI0NzIxYjgwZDEyZDQ2OGFiODVmNC9ub3RlLmpzb24)

| Language | Code | Object Returned | Library |
|----------|------|-----------------|---------|
| Python | `session  = z.getDatasource("<data source name>")` | [cluster.connect.session](https://docs.datastax.com/en/developer/python-driver/3.24/api/cassandra/cluster/#cassandra.cluster.Session)| cassandra-driver - v3.20.0 |

### Write data to Apache Cassandra
> Example coming soon!

# SAP HANA
### Configure
* Host (required)
* Port (required)
* Database (optional)

### Read data from SAP HANA
>Example coming soon!

| Language | Code | Object Returned | Library |
|----------|------|-----------------|---------|
| Python | `conn = z.getDatasource("<data source name>")` | [dbapi.connect](https://help.sap.com/viewer/f1b440ded6144a54ada97ff95dac7adf/2.5/en-US/3b5ebe388c1040ec83617c9e511ecda5.html) | hdbcli - v2.4.167 |
| Scala | ```val df = z.getDatasource("<data source name>").asInstanceOf[org.apache.spark.sql.DataFrameReader]``` | Spark SQL Dataframe: [org.apache.spark.sql.DataFrameReader](https://spark.apache.org/docs/2.3.1/api/java/org/apache/spark/sql/DataFrameReader.html)|

### Write data to SAP HANA
> Example coming soon!

# Alibaba MaxCompute
### Configure
* Endpoint (required)
* Region (required)
* Project (required)

### Read data from Alibaba MaxCompute
> Example coming soon!

| Language | Code | Object Returned | Library |
|----------|------|-----------------|---------|
| Python | `odps = z.getDatasource("<data source name>")` | [ODPS Object](https://pyodps.readthedocs.io/en/latest/index.html)| pyodps - v0.8.4 |
| Scala | ```val df = z.getDatasource("<data source name>").asInstanceOf[org.apache.spark.sql.DataFrameReader]``` | Spark SQL Dataframe: [org.apache.spark.sql.DataFrameReader](https://spark.apache.org/docs/2.3.1/api/java/org/apache/spark/sql/DataFrameReader.html) | odps-jdbc-3.1.0.jar |

### Read data to Alibaba MaxCompute
> Example coming soon!
