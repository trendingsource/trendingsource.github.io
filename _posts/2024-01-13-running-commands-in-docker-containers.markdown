---
layout: post
title: "Running Commands in Docker Containers"
date:   2024-01-13 13:01:12 +0000
categories: "Soccer"
excerpt_image: https://linuxhandbook.com/content/images/size/w600/2021/05/docker-container-lifecycle-diagram-2.png
image: https://linuxhandbook.com/content/images/size/w600/2021/05/docker-container-lifecycle-diagram-2.png
---

Docker containers allow users to isolate applications from one another as well as the underlying infrastructure. This feature makes it easy to deploy and manage applications, databases and microservices while keeping them separate. However, at times it is necessary to access a running container in order to perform commands, checks or troubleshooting. Docker provides multiple ways to do this.
### Checking Existing Containers
To see what containers are currently running on the system, use the `docker ps` command. This will show container IDs, names, image names and other details. For containers that have stopped or exited, use `docker ps -a` to see the full list including those not currently running. This is useful when trying to identify containers by name instead of ID. 
For example:
```
docker ps
```
Would show currently running containers while: 
```
docker ps -a
``` 
Shows all containers, started or not.

![](https://i.ytimg.com/vi/TdOLTlKsRd8/maxresdefault.jpg)
### Executing Commands in Running Containers
Once a container is identified, the `docker exec` command allows running additional processes inside it while it is running. This is useful for debugging, system tasks or installing additional software packages into images. 
The basic syntax is:
```
docker exec [OPTIONS] CONTAINER COMMAND [ARG...]
```
Where CONTAINER is the name or ID of the container and COMMAND is the process or executable to run inside it. Common options include `-it` to get an interactive shell.
For instance, to get a bash shell in a container called **"webserver"**:
```
docker exec -it webserver bash
```
Now any commands can be run directly within the context of that container. When exiting bash, the container continues running in the background.
### Running Commands During Container Startup
For executing a single command during container startup instead of running an interactive shell, use `docker run` instead of `exec`. 
The syntax is: 
```
docker run [OPTIONS] IMAGE [COMMAND] [ARG...]
```
Omitting the COMMAND will run the default entrypoint of the image. Including it allows overriding to run a single command and then exit.
For example, to ping Google DNS 10 times from a new Ubuntu container:
```
docker run -it ubuntu ping -c 10 8.8.8.8
```
This starts the container, runs the ping and then exits. Useful for running one-off commands without needing an interactive shell session.
### Inspecting Container Details 
The `docker inspect` command provides in-depth configuration and runtime details about containers. It outputs JSON which can be parsed to extract specific values.
For example:
```
docker inspect webserver
``` 
Would return all the low-level properties of the "webserver" container like networks, ports, volumes and more. This is helpful for troubleshooting container startup or connectivity issues.
### Container Resource Monitoring
To view system-wide container activity and resource usage, use `docker stats`. This displays a continuously updating output of CPU, memory, network and block I/O usage for all running containers.
Some key things it shows include:
- CPU % currently in use 
- Memory usage and limits
- Network receive and transmit rates
- Block input and output operations 
This helps monitor containers for performance bottlenecks, excessive resource consumption and more over time.
So in summary, Docker provides multiple ways to run commands and interact with containers running on the server through the `docker exec`, `docker run` and `docker inspect` commands while `docker ps` and `docker stats` assist with monitoring and troubleshooting. These features make managing applications and services very flexible.
 ![Running Commands in Docker Containers](https://linuxhandbook.com/content/images/size/w600/2021/05/docker-container-lifecycle-diagram-2.png)