<span class="header-font">Integration with Github</span>

In this section, we will explain how you can create a Github Space and synchronize your Github notebooks.

# Create a space
Click on **New** from the navbar dropdown and select **Space**.
Select the **Github** space **type** from the dropdown menu.

<img src="../img/select_github_space.png" class="image-box" />

# Requirement for connecting a Github space

In order for **ZEPL** to connect to your Github repository, you will need a **Github personal access token**.

Go to [Github settings](https://github.com/settings/tokens) and follow the [Github documentation](https://help.github.com/articles/creating-a-personal-access-token-for-the-command-line/)

The access scope that ZEPL requires is the **repo** scope, as is pictured below.

<img src="../img/github_generate_token.png" class="image-box big-img"/>


The following fields will need to be filled in: Github credentials, the repository URL, and the branch name.

- Github Auth Token: **Copy** the Github access token that you generated in the previous section.

- Github URL: Insert **URL of your Github repository**. In our example we will use [https://github.com/apache/zeppelin](https://github.com/apache/zeppelin)

- Branch name: Set the branch name. If no branch name is set, ZEPL will use the **master** branch by default.

- (Optional field) Folder to search notebooks: Zepl will recursively search this directory path for notebook files. If this field is not set, then Zepl will search from the repository's base path. In our example using [https://github.com/apache/zeppelin](https://github.com/apache/zeppelin) the notebooks are inside the **notebook** folder. So we will set this field to **notebook**.

In our example, the form would look similar to the image below.

<img src="../img/github_space_filled.png" class="image-box big-img"/>

You can now click on **Apply** to create your Github space. You will be redirected to the newly created space.
Zepl will connect automatically to your Github repository and fetch any notebook it finds.
The fetched notebooks should appear inside your space.

<img src="../img/github_space.png" class="image-box big-img"/>


The Github space will automatically re-sync every 10 mins and will add new notebooks, update any modified notebooks, and remove any deleted notebooks.  You can also **manually retrigger** the Github space synchronization.

You can now enjoy the power of **ZEPL** with your notebooks stored in **Github**.
