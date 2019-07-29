title: Data Science and Analytics | Zepl FAQ
description: See our FAQ page for answers to your data science and analytics questions. If you don't see your question in this FAQ please email us at support@zepl.com.
# FAQ

If you don't see your question in this FAQ please send us an email at [support@zepl.com](mailto:support@zepl.com).

### Is Zepl the enterprise version of Apache Zeppelin?

No. Though the people behind Zepl are also the creators of Apache Zeppelin, Zepl is a separate platform expanding upon what we started doing with Apache Zeppelin.
Zeppelin was created because we wanted something that could quickly and easily plug into various back-ends doing everything from data sourcing to visualization. But it was created for the individual in a localized environment. But analytics is not a one person job. It's iterative and usually goes through multiple rounds of back and forth between different people. Zepl is built this in mind.

In addition to the broad spectrum data science facilities and gorgeous charting you have in Zeppelin, Zepl  provides full enterprise collaborative features such as sharing, fine-grained, role-based access control, team management, comments, notifications, and much more. Zepl is built for more than just analytics. It's a collaborative analytics platform for the modern age.

### Does Zepl work with Jupyter notebooks?

Yes. You can import or sync Jupyter notebooks stored in S3 or Github into Zepl.
Once in Zepl, in addition to being able to view the notebook from any browser, you can clone the notebook, make edits, and execute the notebook directly within Zepl.

>Note: currently only Jupyter v4.x is supported

### Can I use Zepl and Apache Zeppelin together?

Yes. You can connect multiple Zeppelin instances to Zepl. Simply click on the *Create Space* button from the main page, toggle on *External Repository* and select Zeppelin from the dropdown menu that appears. All the notebooks in your Zeppelin instance will be sync-ed and available to view in the new Zepl *Space*. At this point you can clone, edit, execute and share the notebooks.

### Can I use Zepl and Jupyter together?

Yes. You can continue to use Jupyter in your local environment and sync and/or import the notebooks as desired.
You can also export notebooks from Zepl to be worked on from you local Jupyter or Zeppelin instance.

### How long are notebooks saved in Zepl?

The notebooks are saved until you delete them or delete your account.

### Can I save my notebooks in a different repository/storage of my choice?

All notebooks created in Zepl are stored in Zepl. You can export the notebooks to your preferred storage if you like.

### Can I connect Zepl to more than one Apache Zeppelin instance?

Yes. You can connect to as many Apache Zeppelin instances as you like.
You simply need to make sure that each Zeppelin instance is setup with its own unique token which is provided when you create a Zeppelin instance *Space* in Zepl.

### How can I use Zepl with Apache Zeppelin running on EMR?

Zepl enables close integration with Apache Zeppelin so you can setup Zeppelin in EMR and use Zepl not only for sync-ing and backing up your notebooks, but you can leverage Zepl as the authentication portal for Zeppelin.
Details on how you can set this up can be found [here](https://www.zepl.com/viewer/notebooks/bm90ZTovL21vb24vN2EzZjE3N2ZmN2RhNDM1OTkzOGFlYTNhNjlkMmNhNzMvbm90ZS5qc29u).

### Can Zepl run privately in an Amazon VPC?

Yes. Enterprise deployments currently only run in Amazon VPC's though other cloud solutions will be supported in the near future.

### Can you create multiple organizations in Zepl?

Yes. The administrator has access to create one or more organizations in their Zepl account.

### Can I share my notebooks with people who are not users of Zepl?

Yes. You can directly share notebooks with non-registered users by simply entering their email address in the notebook sharing window. Another option is to publish your notebook. Publishing a notebook in Zepl creates a public facing URL for the notebook which you can send to anyone you like.

### What level of security does Zepl offer both for notebooks and users?

We take security very seriously at Zepl. Besides all transmissions being over SSL, all notebooks are encrypted with the encryption keys in a separate infrastructure.

### I have Jupyter and Zeppelin notebooks stored in Github. Can I import them to Zepl?

Yes. Zepl supports both Zeppelin and Jupyter (v4.x) notebooks. Simply click on the *Create Space* button from the main page, toggle on *External Repository* and select GitHub from the dropdown menu that appears. Then enter your GitHub credentials. All the notebooks in your GitHub repo will be sync-ed and available to view in the new Zepl *Space*. At this point you can clone, edit, execute and share the notebooks.

### If I set my notebook repository to my private S3 or Github account when creating a new *Space* via an external repository, will my notebooks be saved in Zepl as well?

Yes. When you sync your notebooks from S3 or Github, copies of your notebooks are also saved in Zepl. In addition, if you make changes to your notebooks and save them in your private S3/Github repo, you can update these notebooks manually by clicking the *Synchronize repository* link in the top middle of the page. Otherwise Zepl sync's them behind the scenes every 10 minutes.

### Can I read/import data from S3 to analyze in Zepl?

Yes. Through Python and Scala you can programmatically access data from S3 or other publicly available data sources.

### What are the different roles available in Zepl? What rights does each have?

There are two levels of roles available in Zepl:

1. Within *Spaces* you can give members of that *Space* different roles:

    i. **Member** - only has access to notebooks within the *Space*

    ii. **Collaborator** - the above plus can add/delete notebooks within the *Space*

    iii. **Manager** - the above plus can add/remove members in the *Space*

2. When inviting team members to *Organizations* you can give each team member one of the following roles:

    i. **Member** - only a participant

    ii. **Manager** - has the ability to add/delete other members and *Spaces* within the *Organization* even if not the owner

    iii. **Admin** - all of the manager rights as well as the ability to add/delete both notebooks and interpreter clusters even if not the owner

### What does it mean for a notebook to be public (e.g. publicly accessible for people having the link)?

Public notebooks are notebooks that are published through Zepl and become accessible publicly through the generated URL. You can make the notebook private again by toggling the *Published* control off in the *Publish* dialog.

### What are the notebooks in the *Explore* showcases and how does one manage them?

Notebooks in the *Explore* section are notebooks that were aggregated by us and some of our members. They include notebooks publicly published by various users including data scientists, professors, engineers, etc. and cover a wide range of topics from How-Tos to research papers. Please take the time to [Explore](https://www.zepl.com/explore).

### Which versions of Python, Scala and Spark does Zepl support?

Currently Zepl supports:

- Python v2.7 & v3.5
- Spark v2.1.0
- Scala v2.11
- R v3.3.2

### How can I load external Python libraries?

You can load external Python libraries by using either of the followings commands in a notebook paragraph:

```
%python.conda install <libname>
```

```
%python
!pip install <libname>
```
