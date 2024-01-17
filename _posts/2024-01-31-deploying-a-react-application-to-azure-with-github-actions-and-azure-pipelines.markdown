---
layout: post
title: "Deploying a React Application to Azure with GitHub Actions and Azure Pipelines"
date:   2024-01-31 07:25:49 +0000
categories: "DevOps"
excerpt_image: https://i.ytimg.com/vi/FeSMRFkaRIU/maxresdefault.jpg
image: https://i.ytimg.com/vi/FeSMRFkaRIU/maxresdefault.jpg
---

Deploying modern JavaScript applications like those built with React to cloud platforms often requires some configuration and setup. In this guide, we will outline steps to deploy a React app to Microsoft Azure using both GitHub Actions and Azure Pipelines for continuous integration and deployment (CI/CD). 
## Setting up the React Application
The first step is to build our React app to produce optimized static files for production. The recommended way is to run `yarn build` or `npm build` which will generate production-ready optimized JavaScript and HTML bundled in a `/build` folder. 
### Packaging the App for Deployment  
For deployment, we need to package our built React app so it can be served from a production web server. A common approach is to containerize the app using **Docker**. We can create a simple Dockerfile that copies our built app inside a minimal container image. 

![](https://learn.microsoft.com/en-us/azure/architecture/example-scenario/apps/media/ci-cd-gitops-github-actions-aks-pull.png)
## Using GitHub Actions for CI/CD
GitHub Actions allows continuous integration and deployment directly from a GitHub repository. We can define automated workflows that will run on code changes to build, test and deploy our code.
### Configuring the GitHub Action Workflow
In the root of our GitHub repo, create a `.github/workflows/main.yml` file to define our CI workflow. The workflow will contain jobs to build our app, test it, and deploy it to Azure on pushes to main. 
### Defining the Build and Deploy Jobs
The build job runs `yarn build` to generate optimized static files. These are then packaged into a Docker image ready for deployment. The deploy job uses the GitHub context to authenticate with Azure and deploy the new container image to an Azure Web App.
## Using Azure Pipelines for CI/CD 
As an alternative to GitHub Actions, we can also use Azure Pipelines which is fully integrated with Azure services.
### Creating an Azure Pipeline
In the Azure Portal, navigate to the Pipelines section and create a new pipeline for our repository. Select the option to configure CI/CD with an Azure Repo.
### Defining Pipeline Stages  
Our pipeline will contain stages for continuous integration, containerization, and deployment. The CI stage runs tests during commits. Images are built and tested, then deployed continuously to Azure on merges to main.
By automating app builds, tests and deployments via GitHub Actions or Azure Pipelines, we ensure new code changes are validated and deployed quickly in a secure, scalable manner to Azure. This provides an optimal developer experience and reliable application deployments.
 ![Deploying a React Application to Azure with GitHub Actions and Azure Pipelines](https://i.ytimg.com/vi/FeSMRFkaRIU/maxresdefault.jpg)