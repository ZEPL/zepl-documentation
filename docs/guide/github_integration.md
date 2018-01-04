<h1> Integration with Github </h1>

Github is one of the popular choices that data scientists prefer for
storing their notebooks. In this section, we will explain how you can
create a Github Space and synchronize your Github notebooks.

Note that files should be saved in **Apache Zeppelin(*.json)** or
**Ipython(*.ipynb)** format.

## Create a Github Repository Space
Click **"New Space"** button in the main page to create a new Space and check "External Repository".
Then select the **Github** from the dropdown menu.

<img src="../../img/select_github_space.png" class="image-box big-img" />

### Connecting to a Github Repository

In order for **ZEPL** to connect to your Github repository, you will need a **Github personal access tokens**.

Go to [Github settings](https://github.com/settings/tokens) and follow the [Github documentation](https://help.github.com/articles/creating-a-personal-access-token-for-the-command-line/)

The access scope that ZEPL requires is the **repo** scope, as is pictured below.

<img src="../../img/github_generate_token.png" class="image-box big-img"/>


The following fields will need to be filled in: the Github credentials, the repository URL, and the branch name.

<ul>
  <li>Github Auth Token: Copy the Github access token that you generated in the previous section.</li>

  <li>Github URL: Set the URL of your Github repository. In our example we will use: <strong>https://github.com/apache/zeppelin</strong>.</li>

  <li>Branch name: Set the branch name for the repo.  If no branch name is set, ZEPL will use the <strong>master</strong> branch by default.</li>

  <li id="github-path-guide">(Optional field) Base Path: ZEPL will recursively search this directory path for notebook files. If this field is not set, then ZEPL will search from the repository's root path. In our example repo <strong>https://github.com/apache/zeppelin</strong>, the notebooks are contained inside the notebook folder. So we can set this field to `notebook`.</li>
</ul>
In our example, the dialog form would look similar to the image below:

<img src="../../img/github_space_filled.png" class="image-box big-img"/>

You can now click on **Apply** to create your Github space. ZEPL will first test the connection to the Github repository. If the test succeeds, you will be redirected to the newly created space.
ZEPL will connect automatically to your Github repository and load any notebook it finds. The loaded notebooks should appear inside your repository space.

<img src="../../img/github_space.png" class="image-box big-img"/>

The Github space will automatically re-synchronize to the Github repository every 10 mins and will add new notebooks, update any modified notebooks, and remove any deleted notebooks. You can also manually retrigger the synchronization.

You can now enjoy the power of **ZEPL** with your notebooks store in **Github**.
