title: Python for Data Analysis | Spark Data Analysis | Zepl
description: This topic describes how to upload data into Zepl and analyze it using Spark, Python for data analysis, or other Zepl interpreters. Visit us to learn more.
# Uploading and Downloading Data

This section describes how to upload data from your own filesystem into Zepl and analyze it using Spark, Python and other interpreters within Zepl. You can also download and delete the uploaded data.

## Uploading Data

If you have data files on your local machine that you want to analyze with Zepl you can upload the file by clicking the right menu bar in your notebook and choosing the *Upload file* button. You can also simply drag and drop the relevant file into the sidebar. You can upload multiple files which are only accessible through the given notebook. To access the same file in different notebooks the file will need to be uploaded to each notebook separately.

> Note: Currently we allow up to 100MB in total.

## Accessing Data

Once the file is uploaded to the notebook, you can access the file by the following URL (where *&lt;file-name&gt;* is the name of the file):

```
http://zdata/<file-name>
```

Here are some examples you can use:

**Scala**

```scala
%spark

import org.apache.spark.SparkFiles

sc.addFile("http://zdata/bank.csv")
val sparkDF = spark.read.format("csv")
  .option("delimiter", ";")
  .option("header", "true")
  .option("inferSchema", "true")
  .load(SparkFiles.get("bank.csv"))
```

**PySpark**

```python
%spark.pyspark

from pyspark import SparkFiles

sc.addFile('http://zdata/bank.csv')
sparkDF = spark.read.format('csv').options(delimiter=';', header='true', inferSchema='true').load(SparkFiles.get('bank.csv'))
```

**SparkR**

```r
%spark.r

spark.addFile("http://zdata/bank.csv")
sparkDF <- read.df(path = spark.getSparkFiles("bank.csv"), source = "csv", delimiter = ";", header = "true", inferSchema = "true")
```

If you want to read your data into Python directly, you can also read your data using [*pandas*](https://pandas.pydata.org/). For example:

**Python**

```python
%python

import pandas as pd
pandas_df = pd.read_csv('http://zdata/bank.csv', sep=';', header='infer')
```

## Downloading Data

If the data volume is small enough, you can also load this data directly into the container. You can use `%python !wget http://zdata/<file-name>` to download data to the container. Once the file is downloaded to the container, you can access the downloaded file as a local file.

For example, you can use the following code to access the data after downloading a file named *bank.csv* to the container:

```scala
%spark

val sparkDF = spark.read.format("csv")
  .option("delimiter", ";")
  .option("header", "true")
  .option("inferSchema", "true")
  .load("bank.csv")
```

## Editing Data

You cannot edit data directly within Zepl but you can overwrite the data file by uploading a file with the same name.

> Warning: Overwritten data cannot be recovered.

## Deleting Data

To delete data, click the red "x" button next to the data file in the *Files* tab on the notebook page.

> Warning: Deleted data cannot be recovered.
