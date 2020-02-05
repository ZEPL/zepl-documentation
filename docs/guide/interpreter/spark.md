title: Spark Interpreter | Zepl and Apache Spark
description: Apache Spark is an open source processing engine built around speed, ease of use and sophisticated analytics. Learn about Zepl's Apache Spark interpreters. 
# Apache Spark Interpreter

[Apache Spark](https://spark.apache.org) is an open source processing engine built around speed, ease of use and sophisticated analytics. Zepl provides several interpreters for Apache Spark as follows:

 * `%spark` - provides a Scala environment
 * `%spark.pyspark` - provides a Python environment
 * `%spark.sql` - provides a SparkSQL environment
 * `%spark.dep` - loads dependency libraries into a Spark environment
 * `%spark.r` - provides an R environment

A single Spark context is shared among `%spark`, `%spark.pyspark`, `%spark.sql` and `%spark.r` sessions. Zepl currently runs Apache Spark v2.3.0 on a single node (non-distributed) per notebook container.

## Loading Data from AWS S3

To create a dataset from AWS S3 it is recommended to use the `s3a` connector. First, you need to configure your access and secret keys as follows:

```scala
%spark
sc.hadoopConfiguration.set("fs.s3a.access.key", "[YOUR_ACCESS_KEY]")
sc.hadoopConfiguration.set("fs.s3a.secret.key", "[YOUR_SECRET_KEY]")
```

Then your Spark context will be able to create a dataset from S3 like so:

```scala
%spark
val data = spark.read.text("s3a://apache-zeppelin/tutorial/bank/bank.csv")
```

Alternatively you can load data using the `s3n` connector. In this case your access and secret keys can be configured in the following way:

```scala
%spark
sc.hadoopConfiguration.set("fs.s3n.awsAccessKeyId", "[YOUR_ACCESS_KEY]")
sc.hadoopConfiguration.set("fs.s3n.awsSecretAccessKey", "[YOUR_SECRET_KEY]")
```

And your data accessed as follows:

```scala
%spark
val data = sc.textFile("s3n://....")
```

You can reference the [data loading example notebook](https://www.zepl.com/viewer/notebooks/bm90ZTovL21vb24vY2RjMzQ1NTljOTkzNDNhMTk4NGE0ZWUzNjU1NjgxZWQvbm90ZS5qc29u) to try it yourself.

## Loading Dependencies

When your code requires external libraries `%spark.dep` helps load them from a maven repository. The `%spark.dep` interpreter leverages the Scala environment. You can write scala expressions to call dependency load APIs.

Note that `%spark.dep` should be the first interpreter run in the notebook before `%spark`, `%spark.pyspark` or `%spark.sql`. Otherwise, `%spark.dep` will print error messages and you'll need to shutdown and restart the container for the notebook again.

Check the [Spark dependency loading example notebook](https://www.zepl.com/viewer/notebooks/bm90ZTovL21vb24vZjBmYWIwNGMzZTcxNDMwN2FjYzIxM2JkYmU3ZWIyZWEvbm90ZS5qc29u) for details.

### Usages

```scala
%spark.dep
z.reset() // clean up previously added artifact and repository

// add maven repository
z.addRepo("RepoName").url("RepoURL")

// add maven snapshot repository
z.addRepo("RepoName").url("RepoURL").snapshot()

// add credentials for private maven repository
z.addRepo("RepoName").url("RepoURL").username("username").password("password")

// add artifact from filesystem
z.load("/path/to.jar")

// add artifact from maven repository, with no dependency
z.load("groupId:artifactId:version").excludeAll()

// add artifact recursively
z.load("groupId:artifactId:version")

// add artifact recursively except comma separated GroupID:ArtifactId list
z.load("groupId:artifactId:version").exclude("groupId:artifactId,groupId:artifactId, ...")

// exclude with pattern
z.load("groupId:artifactId:version").exclude(*)
z.load("groupId:artifactId:version").exclude("groupId:artifactId:*")
z.load("groupId:artifactId:version").exclude("groupId:*")

// local() skips adding artifact to spark clusters (skipping sc.addJar())
z.load("groupId:artifactId:version").local()
```

## SparkR

Installed libraries - `ggplot2`, `googleVis`, `knitr`, `data.table`, `devtools`


```r
%spark.r
library(googleVis)
bubble <- gvisBubbleChart(Fruits, idvar="Fruit",
                          xvar="Sales", yvar="Expenses",
                          colorvar="Year", sizevar="Profit",
                          options=list(
                            hAxis='{minValue:75, maxValue:125}'))
print(bubble, tag = 'chart')
```

```r
%spark.r
plot(iris, col = heat.colors(3))
```

```r
%spark.r
library(ggplot2)
pres_rating <- data.frame(
  rating = as.numeric(presidents),
  year = as.numeric(floor(time(presidents))),
  quarter = as.numeric(cycle(presidents))
)
p <- ggplot(pres_rating, aes(x=year, y=quarter, fill=rating))
```
