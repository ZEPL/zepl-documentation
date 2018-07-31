# Sharing Notebooks

In this section, we will explain how you can create a new space and share notebooks to other users and teams.

# What is Space?

A ZEPL space is a collection of notebooks. Users can be invited into a space and can be granted permission to share and collaborate on these notebook.

<img src="../../img/shared_main.png" class="image-box big-img"/>

<br/>
# Create a new Space
Click **"New Space"** button in the main page to create a new Space.

<img src="../../img/create_new_space.png" class="image-box big-img"/>

And write a space name with short description.

**External Repositories** are spaces where the contents of the space are synchronized from external storages or repositories. These notebooks are read-only and cannot be executed. ZEPL supports synchronization from AWS S3, Github and Apache Zeppelin. For more information, please use the following link.

  * [How to connect to Apache Zeppelin](../zeppelin_integration)
  * [How to connect to Github](../github_integration)
  * [How to connect to S3](../s3_integration)

<br/ >
## Share Spaces and Notebooks
After creating new space, you can share a space or a notebook to others.
Members of a space are able to access all notebooks that belongs to the space.
Notebooks can also be shared directly to a user or a team.

<img src="../../img/sharing_overlay.png" class="image-box big-img" />
<br />

<br />
## Sharing option
While you are sharing your space or notebook to other users,
you can configure three options.

<img src="../../img/sharing_option.png" class="image-box"/>
<br />

**Permission**

There are three preset permission policy - Full Read Access,
Full Collaborate Access, Full Manage Access - provided by ZEPL. You can choose
either one of them or you can grant your own custom permission set. One thing
you should note is that execution permission is coupled with resource, so to
grant execute permission, you should manage it in [resource menu](resource_mgmt/#permissions-for-resources).

* Full Read Access - Allows to view the notebook and comment and react on it.
* Full Collaborate Access - Grant permissions that is considered to be essential
for collaboration such as modify, schedule, version notebook, plus Full Read Access
* Full Manage Access - Allows to manage the notebook like publish, share, remove notebook,
plus Full Collaborate Access
* Custom Access - Have granular control over notebook

**Version**(Notebook Share Only)

ZEPL can leverage the version control system as in Apache Zeppelin,
You can share specific revisions of your notebook with others.

**Format**(Notebook Share Only)

Similar to Apache Zeppelin’s Look&Feel, ZEPL supports several different visual styles:

* Default: Grey background notebook theme
* Simple: White background notebook theme with smaller paragraph padding
* Report: Display minimum number of icons and show them icons on mouse-over
* Juno: Jupyter like style


<br/>
# Publishing Notebooks to Web
You can share and [publish the notebook](exploring_notebook.md) in **Spaces** main page.
You can set your notebook to public or private mode in the same dialog used when you share a notebook.

The default value of each notebook is **Unpublished**. It means the notebook is set as private mode.
No one will be able to access an Unpublished notebook, expect for those ZEPL users who have access to the notebook through sharing or a space.

<img src="../../img/publish_dialog.png" class="image-box big-img"/>

Toggling publish will generate a public URL for the notebook.
Anyone who has access to this URL will be able to view the notebook in read-only mode.

<br/>
