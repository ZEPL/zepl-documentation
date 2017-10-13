<h1> Apache Spark Interpreter </h1>

[Apache Spark](https://spark.apache.org) is an open source processing engine built around speed, ease of use, and sophisticated analytics. ZEPL provides several interpreters for Apache Spark.

 * `%spark` - Provides a Scala environment
 * `%spark.pyspark` - Provides a Python environment
 * `%spark.sql` - Provides SparkSQL environment
 * `%spark.dep` - Load dependency libraries into Spark environment

A single Spark context is shared among `%spark`, `%spark.pyspark`, `%spark.sql` sessions.
ZEPL currently runs single node Apache Spark 2.1.0 in the containers of each notebooks.

## Load data from AWS S3

To load data from AWS S3, first you need configure access key and secret key.

```
%spark
sc.hadoopConfiguration.set("fs.s3n.awsAccessKeyId", "[YOUR_ACCESS_KEY]")
sc.hadoopConfiguration.set("fs.s3n.awsSecretAccessKey", "[YOUR_SECRET_KEY]")
```

And then your Spark context will able to access data from S3

```
%spark
val data = sc.textFile("s3n://....")
```

Check [data loading example](https://www.zepl.com/viewer/notebooks/bm90ZTovL21vb24vY2RjMzQ1NTljOTkzNDNhMTk4NGE0ZWUzNjU1NjgxZWQvbm90ZS5qc29u) notebook.

## Load dependencies

When your code requires external library, `%spark.dep` helps load additional libraries from maven repository. `spark.dep` interpreter leverages Scala environment. You can write scala expressions to call dependency load APIs.

Usages

```
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

Note that `%spark.dep` should be the first interpreter run in the notebook before `%spark`, `%spark.pyspark`, `%spark.sql`. Otherwise, `%spark.dep` will print error message and you need to shutdown and start the container for the notebook again.

Check [Dependency loading example](https://www.zepl.com/viewer/notebooks/bm90ZTovL21vb24vZjBmYWIwNGMzZTcxNDMwN2FjYzIxM2JkYmU3ZWIyZWEvbm90ZS5qc29u) notebook.
