# Docker Node API

## Overview
This repository contains the code for a Node.js API, along with a Dockerfile to containerize the application. Follow the instructions below to run the Docker image and verify the functionality of the Node API.


## Prerequisites
Ensure Docker is installed on your computer before proceeding with the steps.

## Instructions

### Running the Docker Image
1. Clone this repository to your local machine:
   ```bash
   git clone <repository_url>
   ```
2. Navigate to the node-api directory:
   ```bash
    cd node-api
   ```
3. Build the Docker image using the provided Dockerfile:
   ```bash
    docker build -t node-api .
   ```
4. Run the Docker container for the Node API, exposing port 8080:
   ```bash
    docker run -p 8080:8080 node-api
   ```


### Verifying the Functionality
1. Once the container is running, open your web browser and navigate to http://localhost:8080/health-check.
2. You should see the message "Server up and running", indicating that the Node API is functioning correctly.


