<span class="header-font">Integration with S3</span>

In this section, we will explain how you can create a S3 of [Amazon Web Service](https://aws.amazon.com/) and seamlessly connect it with your [**S3 Bucket**](https://aws.amazon.com/s3/).

# Requirement for connecting ZEPL
To create a new S3 in ZEPL, ZEPL needs **Access key**, **Private key**, **Bucket** and **Region** information in your S3. If you don't know those information, If you don't have those information, You can refer the [AWS documentation](http://docs.aws.amazon.com/IAM/latest/UserGuide/introduction.html).

# Create S3 space in ZEPL
To create a new S3 space, click **Space** in the top of dropdown menu then you can see **Space** windows.

Select **S3** in dropdown menu in the popup and then type a space name with a short description.
And you need to fill the below fields such as your AWS credentials and S3 bucket information.

- AWS Access Key

- AWS Private Key 

- S3 Bucket name

- S3 Region 

The form should be similar as the picture bellow:

<img src="../img/create_new_s3.png" class="image-box big-img"/>

If the synchronization was successful, ZEPL will show your notebook list that your S3 bucket has.

<img src="../img/manage_s3.png" class="image-box big-img"/>
