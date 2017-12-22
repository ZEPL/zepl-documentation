<h1>Resources in ZEPL</h1>

Need short explanation about key concepts of "Resource" in ZEPL

<br />

## Resource Management

<span class="note-font"> *NOTE* : Only admin of an organization can create/manage a resource  

Open user setting menu(Click the avatar icon at top-right side of the corner) and click "Resources".

### 1. Creation
ZEPL provides **Simple Workload** as a default resource. <br/>
But still you can create your own resource for your own usage.
Click "New Resource" then you'll see below creation form.

<img src="../../img/new_resource.png" width="650px" class="image-box big-img" />

### Configurations

  - **Resource type**: Each resource type consumes hours units at different rates
  - **Idle shutdown time**: If the idle time is over, the container will be shutdowned
  - **Max concurrent running notebooks**: The maximum number of notebooks which can be attached in the resource at the same time
  - **Processing time limit**: (please update)
  - **Default resource setting**: Set default resource which can be displayed as a top priority when you create(clone) a notebook 
  - **Image type**: Different image types provide different ZEPL interpreters

### 2. Update Configuration

You can update the resource settings by clicking its name in the list card.

<img src="../../img/resource_menu.png" width="180px" class="image-box small-img" />

Or "Change Setting" / "Set As Default" in the dropdown menu.

But please note that you can't change the container type in this step. 
Create new one if you want bigger/smaller resource type capacity. 

### 3. Deletion

Please make sure that after removing a resource, all containers attached to it will be shutdown and they will be moved to the default resource.
If you're trying to remove **Default Resource**, the first resource in the list will be the next default one.

## Resource with a Notebook

You can select a resource when you create(or clone) a notebook. 

<img src="../../img/create_new_notebook.png" class="image-box big-img" />

You can also switch the resource after the creation in "Notebook Settings" (click gear icon in top-right side corner of the notebook).
But please note that if the container is running, it will be shutdowned after switching.

<img src="../../img/notebook_settings.png" class="image-box big-img" />
