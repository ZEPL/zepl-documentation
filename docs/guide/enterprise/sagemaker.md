<h1> Integration with Amazon Sagemaker </h1>

Amazon [Sagemaker](!https://aws.amazon.com/sagemaker/) is a fully managed service for handling machine handling workflows. It enables users to build, train, and deploy ML models quickly. But before you can deploy your ML model, it must first be built, tuned, and iterated. Notebook, and specifically, Zepl notebooks are perfectly setup for these tasks.

Now you can use Zepl to directly connect to Sagemaker in your VPC simply by selecting the Sagemaker Resource available in Zepl.

Simply open a new notebook (or an existing notebook), and select Sagemaker in the resource drop down:
<img src="../../../img/sagemaker_resource.png" class="image-box big-img" />


That's it. Nothing else to install. From the notebook you can then do the following:

```python
%python
# from sagemaker import get_execution_role
from sagemaker.session import Session
from sagemaker import KMeans
import boto3

import pickle, gzip, numpy, urllib.request
import matplotlib.pyplot as plt

AWS_ACCESS_KEY_ID="[your_AWS_KEY_ID]"
AWS_SECRET_ACCESS_KEY="[your_AWS_SECRET_KEY]"
REGION_NAME = "[region_of_your_VPC]"

def get_boto3_session_with_credentials():
    return boto3.Session(aws_access_key_id=AWS_ACCESS_KEY_ID, aws_secret_access_key=AWS_SECRET_ACCESS_KEY,region_name=REGION_NAME)

# role = get_execution_role()
role = "[your_ARN_ROLE]"
session = Session(get_boto3_session_with_credentials())
bucket = session.default_bucket()

# your code goes below
```

As long as you have your AWS credentials setup correct, your model would be deployed to the Sagemaker service in your VPC.

In addition, the Zepl Sagemaker resource image is already pre-loaded with the following python libraries:

* boto3
* matplotlib
* numpy
* pandas
* pandasql
* Pillow
* scipy
* scikit-learn
* tensorflow
* bkzep
* statsmodels
* seaborn
* plotly
* bokeh
* pydot
* keras
* nltk
* gensim
* scrapy
* requests
* sagemaker

So you and your team should be able to start doing data science out of the box.

You can also create custom images for your organization using our [Custom Image Support](/guide/enterprise/custom_image_support.html) feature.

As always, if you have any questions, please don't hesitate to [contact us]((mailto:support@ZEPL.com)).
