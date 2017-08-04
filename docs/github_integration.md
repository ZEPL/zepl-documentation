<span class="header-font">Integration with Github</span>

In this section, we will explain how you can create a Github Space and synchronize your Github notebook.

# Create a space
Click on **New** on the navbar dropdown and click on **Space**.
The first step is to choose the **type** of your space. In this case we will choose **Github**.

<img src="../img/select_github_space.png" class="image-box" />

# Requirement for connecting a Github space

In order to connect to your Github repository, **ZEPL** needs a **Github personal access tokens**.

Go to [Github settings](https://github.com/settings/tokens) and follow the [Github documentation](https://help.github.com/articles/creating-a-personal-access-token-for-the-command-line/)

The **Repo scope** needed for ZEPL is **repo** like the picture below.

<img src="../img/github_generate_token.png" class="image-box big-img"/>


And you need to fill the below fields: Github credentials and repository information such as URL and branch name.

- Github Auth Token: **Paste** the Github access token that you generated in the previous section.

- Github URL: Is the **URL of your Github repository**. In our example we will take: [Apache Zeppelin Github Repository](https://github.com/apache/zeppelin).

- Branch name: ZEPL will use **master** by default, if you don't set other branch name.

- (Optional field) Folder to search notebooks: is the directory where your notebook are. In our example, [Apache Zeppelin Github Repository](https://github.com/apache/zeppelin) the notebooks are inside the **notebook folder**. So we will set it to **notebook**.

The form should be similar as the picture bellow:

<img src="../img/github_space_filled.png" class="image-box big-img"/>

You can now click on **Apply** to create your Github space. You will be redirected to the newly created space. 
The space will synchronize automatically your Github repository and will fetch the notebooks one by one.
And they will be displayed inside your space.

<img src="../img/github_space.png" class="image-box big-img"/>


You can also **manually retrigger** the synchronization of your Github space or it will be done automatically every 10 min.

You can now enjoy the power of **ZEPL** with your notebook store in **Github**.
