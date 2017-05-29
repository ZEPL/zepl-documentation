<span class="header-font">Sharing your Notebooks</span>

In this section, we will explain how you can create a new space and share Apache Zeppelin notebooks to communicate with your team members.

<br/>
# What is Space?

ZEPL Space is a kind of room for sharing notebooks. 
You can gather your own and shared notebooks shared from your team members efficiently in Space.
When you create a space, you can invite your team members. Only invited people can have an access permission to the shared notebooks.

You can find the list of Spaces in **Shared** page.

<img src="../img/shared_main.png" class="image-box big-img"/>

<br/>
# Create a new Space
To create a new Space, click **Space** in the dropdown menu, then type a Space name with short description. 

<img src="../img/create_new_space.png" class="image-box big-img"/>

Now you're an owner of this Space. You can invite collaborators and manage the shared notebooks in here.

<img src="../img/after_add_space.png" class="image-box big-img"/>

<br/ >
## Sharing Notebooks
Notebooks can be shared to a space or can be shared directly to another
user, or you can [publish the notebook](exploring_notebook.md) to the web.
<br />
You can share/ in **Spaces** main page.

<img src="../img/card_share_menu.png" class="card-img" />

Or you can find **Share and Publish** button in top-right corner of each notebook and directly do in it.
<br />

## More about sharing options
<img src="../img/sharing_dialog.png" class="image-box big-img"/>

<br />
While you are sharing your notebook to other users or to spaces, you can
configure three options:

**Permission**

* View - Allows others to only view the notebook
* Edit - Allows shared party to edit the notebook(If you share notebooks
with this option enabled, your interpreter will be used when the
notebook is executed)

**Format**

Same as three visual modes in Apache Zeppelin

* Default
* Simple
* Report

You can allow the shared party to access your notebooks only in the specified visual mode

**Version**

ZEPL can leverage the version control system as in Apache Zeppelin,
you can share a specific revision of your notebook with a user or a space

<br/>
# Publishing Notebooks to web

You can set your notebook to public or private mode in the same dialog used when you share a notebook.

<img src="../img/publish_dialog_initial.png" class="image-box big-img"/>

The default value of each notebook is **Unpublished**. It means the notebook is set as private mode.
So no one would be able to access the notebook, except the ZEPL users that it has been shared with, and public URI won't work in this status.

<img src="../img/publish_dialog.png" class="image-box big-img"/>

If you want to make your notebook public and anyone can access to it, just slide the toggle bar.
It will generate the public URL for the notebook. Just copy to the clipboard and visit the site.

Optionally you can select the showcase where your public notebook is located.
Of course you can choose multiple showcases at a time. If you have no idea about **Showcases** yet, please read [What is the showcase?](exploring_notebooks.md#what-is-the-showcase) section first. 
Then you can see your notebook under the showcase you chose in **Explore** tab. 


<br/>
# Inviting people to the Space
In the space, you can invite collaborators. Once someone is added to your space, he/ she can see your space in his **Shared** page.

<img src="../img/invite_people.png" class="image-box big-img"/>

<br/>
## User roles in space

While adding new members to space, you can decide what role they have in
your space. Each role will have specific powers over the space

* Manager: Manager of space can add or remove users, change user roles,
add or remove notebooks from space and view or edit notebooks that are
shared to the space

* Collaborator: Collaborator of a space can add or remove notebooks and
view or edit notebooks that are shared to the space

* Members: Members can only view or edit notebooks that are shared to
the space

<br/>

Give some feedback by leaving comments on the shared notebook.
You can find **conversation button** <img src="../img/conversation_button.png" class="button-img"/>at the top of the each paragraph and start a conversation with your people about the report.

<img src="../img/conversation.png" class="image-box big-img"/>
