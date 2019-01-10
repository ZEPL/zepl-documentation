<h1>Accessing Data</h1>

This topic describes how to import data, load data using the Spark API, and edit and delete data.

## Import data

If you have small files on your local machine that you want to analyze with ZEPL, you can easily upload them to ZEPL File System. To upload data, drop files into or browse to files in the **Files** tab on the notebook page.

## Load data

You can read your raw data into Spark directly. For example, if you uploaded a CSV, you can read your data using one of these examples.

**Scala**

```
%spark

import org.apache.spark.SparkFiles

sc.addFile("http://zdata/bank.csv")
val sparkDF = spark.read.format("csv")
  .option("delimiter", ";")
  .option("header", "true")
  .option("inferSchema", "true")
  .load(SparkFiles.get("bank.csv"))
```

**Python**

```
%spark.pyspark

from pyspark import SparkFiles

sc.addFile('http://zdata/bank.csv')
sparkDF = spark.read.format('csv').options(delimiter=';', header='true', inferSchema='true').load(SparkFiles.get('bank.csv'))
```

**R**

```
%spark.r

spark.addFile("http://zdata/bank.csv")
bank <- read.df(path = spark.getSparkFiles("bank.csv"), source = "csv", delimiter = ";", header = "true", inferSchema = "true")
```

If you want to read your data into Python directly, you can also read your data directly using [*pandas*](https://pandas.pydata.org/). For example:

**Python**

```
%python

import pandas as pd
pandas_df = pd.read_csv('http://zdata/bank.csv', sep=';', header='infer')
```

## Download data

If the data volume is small enough, you can also load this data directly onto the container. You can use `%python !wget http://zdata/<filename>` to download data to the container.

## Edit data

You cannot edit data directly within ZEPL, but you can overwrite the data file by uploading a file with the same name.

> Warning: Overwritten data cannot be recovered.

## Delete data

To delete data, click the delete button next to the data file in the **Files** tab on the notebook page.

> Warning: Deleted data cannot be recovered.