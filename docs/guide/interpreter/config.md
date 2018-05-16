<h1> Inline Interpreter configuration </h1>

`%[Interpreter name].config` is a special interpreter that allows for interpreter properties and environment variables to be configured in each notebook. This features brings additional flexibility enabling users to do, among other things:

  - Share a notebook with a custom interpreter configuration or specific environment variable the paragraphs require already set. 
  - Fine-grained control on interpreter configuration at notebook level.


## Usage

```
%[Interpreter name to configure].config
[Key 2] = [Value 1]         # comment
[Key 2] = [Value 2]
...
```

Note that inline configuration must run before any other paragraph. So it will usually be the first paragraph in the notebook.

### Key

Key can not include empty space. `[A-Z_0-9]+` is treated as a environment variable, otherwise it's considered an interpreter property. e.g.:

 - `spark.app.name`, `zeppelin.python` - Interpreter property
 - `SPARK_HOME`, `CUSTOM_VAR` - Environment variable

### Value

Value is separated by spaces or tabs from Key. Value can include any character except for newline. For example, following are all valid:

 - `100`, `true`, `/dir/path`, `spark app name`



### Example


```
%spark.config

spark.app.name = ZEPL            # override default spark app name
AWS_ACCESS_KEY_ID = ....         # AWS access key environment variable
AWS_SECRET_ACCESS_KEY = ....     # AWS secret key environment variable
```

```
%spark
val data = sc.read.text("s3a://...")
```


## Available configurations

**1. `%python.config`**

| key | value | description |
| --- | ---- | ---- |
| zeppelin.python | `python` or `python3` | Python command to use. `python` for 2.x, `python3` for 3.x. You can also configure python version by creating [conda environment](/guide/interpreter/python/#manage-python-environment).|
| zeppelin.python.maxResult | Number (e.g. `10000`) | Max number of dataframe rows to display. |


**2. `%spark.config`**

| key | value | description |
| --- | ---- | ---- |
| zeppelin.spark.useHiveContext | `true` or `false` | Use HiveContext instead of SQLContext if it is true (default).|
| zeppelin.spark.maxResult | Number (e.g. 10000) | Max number of Spark SQL result to display. |
| zeppelin.dep.additionalRemoteRepository | A list of 'id,remote-repository-URL,is-snapshot;'. <br />e.g. `spark-packages,http://dl.bintray.com/spark-packages/maven,false;` | Additional maven repository for spark dependency interpreter `%spark.dep`. |
| zeppelin.pyspark.python | `python` or `python3` | Python command to use in pyspark. `python` for 2.x, `python3` for 3.x.|

**3. `%jdbc.config`**

| key | value | description |
| --- | ---- | ---- |
| default.url | JDBC url. e.g. `jdbc:postgresql://my.host.com:5432` | JDBC URL to connect. |
| default.user | String | user name. |
| default.password | String | password. |
| default.driver | Driver class name. e.g. `org.postgresql.Driver` | JDBC driver class name. |
| common.max_count | Number (e.g. `10000`) | Maximum number of rows to return. |
