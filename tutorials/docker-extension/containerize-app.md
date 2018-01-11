---
Order: 3
Area: docker
TOCTitle: Containerize the Application
PageTitle: Containerize the Application
MetaDescription: Node.js Deployment to Azure App Services with Visual Studio Code
DateApproved: 1/11/2018
---
# Containerize your Node.js Application

Next, use the Docker extension to add the necessary files to containerize your app, build the image, and push it to a registry.

> **Tip:** If you don't already have an app to containerize, follow this [Node.js tutorial](/docs/nodejs/nodejs-tutorial.md).

## Add the Docker files to workspace

Open the **Command Palette** (`kb(workbench.action.showCommands)`) and type `add docker files to workspace` to run the **Docker: Add docker files to workspace** command. This command will create the necessary Docker files. Choose your application type - **Node.js** in this tutorial - along with the port that your application listens on.

> **Tip:** Be sure that the port you select matches the port your app listens on. If you used the Express generator, set this to 8080.

This will add a `Dockerfile` along with some configuration files for Docker compose and a `.dockerignore`.

## Build a Docker image

The files you just added, specifically, `Dockerfile`, describe the environment for your app including the location of the source files and the command to start the app within a container.

> **Tip:** Container vs. image: a container is an instance of an image.

Open the **Command Palette** (`kb(workbench.action.showCommands)`) and run **Docker: Build Image** to build the image. Choose
the `Dockerfile` that was just created then give the image a name. It's important that you specify a couple of things here, the format is as follows:

`[registry or username]/[image name]:[tag]`

This tutorial uses the Azure Container Registry so for my example:

`fiveisprime.azurecr.io/myExpressApp:latest`

If you are using Docker Hub, use your Docker Hub username (for example, `fiveisprime/myExpressApp:latest`).

Once completed, the Output panel will open and the Docker command will be executed. This is a good way to get an understanding of the commands required to do the same steps directly from the terminal. You'll also see each step, or layer, that makes up the app environment.

Once built, the image will show up in the **DOCKER** explorer under **Images**.

![Docker Image](images/docker-extension/image-list.png)

## Push the image to a registry

Open the **Command Palette** (`kb(workbench.action.showCommands)`) and run **Docker: Push** and choose the image you just built to push the image to the registry. This will also execute the Docker command in the Output panel to show the status of the operation. Once completed, expand the **Images** node in the Docker extension explorer to see your image.

![Image in ACR](images/docker-extension/image-in-acr.png)

Next, you'll deploy your image to Azure.

----

<a class="tutorial-next-btn" href="/tutorials/docker-extension/deploy-container">I containerized my Node.js application</a> <a class="tutorial-feedback-btn" onclick="reportIssue('docker-extension', 'containerize-app')" href="javascript:void(0)">I ran into an issue</a>