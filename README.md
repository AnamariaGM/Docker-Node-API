# Docker

## Summary

Up to now you have utilised Amazon EC2 for deploying applications. 

You have provisioned instances and installed your applications on to the instance. You can think of this as a one to one mapping between instance and application.

As you know, instances have a cost 💰 for all the time they are running. 

What if we could run many different applications on an instance, such as a Python application, Node application, Java application etc all running on the same instance. 

This is where containerisation comes in and the most popular tool in containerisation technology is Docker.

## Prerequisites

You will need to make sure Docker has been installed on your computer in order to follow through the steps.

## Scenario

Throughout this exercise you will explore various aspects of the containerisation tool [Docker](https://www.docker.com/)

You will use Docker to build containers and also run them using Docker

## Instructions

## 1. Docker familiarisation

By now you should have Docker installed. If this is not the case then navigate to [Docker.com](https://www.docker.com/) in order to install Docker Desktop.

**🗒️ NOTE:** You do NOT need to have a Docker account or pay for anything when completing the exercises.

You will work with Docker over the remainder of the programme. For this step, familiarise yourself with the Docker commands

You can find a [handy cheatsheet on the Docker website](https://docs.docker.com/get-started/docker_cheatsheet.pdf)

Some of the commands might not be useful immediately until we create containers and run them, so once you have reviewed the cheet sheet and bookmarked it then move on to step 2.

## 2. Running a container

To run website based applications, developers will run them behind a web server. A popular web server is [NGINX](https://www.nginx.com/)

The Docker Hub has an [official NGINX Docker image](https://hub.docker.com/_/nginx), read through the Docker material and see if you can get the NGINX container running locally on your computer.

At this point just showing the regular NGINX "Welcome to nginx!" page is great

**💡 HINT:** In order to see the webpage in your browser you will need to **Expose an external port**

Once you have verified that you can see the NGINX homepage on your browser move on to step 3.

## 3. Running a container with your custom HTML page

Re-visiting the NGINX container, let's get it showing the HTML located within the [nginx-website](./nginx-website) directory.

Re-review the [official NGINX Docker image documentation](https://hub.docker.com/_/nginx) and see if you can get the container showing the index.html.

Once you have got your HTML page showing (instead of the default NGINX page) move on to Step 4.

## 4. Building containers

Now let's turn attention to building your own custom containers

Create a new directory called **echo-command-app** and within that directory create a file called **Dockerfile**

Add the following contents to the file

```
FROM ubuntu:22.10


CMD ["/usr/bin/echo", "Hello, World!"]
```

Now navigate to that directory and let's build the container

Using the Docker cheat sheet see if you can build that container.

If you run `docker images` and you can see your container listed then move on to step 5.

## 5. Running containers

Next, let's run the container. 

Explore the docker cheatsheet again and this time try to work out the correct command for running your container.

If you did not update the code above you should see the terminal display `Hello, World!` if you container successfully ran.

Before you move on to step 6, you might have noticed `latest` listed as the TAG. The tagging of images in docker is an important concept to understand and is how you will version your images. Have a [read over information around tagging](https://kodekloud.com/blog/docker-image-tag/).

Tag your docker image with the version `1.0.0`

Once you have got your container successfully running and tagged it with version 1.0.0 move on to step 6.

## 6. All together now...

Now it is time to create a brand new Docker image from scratch and get in running as a container 🙌

Within the [node-api](./node-api) directory you will find the code for the application and an [empty Dockerfile](./node-api/Dockerfile)

See if you can populate that Dockerfile in order to get your Node API running - you should be able to visit http://localhost:8080/health-check in order to view the health of the application.

If you are able to open up your browser and navigate to [http://localhost:8080/health-check](http://localhost:8080/health-check) to see the message **Server up and running** then you have completed this task! 

Great work on your first steps with Docker.

**💡 HINTS:** 

* You should use the [Node official image](https://hub.docker.com/_/node) as your **Base Image** and have a look at the further reading for a guide that might help.

* You will need to expose ports - look over the application code to see which port the application is listening on along with the link below for which port to bind to. You can then use this information and research how to expose ports in Docker. 

* You will need a command to start the application, take a look at the **package.json** and in particular the **start** script - you'll need that command.

## Conclusion

During this sprint, you have explored Docker as a tool for creating container images as well as running them. You have also begun those steps of becoming familiar with the various Docker commands.