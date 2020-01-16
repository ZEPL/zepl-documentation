# Data Source Integrations
Zepl currently integrates with Snowflake, S3, MySQL, PostgreSQL, Cassandra, and SAP HANA - we are constantly adding more, so let us know if something you were hoping to use is not yet available!
All Data Source integrations follow the same flow for configuring - you name your Data Source and add a helpful description, you add JDBC connection string information, and you add a set of user-specific personal credentials to allow you to securely establish a connection. Mandatory fields vary slightly for each Data Source integration.

### Snowflake
#### Username & Password
If your Snowflake instance is configured to log in with a Snowflake username and password, use this Data Source configuration option.

Warehouse, Database, and Schema are an optional field to allow a Data Source to be defined a single time for many use cases, but if they are not provided, they must be declared in the SQL statements you send to snowflake.

Role is also an optional field, and can be provided by users to refine their access to objects in Snowflake as defined by the Snowflake account permissions set by your administrator.

<img src="../../../img/datasource/snowflake_create_popup_1.png" class="image-box img-100" />

#### SSO Authentication
If your Snowflake instance is configured to log in with an external authentication provider, use this Data Source configuration option. Your Snowflake administrator will need to go through a few steps to extend authentication from Snowflake to Zepl before you will be able to establish a connection. You can follow the steps here.

Warehouse, Database, and Schema are an optional field to allow a Data Source to be defined a single time for many use cases, but if they are not provided, they must be declared in the SQL statements you send to snowflake.

Once the Snowflake account admin has properly integrated your snowflake instance with your snowflake security, you should be able to use whatever SSO provider your organization has elected to use to connect to your Snowflake instance.

Role is also an optional credential field, and can be provided by users to refine their access to objects in Snowflake as defined by the Snowflake account permissions set by your administrator.  Schema is an optional field but is required for R.

<img src="../../../img/datasource/snowflake_create_popup_2.png" class="image-box img-100" />

### Amazon S3
<img src="../../../img/datasource/s3_create_popup.png" class="image-box img-100" />

### MySQL
<img src="../../../img/datasource/mysql_create_popup.png" class="image-box img-100" />

### PostgreSQL
<img src="../../../img/datasource/postgresql_create_popup.png" class="image-box img-100" />

### Cassandra
<img src="../../../img/datasource/cassandra_create_popup.png" class="image-box img-100" />

### SAP Hana
<img src="../../../img/datasource/hana_create_popup.png" class="image-box img-100" />
