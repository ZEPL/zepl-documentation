# FAQ

If you don't see your question in this FAQ, please send us an email at [support@zepl.com](mailto:support@zepl.com).

<br />

### Is ZEPL the enterprise version of Apache Zeppelin?
No. Though the people behind ZEPL are also the creators of Apache Zeppelin, ZEPL is a separate platform expanding upon what we started with Apache Zeppelin.
Zeppelin was created because we wanted something that could easily and quickly plug into various back-ends, and through it, do everything from data sourcing to visualization. 
But Zeppelin was created for the individual in a localized environment. But analytics is not a one person job. 
It's iterative and usually goes through multiple rounds of back and forth between different people. 
ZEPL is built this in mind. 
You can still analyze like a hero in ZEPL as you would in Zeppelin, but ZEPL also provid full enterprise collaborative features such as sharing, fine grained access control, team management, role based access control, discussions, comments, notifications, and many more. 
ZEPL is built for more than just analytics, it's a collaborative analytics platform for the modern age.

### Does ZEPL work with Jupyter notebooks?
Yes. You can import or sync Jupyter notebooks (currently supports only v4) stored in S3 or Github into ZEPL. 
Once in ZEPL, in addition to being able to view the notebook from any browser, you can clone the notebook, make edits, and execute the notebook directly from ZEPL.

### Can I use ZEPL and Apache Zeppelin together?
Yes. You can connect multiple Zeppelin instances to ZEPL. 
Simply click on Create Space and select Zeppelin in the dropdown. 
Once connected, all the notebooks in your Zeppelin instance will be sync-ed and available on ZEPL to view. 
At this point, you can clone, edit, and execute the notebooks, as well as share the notebooks once you're done.

### Can I use ZEPL and Jupyter together?
Yes. You can continue to use Jupyter in your local environment and sync and/or import the notebooks as desired. 
You can also export notebooks from ZEPL to be worked on from you local Jupyter or Zeppelin instance.

### How long do you save the notebooks?
The notebooks are saved until you delete them or delete your account.

### Can I save my notebooks in a different repository/storage of my choice?
All notebooks created on ZEPL are saved on ZEPL. You can export the notebooks to your preferred storage if you like.

### Can I connect ZEPL to more than one Apache Zeppelin instance?
Yes. You can connect to as many Apache Zeppelin instances as you like. 
You simply need to make sure that each Zeppelin is setup with its unique token which is provided when you create a Zeppelin instance Space in ZEPL.

### How can I use ZEPL on Apache Zeppelin running on EMR?
ZEPL enables close integration with Apache Zeppelin so you can setup Zeppelin in EMR and use ZEPL not only for sync-ing and backing up of your notebooks, but you can leverage ZEPL as the authentication portal for Zeppelin.
Details of how you can set this up can be found [here](https://www.zepl.com/spaces/S3pWITo5J/7a3f177ff7da4359938aea3a69d2ca73).

### Can ZEPL run on-premise, in a private infrastructure?**
Yes. We offer an Enterprise tier which has an on-premise version. 
Please contact us at [sales@zepl.com](mailto:sales@zepl.com) for more information.

### Can ZEPL run privately on an Amazon VPC?**
Yes. The same package for Enterprise on-premise can be use on a private VPC (Amazon's or other cloud).
Please contact us at [sales@zepl.com](mailto:sales@zepl.com) for more information.

### Can you create multiple organizations in ZEPL?**
Yes. The administrator has access to create one or more organizations under their ZEPL account.

### Can I share my notebooks to people who are not users of ZEPL?
Yes. You can directly share notebooks with non-registered users by simply putting their email address on the sharing option. 
Another option is to 'publish' your notebook. 
Publishing a notebook in ZEPL creates a public facing URL for the notebook which you can then send to anyone you like. 

### What levels of security do you have on ZEPL? For the notebooks and users?
We take security very seriously in ZEPL. Besides all transmissions being over SSL, all PII information is anonymized. 
In addition, all notebooks are encrypted on store with the encryption keys in a separate infrastructure.

### I have Jupyter and Zeppelin notebooks stored in Github. Can I import them to ZEPL? How?
Yes. ZEPL supports both Zeppelin and Jupyter notebooks (v4 currently). 
Simply click on create Space, select Github in the external repository option, enter your Github credentials, and watch all your notebooks sync in ZEPL. 

### If I set my notebook repository to my private S3 or Github, will my notebooks be saved in ZEPL as well?**
Yes. When you sync your notebooks in S3 and/or Github, a copy of your notebooks is also saved in ZEPL. 
In addition, if you make changes to your notebooks and save them on your private S3/Github repo, you can update these notebooks by simply clicking on "Synchronize".

### Can I read/import data from S3 to analyze in ZEPL?
Yes. Through python or scala, you can programmatically load data from S3 or other publicly available data source. 
We are also working on a more comprehensive data import feature. Keep a look out for it!

### What are the different roles available in ZEPL? What rights do each have?**
There are two levels of roles available in ZEPL:

1. Within Spaces, you can give members of that space different roles:

    i. **Member** - Has only access to notebooks within the Space

    ii. **Collaborator** - Above plus, can add/delete notebooks within the Space

    iii. **Manager** - Above plus, can add/remove members in the Space

2. If you're using organizations, when you invite team members, you can give each team member the following roles:

    i. **Member** - Only a participant

    ii. **Manager** - Have ability to add or delete other members. Can also add/delete Spaces within the organization even if not owner. 

    iii. **Admin** - All the manager rights as well as ability to add/delete notebooks even if not owner, and add/delete interpreter clusters.

### What’s the meaning of “Public notebook”? (e.g. publicly accessible for people having the link)
Public notebooks are notebooks that are 'published' through ZEPL and are accessible publicly through the URL.
You can make the notebook private again by toggling the "Published" button on the Publish pop-up.

### XTWhat are the notebooks in “Explore” showcases and how to manage it?
Notebooks in the Explore section are notebooks that were aggregated by us and some of our members. 
They include notebooks publicly published by various users--data scientists, professors, engineers, etc--as well as cover a wide range of topics--from How-Tos to research papers. 
Please take the time and [Explore](https://www.zepl.com/explore).

### What versions of Python, Scala, and Spark does ZEPL support?
Currently ZEPL supports Python.

### How can I load external Python libraries?
You can load external Python libraries by using the following command: ``%python.conda install libname``