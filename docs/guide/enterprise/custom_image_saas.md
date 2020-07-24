# Custom Images

Creating a reproducible environment for data science is a common challenge when working as a team on a data science challenge. It is common practice to put several install commands at the beginning of a notebook or script to help ensure that others will be able to recreate your analysis. Unfortunately, this installation step can take a long time when many different libraries and packages are required. 

This is where Zepl Custom Images can help you and your team save significant time. Every time you run a notebook, you are spinning up a container which contains an “image” - a prebuilt environment with the all the libraries and settings your team needs for reproducible data science. Custom Images lets you create images that contain as many or as few libraries as your team needs.

Contact beta@zepl.com to sign up and learn more!

# Creating a New Custom Image

Custom Images can easily be found under Resources. To start creating a new custom image, simply click “Create new”. If you have another Custom Image which you’d like to modify as a template for your new image, you can also “Clone” that template under the actions for that Custom Image.

<img src=“/img/CI_CREATE_NEW.png” class=“image-box img-100”/>

Each Custom Image should have a unique, descriptive name that makes it easy to find later. As a first step of creating a Custom Image, give your image a name and a description of what you plan to use it for. 

<img src=“/img/CI_CREATE_NEW_MODAL.png” class=“image-box img-100”/>

After naming your image, you are ready to start configuring your Custom Image with interpreters, libraries, packages, and system dependencies. The syntax for doing this is documented below.

To build your custom image, click the “Create” button at the bottom. Building the image will take a few minutes, and takes longer when more libraries are installed to the image. Sometimes builds can fail if the wrong syntax is used, or there is a library version mismatch issue. If that occurs, you can download a log in the image actions which describes where the build failed.  If the image builds successfully, congrats! You can now attach it to notebooks. If you’d like the image you created to be the standard for your entire organization, you can set it as the default image in the image actions. You can also edit or delete an image under these image actions. 

# Adding Python Interpreter & Libraries

To add a Python interpreter to a Custom Image, simply click “+ Python” in the image creation screen. Zepl supports Python 3.8 as the default Python interpreter for custom images. Today, you cannot edit the %alias of an interpreter nor can you add more than one version of a Python interpreter to a Custom Image. 

<img src=“/img/CI_CREATE_NEW_PYTHON.png” class=“image-box img-100”/>

To add libraries to your custom image, you can use the following supported to install libraries using pip:

    Libraryname
    libraryname==version

In addition to any libraries that you include in your custom image list, Zepl installs multiple Python libraries to the image necessary for Zepl to function well. If you try to install a different version of these libraries, it is possible you may run into a compatibility issue. You can always see what versions of libraries you have installed in your image by running a pip list command in the notebook. As of July 2020, the list of libraries we install for Python in a custom image are the following:


    grpcio==1.24.3 
    ipykernel==5.1.3 
    ipython==7.13.0 
    jupyter-client==5.3.4 
    protobuf==3.10.0 
    py4j==0.10.8.1
    boto3==1.10.9 
    cassandra-driver==3.22.0 
    google-cloud-bigquery==1.21.0 
    mysql-connector-python==8.0.18 
    snowflake-connector-python==2.2.7 
    hdbcli==2.4.167 
    psycopg2-binary==2.8.4 
    pyodps==0.8.4


# Adding R Interpreter & Libraries

To add an R interpreter to a Custom Image, simply click “+ R” in the interpreter creation screen. Zepl supports R 3.6 as the default R interpreter for custom images. Today, you cannot edit the %alias of an interpreter nor can you add more than one version of an R interpreter to a Custom Image. 

<img src=“/img/CI_CREATE_NEW_R.png” class=“image-box img-100”/>

To add libraries from a CRAN server to your custom image, you simply list out the libraries you hope to install on seperate lines. This installs packages similarly to using install.package(“LibraryName”) in the notebook

    Libraryname1
    Libraryname2

In addition, you can install libraries using the devtools. The following syntaxes are supported:

    devtools::install_github() from github
    devtools::install_bitbucket() from bitbucket
    devtools::install_url() from an arbitrary url
    devtools::install_version() installs a specified version from cran


In addition to any libraries that you include in your custom image list, R comes with many libraries already installed, and Zepl installs multiple R libraries to the image necessary for Zepl to function well. If you try to install a different version of these libraries, it is possible you may run into a compatibility issue. You can always see what versions of libraries you have installed in your image by running a installed.packages() command. As of July 2020, the list of libraries we install for R in a custom image are the following:

    devtools 
    DatabaseConnector 
    dplyr 
    knitr 
    rJava 
    RJDBC 
    snowflakedb/dplyr-snowflakedb

# Adding Spark Interpreter & Libraries

To add a Spark interpreter to a Custom Image, simply click “+ Spark” in the interpreter creation screen. Zepl supports Spark 2.3.2 as the default Spark interpreter for custom images. Today, you cannot edit the %alias of an interpreter nor can you add more than one version of a Spark interpreter to a Custom Image. 

<img src=“/img/CI_CREATE_NEW_SPARK.png” class=“image-box img-100”/>

To add libraries to Spark, you can do so by adding maven dependencies on separate lines. Please note that we only support compile and exclude_group commands in the syntax today. 

    compile “commons-io:commons-io:2.6”
    compile(“org.apache.hadoop:hadoop-aws:2.8.3”) { exclude group ‘javax.servlet’, module: ‘servlet-api’}


In addition to any libraries that you include in your custom image list, Spark comes with many libraries already installed, and Zepl installs multiple Spark libraries to the image necessary for Zepl to function well. If you try to install a different version of these libraries, it is possible you may run into a compatibility issue. You can always see what versions of libraries you have installed in your image by running the following code in the notebook:

    %pyspark
    !ls /usr/zepl/interpreter/lib/

As of July 2020, the list of libraries we install for Spark in a custom image are the following:

    interpreterDatasource "mysql:mysql-connector-java:8.0.18"
    interpreterDatasource "org.postgresql:postgresql:42.2.8"
    interpreterDatasource "net.snowflake:snowflake-jdbc:3.12.5"
    interpreterDatasource "com.sap.cloud.db.jdbc:ngdbc:2.4.63"
    interpreterDatasource "com.aliyun.odps:odps-jdbc:3.1.0"
    interpreterDatasource "com.google.cloud.spark:spark-bigquery-with-dependencies_2.11:0.15.1-beta"
    interpreterDatasource "com.aliyun.odps:odps-jdbc:3.1.0"
    interpreterDatasource("com.datastax.spark:spark-cassandra-connector_2.11:2.0.11")
    interpreterDatasource("net.snowflake:spark-snowflake_2.11:2.7.1-spark_2.2")
    interpreterDatasource("org.apache.spark:spark-hive_2.11:2.2.1")

# Adding System Dependencies

You can add environmental variables and packages to your image with this feature. This can be helpful because certain libraries sometimes require underlying infrastructure to be installed to or environment variables set in the image for certain libraries to work properly. 

You can set an environment variable with very simple syntax: 

    VAR1=123
    VAR2=456

You can install packages from github directories with maven syntax. 

<img src=“/img/CI_CREATE_NEW_SYSTEM_DEPENDENCIES.png” class=“image-box img-100”/>

# Custom Image Management

Custom Images can easily be managed and analyzed from the Custom Images management console. For any existing image that you have created, you can see what it is called, who created the image, if the image successfully created, when it was created, and what notebooks are associated with the image. 

<img src=“/img/CI_MANAGEMENT.png” class=“image-box img-100”/>

For any Custom Image that you are curious in learning more about, you can click on the row to learn more about how that custom image was constructed. Under the actions menu for custom images, you can perform the following operations: 

**Clone:** This lets you use an existing image as a template to modify while creating a new image
**Edit:** This lets the creator of an image modify the configuration of the image
**Delete:** This lets the creator of an image delete the image
**Set as Default:** This sets an image as the default image for all users in an organization

# Using a Custom Image In A Notebook 

When you are creating a new notebook, you must select the Custom Image you want to use to execute code from that notebook.

<img src=“/img/CI_NB_CREATE.png” class=“image-box img-100”/>

In the notebook, we’ve designed a toolbar on the right hand side which helps you see what interpreters and libraries are available for you to use in your custom image. 

<img src=“/img/CI_NB_SIDEBAR.png” class=“image-box img-100”/>

You can change this selection at any time for a given notebook by editing the notebook settings - to do so, your container must be shut down.

<img src=“/img/CI_NB_SETTINGS.png” class=“image-box img-100”/>




