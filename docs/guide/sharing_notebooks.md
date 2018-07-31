# Sharing Notebooks

In this section, we will explain how you can create a new space and share notebooks to other users, teams.

# What is Space?

A ZEPL space is collection of notebooks where you can organization your notebooks by putting them into different spaces depending on the contents or people who work on. You can collaborate on space by inviting your coworkers or team and granting them permission.

<img src="../../img/shared_main.png" class="image-box big-img"/>

<br/>
# Create a new Space
Click **"New Space"** button in the main page to create a new Space.

<img src="../../img/create_new_space.png" class="image-box big-img"/>

And write a space name with short description.

**External Repository** is an option for the one who wants to load notebooks from external storages such as AWS S3, Github and Apache Zeppelin. See following links for the detailed information.

  * [How to connect to Apache Zeppelin](../zeppelin_integration)
  * [How to connect to Github](../github_integration)
  * [How to connect to S3](../s3_integration)

<br/ >
## Share Spaces and Notebooks
After creating new space, you can invite collaborators into space. You can share notebooks as well.
Normally space members should be able to access all notebooks that belongs to space, except for the case that notebook is shared to specific user or team.

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
* Custom Access - Have granular control over notebook by giving selective permission

**Version**(Notebook Share Only)

ZEPL can leverage the version control system as in Apache Zeppelin,
you can share a specific revision of your notebook with people

**Format**(Notebook Share Only)

You can allow the shared party to access the notebooks only in the specified visual mode
and ZEPL supports four different formats. (This is known as Look&Feel in Apache Zeppelin.)

* Default: Grey background notebook theme
* Simple: White background notebook theme with smaller paragraph padding
* Report: Display minimum number of icons and show them icons on mouse-over
* Juno: Jupyter like style


<br/>
# Publishing Notebooks to Web
You can share and [publish the notebook](exploring_notebook.md) in **Spaces** main page.
You can set your notebook to public or private mode in the same dialog used when you share a notebook.

The default value of each notebook is **Unpublished**. It means the notebook is set as private mode.
So no one would be able to access the notebook, except the ZEPL users that it has been shared with, and public URL won't work in this status.

<img src="../../img/publish_dialog.png" class="image-box big-img"/>

If you want to make your notebook public and allow anyone to access to it, just slide the toggle bar.
It will generate the public URL for the notebook. Copy to the clipboard and visit the site.

<br/>
