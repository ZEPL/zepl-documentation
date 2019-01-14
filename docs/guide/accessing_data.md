<h1>Uploading Data</h1>

This topic describes how to upload data into ZEPL, and analyze it using Spark, Python, or other interpreters within ZEPL.

## Import data

If you have files (up to 100MB in size) on your local machine that you want to analyze with ZEPL, you can upload the file by clicking the right menu bar in your notebook and choosing the **Upload** button, or by simply dragging and dropping the relevant file into the sidebar. Once you upload the files to the notebook, the uploaded files are only accessible through the given notebook.

> Notes: The files are mapped to the notebook it was uploaded. To access the same file in different notebooks, the file will need to be uploaded to each notebook separately.

## Load data

Once the file is uploaded to the notebook, you can access the file by the following URL (where the **&lt;file-name&gt;** is the name of the file):

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

If you want to read your data into Python directly, you can also read your data directly using [*pandas*](https://pandas.pydata.org/). For example:

**Python**

```python
%python

import pandas as pd
pandas_df = pd.read_csv('http://zdata/bank.csv', sep=';', header='infer')
```

## Download data

If the data volume is small enough, you can also load this data directly onto the container. You can use `%python !wget http://zdata/<file-name>` to download data to the container. Once the file is downloaded to the container, you can access the downloaded file as a local file.

For example, you can use the following code to access the data after downloading a file named *bank.csv* to the container:

```scala
%spark

val sparkDF = spark.read.format("csv")
  .option("delimiter", ";")
  .option("header", "true")
  .option("inferSchema", "true")
  .load("bank.csv")
```

## Edit data

You cannot edit data directly within ZEPL, but you can overwrite the data file by uploading a file with the same name.

> Warning: Overwritten data cannot be recovered.

## Delete data

To delete data, click the delete button next to the data file in the **Files** tab on the notebook page.

> Warning: Deleted data cannot be recovered.