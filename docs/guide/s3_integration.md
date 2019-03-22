# Integrating with *S3*

*S3* is a popular online data storage service offered by AWS and used by many data scientists to store their notebooks whether they be Zeppelin or Jupyter. Zepl supports integration of both notebook types via *Spaces* as described below. Note that the files in *S3* must be in *JSON* (Apache Zeppelin) or *ipynb* (Jupyter) format.

>Note: *S3* synchronization is unidirectional from *S3* to Zepl so edits in Zepl do not get updated in *S3*. Also the notebooks from *S3* are read-only in Zepl and need to be cloned to modify.

In this section, we will explain how you can create an [Amazon Web Service](https://aws.amazon.com/) *S3* *Space* in Zepl and seamlessly synchronize your notebooks from your own [*S3* bucket](https://aws.amazon.com/S3/).

## Creating an AWS *S3* Repository Space

Click the *New Space* button in the main page to create a new *Space* and fill in the name and description fields. Then check *External Repository* and select *S3* from the dropdown menu. In order for Zepl to connect to your *S3* repository, you will need to enter your *Access key* *Private key*, *Bucket* and *Region*. If you are unaware of how to find and retrieve this information, you can refer to the [AWS documentation](http://docs.aws.amazon.com/IAM/latest/UserGuide/introduction.html).

A completed form might look like the following image.

<img src="../../img/create_new_*S3*.png" class="image-box big-img"/>

If the synchronization is successful, the notebooks in your *S3* bucket should be automatically added to your Zepl *S3* Space.

<img src="../../img/manage_*S3*.png" class="image-box big-img"/>

The *S3* space will automatically synchronize with the *S3* repository every 10 mins and will add new notebooks, update any modified notebooks, and remove any deleted notebooks. You can also manually re-trigger the synchronization.
