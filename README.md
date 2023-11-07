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

### 3. Running a container with your custom HTML page

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

Run the command

```
docker build -t ubuntu-echo .
```

As long as you are within the directory that contains the Dockerfile (the . at the end of the command means "look in my current directory for the dockerfile) then the Docker build will kick in to action.

In the above command you created a docker image called **ubuntu-echo** - now let's have a look at your docker images

```
docker images
```

Using knowledge from the previous section, can you get the container running?

**💡 NOTE:** If you find that your terminal no longer works after running the container, simply close the terminal and open a new one.

**💡 HINT:** You should see the container start, print "Hello, World!" and then immediately stop.

### 7. A note on tagging

It is good practice to tag each new container build with a new version

Under the hood when you run the command

```
docker build -t ubuntu-echo .
```

Docker actually creates a tag called **latest** and associates it with that build, you can see this under the **TAG** column when you run `docker images`

Try updating the command from **Hello, world!!** to being something else and lets build a new version of the image

```
docker build -t ubuntu-echo:1.0 .
```

Notice in the above command you specify the tag after the image name in the format of `<image-name>:<image-tag>` such as `ubuntu-echo:1.0`

Then if you want to run that particular version you can run

```
docker run ubuntu-echo:1.0
```

### 8. Your own Node container

Remember that Node API that allowed you to add learners - now you are going to containerise it.

Within the [node-api](./node-api) directory you will find the code for the application and an [empty Dockerfile](./node-api/Dockerfile)

See if you can populate that Dockerfile in order to get your Node API running - you should be able to visit http://localhost:8080/health-check in order to view the health of the application.

**💡 HINT:** You should use the [Node official image](https://hub.docker.com/_/node) as your **Base Image** and have a look at the further reading for a guide that might help.

**💡 HINT:** Remember you will need to expose ports, the above example uses port 8080 which could be mapped to port 3000

**💡 HINT:** You will need a command to start the application, take a look at the **package.json** and in particular the **start** script - you'll need that command.

### 9. Docker multi-stage builds

In task 8 you might have found that your container builds the app, using `npm install` and then also runs it using `node src/index.js`

Have a look over Docker multistage builds as a way of separating building the application from running it.

[https://docs.docker.com/build/building/multi-stage/](https://docs.docker.com/build/building/multi-stage/)

## Submission Process

Given the nature of using the Docker tool, much of what you will be doing is running commands so as part of submitting you work you will complete the [SOLUTION.md](./SOLUTION.md) file so that it acts as a study guide for completing docker.

1. Fork this repository

2. Complete the [SOLUTION.md](./SOLUTION.md) file

3. Share your repository link as indicated

## Further reading

[Building a NodeJS app](https://nodejs.org/en/docs/guides/nodejs-docker-webapp)

[Docker multistage builds - NodeJS example](https://sachithsiriwardana.medium.com/dockerizing-nodejs-application-with-multi-stage-build-e30477ca572)
