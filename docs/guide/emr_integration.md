<h1>Integration with Amazon EMR</h1>

[Amazon EMR](https://aws.amazon.com/emr/) is a managed cluster platform that simplifies running big data frameworks, such as Apache Hadoop and Apache Spark, on AWS to process and analyze vast amounts of data.

> Important: This article applies to the [Enterprise plan](https://www.zepl.com/plans-and-pricing/) (with AWS Cloud) only. Please [contact us](mailto:sales@zepl.com) for more information.

There are two options when connecting ZEPL to AWS EMR clusters.
> Note: In both cases, the EMR cluster will have to reside on the same VPC as ZEPL.

### Option 1. Existing AWS EMR Clusters

ZEPL can connect to existing EMR clusters that your team has created through the AWS console. There are two requirements:

* The EMR cluster and the ZEPL deployment must be on the same VPC

* The EMR cluster must have a public resolvable domain name

To connect a ZEPL notebook to an existing EMR cluster:

1. Go to the `Resources` page on ZEPL and click on `Clusters` menu

2. On the `Clusters` page, click on `Create new Cluster`

3. Select the `Connect to an externally managed EMR cluster` and click `Next`
<img src="../../img/external_cluster_support/select_existing_cluster.png" class="image-box big-img"/>

4. Give the cluster a name and add the `Master public DNS` of the EMR cluster in the respective fields
<img src="../../img/external_cluster_support/set_public_dns.png" class="image-box big-img"/>

5. Once it's connected, you can go to any notebook, and on the `Notebook Settings`, select the cluster you just created
<img src="../../img/external_cluster_support/attach_note_to_cluster.png" class="image-box big-img"/>

> Note: Currently, ZEPL only supports EMR Release 5.14.0 version (more will be added in the future)


### Option 2. Create a new EMR Cluster

ZEPL also enables you to create a new EMR cluster through the ZEPL interface.
> Note: It is assumed that in the process of the ZEPL deployment, the ZEPL user IAM role has the credentials to create EMR clusters.

1. As the above, go to the "Resources" page on ZEPL and click on `Clusters` menu

2. On the `Clusters` page, click on "Create new Cluster"

3. Select the `Launch new ZEPL managed EMR cluster` and click `Next`

4. Give the cluster a name, give it an idle timeout (timeout where the cluster is shutdown), give it any additional configurations, select the Hardware configuration, and click "Create"
<img src="../../img/external_cluster_support/create_new_cluster.png" class="image-box big-img"/>

5. Again, once created, go to any notebook and select the cluster you just created.

> Note: The speed at which the new EMR cluster is created by AWS is dependent on AWS. This often take about 5 minutes.

### Manage Clusters

For all your cluster, you can manage them from the `Clusters` console.
<img src="../../img/external_cluster_support/clusters_menu.png" class="image-box big-img"/>

From here you can disconnect, shutdown, clone, and control access to these clusters to your organization members.
