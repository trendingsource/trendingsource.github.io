---
layout: post
title: "Write Code and Develop Inside a Docker Container"
date:   2024-01-09 12:41:21 +0000
categories: "DevOps"
excerpt_image: https://learn.microsoft.com/en-us/dotnet/architecture/containerized-lifecycle/design-develop-containerized-apps/media/docker-apps-inner-loop-workflow/life-cycle-containerized-apps-docker-cli.png
image: https://learn.microsoft.com/en-us/dotnet/architecture/containerized-lifecycle/design-develop-containerized-apps/media/docker-apps-inner-loop-workflow/life-cycle-containerized-apps-docker-cli.png
---

### Containerized Development Is the Way to Go
Yes, it is highly recommended to do development inside Docker containers. Containers provide many advantages over traditional development methods. Containers are like virtual machines but much lighter and faster, allowing you to create development environments in seconds. You can have many dev environments running on the same machine without issues. Using containerized development enables **faster iteration cycles** and **uniform environments** across teams. 

![](https://learn.microsoft.com/en-us/dotnet/architecture/microservices/docker-application-development-process/media/docker-app-development-workflow/life-cycle-containerized-apps-docker-cli.png)
### Consistent and Isolated Environments for All Developers  
With containers, every developer gets an isolated Linux environment that is identical to their peers. This ensures no 'works on my machine' bugs and allows seamless integration. Images can be easily version controlled and reused. Teams get consistent environments without hassles of installing tools and dependencies on each local machine. **Portable development environments** eliminate environmental unknowns that often plague traditional development workflows.
### Try Changes Quickly with Docker Volumes
To persist data in containers across runs, Docker volumes can be leveraged. Volumes allow mounting host directories into the container or using network storage options like NFS. This provides persistence for databases, credentials, source code etc. Developers get instant feedback on code changes without having to rebuild images. With volumes, developers can **test iterations at blazing fast speeds** without sacrificing portability.
### Version Control At Your Fingertips  
For version control, lightweight container-based Git services like GitLab Runners eliminate the need to install Git servers. But self-hosted Git servers in containers work great too with persistent storage. Either route gives developers seamless Git access directly from their container shell without requiring network hops. This yields a **fully self-contained** and portable development workflow.
### Open-Source Container-Based IDEs Boost Efficiency 
For more advanced collaboration needs, clouds IDEs like Codenvy and Devspace provide on-demand containerized **virtual workspaces** on any infrastructure including bare metal, VMs and clouds. Teams can quickly provision sandboxes with full software stacks and collaboration tools. Workflow plugins, in-IDE terminals and browser-based UIs allow **maximizing developer productivity** in distributed teams.
### The Right Way is to Modfiy Container Images
While possible, modifying a running container's filesystem is not recommended. Containers are meant to be ephemeral - they run an immutable image. For changes, developers modify the Dockerfile, commit the changes and deploy the new image. This promotes **immutable infrastructure** for reproducibility and Rollbacks. Developers using a version controlled Dockerfile get **complete traceability** to changes over time.
### Dockerstreamlines Software Delivery
An established pattern with Docker is for the development container to build and pack the application into a deployment image. This deployment image is optimized to run in production without build tools etc. By leveraging Docker best practices at every stage from dev to production, teams gain productive **accelerated and streamlined workflows** for **rapid and reliable software delivery**.
 ![Write Code and Develop Inside a Docker Container](https://learn.microsoft.com/en-us/dotnet/architecture/containerized-lifecycle/design-develop-containerized-apps/media/docker-apps-inner-loop-workflow/life-cycle-containerized-apps-docker-cli.png)