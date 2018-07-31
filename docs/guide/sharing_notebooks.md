# Sharing Notebooks

In this section, we will explain how you can create a new space and share notebooks to other users and teams.

# What is Space?

A ZEPL space is a collection of notebooks. Users can be invited into a space and can be granted permission to share and collaborate on these notebooks.

<img src="../../img/shared_main.png" class="image-box big-img"/>

<br/>
# Create a new Space
Click **"New Space"** button in the main page to create a new Space.

<img src="../../img/create_new_space.png" class="image-box big-img"/>

Give your space a short description.

**External Repositories** are spaces where the contents of the space are synchronized from external storages or repositories. The sync-ed notebooks are read-only and cannot be run/executed in ZEPL (To run these notebooks in ZEPL, you can clone the notebooks, edit, and run in ZEPL). ZEPL supports synchronization from AWS S3, Github, and Apache Zeppelin. For more information, please use the following link.

  * [How to connect to Apache Zeppelin](../zeppelin_integration)
  * [How to connect to Github](../github_integration)
  * [How to connect to S3](../s3_integration)

<br/ >
## Share Spaces and Notebooks
After creating a new space, you can share the space with others and/or share a notebook into the space.
Members of a space are able to access all notebooks that belongs to the space.
Notebooks can also be shared directly to a user or a team.

<img src="../../img/sharing_overlay.png" class="image-box big-img" />
<br />

<br />
## Sharing Notebooks
ZEPL provides fine grained access control to notebooks you want to share with others.

<img src="../../img/sharing_option.png" class="image-box"/>
<br />

**Permission**

There are three preset permission policies - Full Read Access,
Full Collaborate Access, Full Manage Access - provided by ZEPL. You can choose
either one of them or you can grant your own custom permission set. One thing
you should note is that execution permission is coupled with resource, so to
grant execute permission, you should manage it in [resource menu](resource_mgmt/#permissions-for-resources).

* Full Read Access - Allows users to view the notebook, comment and react on it.
* Full Collaborate Access - Full Read Access plus ability to edit, schedule, version, and run notebook.
* Full Manage Access - Full Collaborate Access plus ability to manage the notebook like publish, share, remove notebook
* Custom Access - Have granular control over notebook

**Version**(Notebook Share Only)

You can share specific revisions of your notebook with others.

**Format**(Notebook Share Only)

ZEPL supports several different visual styles:

* Default: Grey background notebook theme
* Simple: White background notebook theme with smaller paragraph padding
* Report: Display minimum number of icons and show them icons on mouse-over
* Juno: Jupyter like style


<br/>
# Publishing Notebooks to Web
You can share and [publish the notebook](exploring_notebook.md) in **Spaces** main page. Publishing a notebook will automatically render the notebook public. You can set your notebook to public or private mode in the same dialog used when you share a notebook.

The default value of each notebook is **Unpublished**. It means the notebook is set as private.
No one will be able to access an Unpublished notebook, except for those ZEPL users who have access to the notebook through the above sharing mechanism.

<img src="../../img/publish_dialog.png" class="image-box big-img"/>

Toggling publish will generate a public URL for the notebook.
Anyone who has access to this URL will be able to view the notebook in read-only mode.

<br/>
