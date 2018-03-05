<h1>Resources in ZEPL</h1>

A Resource must be attached to a ZEPL Notebook before it can be executed.
Resources in ZEPL determine which interpreters will be available and which and physical resources will be allocated to execute the notebook.

## Attach Resource to Notebook

You can select a resource when you create(or clone) a notebook. 

<img src="../../img/create_new_notebook.png" class="image-box big-img" />

You can also switch a notebook's attached resource after the notebook has been created through the "Notebook Settings" menu item (click gear icon in top-right side corner of the notebook).
Changing the attached resource will cause any running containers to be shutdown.

<img src="../../img/notebook_settings.png" class="image-box big-img" />

<br>

## Resource Management
<span class="note-font"> *NOTE* : Only an organization's admin can create and manage a resource  

Select the "Resources" menu item from the main menu (Click the avatar icon at top-right side of the corner).

### Create/Update Resource
ZEPL provides **Simple Workload** as a default resource. <br/>
Additional resources can be created to customize the capabilities and capacity of attached notebooks.

To create a new resource, Click "New Resource". The following form should appear.

<img src="../../img/new_resource.png" width="650px" class="image-box big-img" />

<br>

### Configuration

  - **Resource type**: Select the container size for the running notebook. Each resource type consumes hours units at different rates.
  - **Idle shutdown time**: Resource for a Notebook will shut-down automatically if the container is idle for the set amount of time
  - **Max concurrent running notebooks**: The maximum number of notebooks which can be attached to this resource at the same time
  - **Processing time limit**: A limit to the total time that this resource can run across all notebooks. It is useful to prevent over-consumption of resources and cap the associated fees. This is currently ignored.
  - **Default resource setting**: Set resource to be selected by default when you create(clone) a notebook 
  - **Image type**: Different image types provide different ZEPL interpreters. Currently there is only one image, but more will be added in the future.

You can update the resource settings by clicking its the name or by clicking on the menu item from the **Resources** main page.

<img src="../../img/resource_menu.png" width="180px" class="image-box small-img" />

You cannot change the container type or the image type after the resource is created.
Create new resource if you want a different container resource type and image type.
<br>
### Delete Resource

After a resource is deleted, all containers for that resource will be shutdown, and any notebooks that have the deleted resource attached will be set to the default resource.
If you're trying to remove **Default Resource**, the next available resource in the resource list will be set as the next default resource.

## Permissions for resources

Inside an organization, users share its resources. To control the usage of
resources in an organization, you can make use of resource permissions.
After the introduction of resource permissions users can attach resources
to notebooks and run them. View only and edit permissions set while sharing
notebooks can only be used to restrict editing of notebooks, they won't
restrict the execution of notebooks.

There are three different permissions which can be applied to users
or user groups such as team groups(members/ managers) or space user groups
(members/ collaborators / managers)

* Allow Attach, Detach Resource on a notebook
* Allow Start, Stop, Execute Resource
* Allow Modify Resource Setting

Please note that these permissions do not depend on each other or have
precedence over each other. You will have to be explicit on permissions.
A user who doesn't have attach permission still can have edit permission.
Also, giving permission to a specific user group doesn't give permission
to a higher user group. Example - giving edit permission to space users
doesn't give edit permission to managers of that space.

### Create a resource permission

* Initially, only resource admins can configure permissions to resources.
Later, users with edit permission would be able to do this.

<img src="../../img/resource-add-permission-button.png" class="image-box middle-img" />

* To add a permission, go to edit page of a resource and click
`add permission` button.

<img src="../../img/resource-permission-popup.png" class="image-box middle-img" />

* Fill the users or space or team name.

* If you choose space or team, select the specific user group
(managers/members) etc.

* Check the required permissions and click `Submit`.

### Edit or delete a resource permission

<img src="../../img/resource-permission-context-menu.png"
  class="image-box middle-img"
/>

You can use the context menu to edit or delete specific resource permissions.
