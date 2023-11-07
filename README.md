# Docker

Up to now you have utilised Amazon EC2 for deploying applications. 

You have provisioned instances and installed your applications on to the instance. You can think of this as a one to one mapping between instance and application.

As you know, instances have a cost 💰 for all the time they are running. 

What if we could run many different applications on an instance, such as a Python application, Node application, Java application etc all running on the same instance. 

This is where containerisation comes in and the most popular tool in containerisation technology is Docker.

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
