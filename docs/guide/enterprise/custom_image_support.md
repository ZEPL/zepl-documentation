## Custom Image Support

Zepl notebooks run in a container on the cloud. The particular environment that is used to run code on this container is stored as an image file, which ensures any analysis created in Zepl is reproducible on another container. This image file contains preinstalled libraries which are relevant to you and your team.

With custom image support, you are able to create an image for you and your organization to use with exactly the toolkit you need. You can pick the versions of programming languages / interpreters that are right for you and your team,  define the versions libraries that come preloaded for those interpreters, and set any system dependencies that you hope to refer to while programming in the notebook.

## SaaS Deployment - Custom Images

You don't need to be a DevOps professional to build an image. With our Custom Image editor, simply choose the interpreters that are important to you and your team and list out the libraries you hope to install. Within 30 minutes, you and your team will have a new image to try out when spinning up a container. 

[You can learn how to use custom images here.](https://docs.zepl.com/guide/enterprise/custom_image_saas)

## VPC Deployment - zcr Utility

Zepl provides a CLI tool called `zcr` to build custom interpreter images that you can use with notebooks in your enterprise deployment.

[You can learn how to use zcr here.](https://docs.zepl.com/guide/enterprise/custom_image_zcr/) 
