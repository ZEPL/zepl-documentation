<h1>Integration with Amazon EMR</h1>

[Amazon EMR](https://aws.amazon.com/emr/) is a managed cluster platform that simplifies running big data frameworks, such as Apache Hadoop and Apache Spark, on AWS to process and analyze vast amounts of data.

> Important: This article applies to the [Enterprise plan](https://www.zepl.com/plans-and-pricing/) (with AWS Cloud) only.

## Working with Amazon EMR Clusters

### Step 1: Launch the Amazon EMR Cluster

In this step, you launch the Amazon EMR cluster by using the Amazon EMR console or the AWS CLI.

#### Launch the Amazon EMR Cluster

You can launch the Amazon EMR cluster using the Amazon EMR console and the AWS CLI.

##### To launch an Amazon EMR cluster using the Amazon EMR console

Sign in to the AWS Management Console and open the [Amazon EMR console](https://console.aws.amazon.com/elasticmapreduce/).

1. Choose **Create cluster**.

1. Click **Go to advanced options**.

1. On the **Software and Steps** step, accept the default values except for the following fields and choose **Next**. For more information, see [Configure Cluster Software](https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-plan-software.html).

    - For **Software Configuration**, choose the Amazon EMR release and applications which you want to use. To see which software configuration is supported in ZEPL, see [Docker Images Provided by ZEPL](#docker-images-provided-by-zepl).

1. On the **Hardware** step, accept the default values except for the following fields and choose **Next**. For more information, see [Configure Cluster Hardware and Networking](https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-plan-instances.html).

    - For **Network**, choose the VPC which is the Amazon ECS cluster for ZEPL is running in. In general, you can choose the VPC which is the ZEPL application is running in. The VPC for the Amazon ECS cluster is mostly the same as the ZEPL application.
    - For **EC2 Subnet**, choose the *public* subnets to make your cluster directly accessible from the internet or *private* subnets to avoid making cluster directly accessible from the internet.

1. On the **General Cluster Settings** step, add the bootstrap action to configure the Amazon EMR cluster to work with ZEPL and choose **Next**.

    > Notes: In the case you don't want to add the bootstrap action, you can configure the Amazon EMR cluster manually. For more information, see [Configure the Amazon EMR cluster](#configure-the-amazon-emr-cluster).

    1. Under **Bootstrap Actions**, choose the **Custom action** and select **Configure and add**.
    1. For **Name**, enter a name for the bootstrap action, such as ***ZEPL***.
    1. For **Script location**, enter as follows: ***s3://zepl/emr/bootstrap.sh***.
    1. Choose **Add**.

1. On the **Security** step, accept the default values except for the following fields and choose **Create cluster**.

    - For **EC2 key pair**, choose the key pair that you have. You must have an Amazon EC2 key pair to connect to the nodes in your cluster over a secure channel using the Secure Shell (SSH) protocol. If you don't want to connect to the nodes in your cluster, choose **Proceed without an EC2 key pair**.

1. Proceed to the [next step](#step-2-create-the-resource).

##### To launch an Amazon EMR cluster using the AWS CLI

To launch a cluster to work with ZEPL, type the following command, replace *myKey* with the name of your EC2 key pair and *subnet-xxxxx* with the VPC subnet in which to create the cluster. For more information, see [AWS CLI Command Reference](https://docs.aws.amazon.com/cli/latest/reference/emr/create-cluster.html).

```sh
$ aws emr create-cluster --name "ZEPL cluster" --release-label emr-5.14.0 \
--use-default-roles --ec2-attributes KeyName=myKey,SubnetId=subnet-xxxxx \
--applications Name=Hadoop Name=Hive Name=Spark \
--instance-count 3 --instance-type m3.xlarge \
--bootstrap-actions Path="s3://zepl/emr/bootstrap.sh"
```

#### Configure the Amazon EMR Cluster

> Notes: If you created a cluster with the bootstrap action to configure the cluster to work with ZEPL, you can skip this step.

To configure the Amazon EMR cluster, you should [connect to the master node using SSH](https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-connect-master-node-ssh.html).

On the SSH console to the master node, type the following command to configure the cluster to work with ZEPL:

```sh
$ hadoop fs -get s3://zepl/emr/bootstrap.sh /usr/tmp/
$ chmod +x /usr/tmp/bootstrap.sh
$ /usr/tmp/bootstrap.sh
```

### Step 2: Create the Resource

To connect to the Amazon EMR from ZEPL, you should create the designated resource for Amazon EMR cluster.

#### To create new resource

1. Go to *Resources*, and click *New Resource*.
1. Enter the name for a new resource such as *EMR Resource*.
1. Select the image type corresponding to your EMR cluster.

You should select the image exactly corresponding with your EMR cluster. For more information, see [Docker Images Provided by ZEPL](#docker-images-provided-by-zepl).

#### Docker Images Provided by ZEPL

ZEPL manages the following Docker images that are available when creating the resources.

> Notes: If you do not find your image on this page, it most likely contains components that are not supported by ZEPL yet. Please contact ZEPL to get support for your configuration.

| EMR Release | Application Versions |
| --- | --- |
| 5.12.1 | Hadoop 2.8.3, Spark 2.2.1, Hive 2.3.2 |
| 5.14.0 | Hadoop 2.8.3, Spark 2.3.0, Hive 2.3.2 |

### Step 3: Create the Notebook

In ZEPL, create a new notebook and select the EMR resource which is created in the previous step. Once it is created, you should [configure the Spark interpreter](#configuring-spark-interpreter) to connect to the Amazon EMR cluster.

#### Configure Spark Interpreter

To connect to the Amazon EMR cluster from ZEPL, you need the public DNS name of the master node. You can [retrieve the master public DNS name](https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-connect-master-node-ssh.html#emr-connect-master-dns) using the Amazon EMR console and the AWS CLI.

In the notebook, you can configure the Spark interpreter by adding following paragraph:

```
%spark.config
EMR_MASTER_PUBLIC_DNS=ip-10-0-1-56.ap-northeast-1.compute.internal
```

> Notes: you should replace *ip-10-0-1-56.ap-northeast-1.compute.internal* with the public DNS name of the master node.

#### To access the data in Amazon S3

To access the data in [Amazon S3](https://aws.amazon.com/s3/), you should set the AWS access key ID and secret access key.

In the notebook, use following commands to set the AWS credentials:

```
%spark
sc.hadoopConfiguration.set("fs.s3a.access.key", "<AWS-ACCESS-KEY-ID>")
sc.hadoopConfiguration.set("fs.s3a.secret.key", "<AWS-SECRET-ACCESS-KEY>")
```

You should use `s3://` prefix to access the data in Amazon S3. For more information, see [Work with Storage and File Systems](https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-plan-file-systems.html).

## Managing Amazon EMR Clusters

Amazon EMR uses *YARN (Yet Another Resource Negotiator)*, which is a component introduced in Apache Hadoop 2.0 to centrally manage cluster resources for multiple data-processing frameworks.

For more information, see [View Web Interfaces Hosted on Amazon EMR Clusters](https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-web-interfaces.html).
