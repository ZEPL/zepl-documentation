# Snowflake Data Source

Snowflake is cloud-built data warehouse that delivers instant elasticity, secure data sharing across multiple clouds. Snowflake combines the power of data warehousing, the flexibility of big data platforms and the elasticity of the cloud at a fraction of the cost of traditional solutions.

The Zepl/Snowflake integration provides a unified, cohesive, and highly scalable solution to enable data science teams to rapidly explore, analyze, visualize and collaborate around their entire data warehouse.

## Establishing Snowflake Data Source Connection

1. Click _Data Source_ icon in the upper right side to open data source panel and click _Add New_ button.
<img src="../../../img/datasource/snowflake_note.png" class="image-box img-100" />

2. Set _Type_ as _Snowflake_ and provide a name. Name should be unique within organization since the name will be used as data source identifier when you call it from the notebook. For the purposes of this guide we used `Zepl_Snowflake`.
<img src="../../../img/datasource/snowflake_create_popup_1.png" class="image-box img-70" />

3. Enter the account name associated with your Snowflake account, without the "@snowflakecomputing.com" extension. There are 3 other optional fields (_warehouse_, _database_, and _schema_) to further customize the details for this source.
<img src="../../../img/datasource/snowflake_create_popup_2.png" class="image-box img-70" />

4. Enter your Snowflake account user and password credentials and click the _Create_ button. The Snowflake source will be auto-attached to the notebook so that you can use the data source inside of notebook. You can detach datasource if you are not gonna use it in the notebook. By having attach/detach mechanism, notebook execution container doesn't need to keep unnecessary connections to data sources. The data source created here is available to all members in the organization and can be used in other notebooks. But for other members to use the data source, they need to set their own credential.
<img src="../../../img/datasource/snowflake_create_popup_3.png" class="image-box img-70" />

5. To verify if the Snowflake configuration is valid to establish connection, click _Test all connections_. Green check icon will be shown if it succeeds. If it fails, warning icon will be shown with tooltip describing the cause of failure. <br />
<img src="../../../img/datasource/snowflake_test_connection_success.gif" class="image-box img-35" style="margin-right: 20px;" />
<img src="../../../img/datasource/snowflake_test_connection_fail.gif" class="image-box img-35" />

### Exploring Data from Snowflake Data Source

Once you create the data source, you can explore and interact with Snowflake data warehouse via python, spark, sql interpreter. Name of data source will be used to refer the data source you want to use. In below example we used `Zepl_Snowflake` as data source name.

#### Python Example
```python
%python
import pandas as pd
# establish connection to Snowflake
conn = z.getDatasource('Zepl_Snowflake')

# execute query
res = conn.execute('SELECT * FROM ITEM LIMIT 1000')

# convert datasource into pandas dataframe
df = pd.DataFrame(res)
df.columns = [col[0] for col in conn.description]

# print dataframe as table
z.show(df)
```

#### Spark Example
```scala
%spark
// establish connection to Snowflake and read query result as spark dataframe
val df = z.getDatasource("Zepl_Snowflake")
  .asInstanceOf[org.apache.spark.sql.DataFrameReader]
  .option("query", "SELECT * FROM ITEM LIMIT 100")
  .load()

// print dataframe as table
z.show(df)
```

#### SQL Example
```sql
%datasource.Zepl_Snowflake
SELECT * FROM ITEM LIMIT 1000
```

### Managing Data Sources
You can manage data sources created under the organization in _Data Sources_ page.
Everyone in the organization has access to this page and anyone can add new data sources, update and delete. Even when the data source is created by other member, you can use them by setting your credential. _My credential_ column indicates if you have your credential set or not. In addition, you can see how many members set their own credential and how many notebooks the data source is attached to.
<img src="../../../img/datasource/datasource_manage.png" class="image-box img-100" />
