---
layout: post
title: "Getting Started with Kubernetes on macOS"
date:   2024-03-02 08:18:32 +0000
categories: "Docker"
excerpt_image: https://matthewpalmer.net/kubernetes-app-developer/articles/minikube-mac.png
image: https://matthewpalmer.net/kubernetes-app-developer/articles/minikube-mac.png
---

## Installing Kubernetes Locally with Minikube
Minikube is one of the easiest ways to get started with Kubernetes on your local machine. It allows you to run a single-node Kubernetes cluster inside a virtual machine on macOS, Linux, or Windows. 
### Creating the Minikube VM
To install Minikube, first run `brew cask install minikube` if you have Homebrew installed. Then run `minikube start` to create and configure a virtual machine using VirtualBox. Minikube will download a Linux VM image, configure it, and start the VM. This process usually takes a few minutes.
Once Minikube has started, you can verify it is working by running `kubectl cluster-info`. This should output information about the Kubernetes API server endpoint Minikube is exposing.

![](http://caleb.cloud/assets/images/docker-cube-about.png)
### Interacting with Kubernetes Components
With Minikube running, you now have a fully functional Kubernetes cluster at your fingertips. You can interact with Kubernetes components like **Pods**, **Services**, and **Deployments** using the `kubectl` command line interface. 
For example, to deploy a sample application you can run `kubectl run hello-minikube --image=k8s.gcr.io/echoserver:1.4 --port=8080`. This will create a Pod running the EchoServer container. You can then expose the Pod to the host with `kubectl expose deployment hello-minikube --type=NodePort --port=30000` and access it at http://$(minikube ip):30000.
## Installing kubectl on macOS 
The kubectl CLI is required to interact with your Kubernetes cluster. You have a few options to install it on macOS.
### Installing with Homebrew 
If you have Homebrew installed, run `brew install kubectl` to download and install the latest version of kubectl.
### Installing from Binary 
Alternatively, you can download the macOS binary directly from the Kubernetes release page. For example:
```
curl -LO https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/darwin/amd64/kubectl
```
Make it executable with `chmod +x kubectl` and move it somewhere in your PATH like `/usr/local/bin`.
### Verifying the Installation
Regardless of your installation method, verify kubectl is working properly by checking the client version with `kubectl version`. You should see output indicating the installed kubectl version matches your Minikube cluster.
## Configuring kubectl Access
By default, kubectl is configured to access your locally running Minikube cluster. However, you may need to configure it explicitly.
### Setting the Context 
Run `minikube context` to view the current context. If needed, set it with `kubectl config use-context minikube`. 
### Finding the Kubernetes Configuration File
The Kubernetes configuration is stored in `~/.kube/config` by default. Edit this file if you need to modify cluster endpoints, certificates, or authenticate with different clusters.
### Enabling Shell Autocompletion
Shell autocompletion for kubectl can save you typing. Configure it by running `kubectl completion bash` and adding the output to your `.bash_profile`.
This covers the basics of installing Minikube and kubectl, and configuring access to your local Kubernetes cluster on macOS. From here you can start exploring additional Kubernetes components and building applications.
## Deploying Sample Applications 
With your Kubernetes development environment set up, it's time to deploy some sample applications and see Kubernetes in action.
### Deploying the Echo Server
As mentioned earlier, you can deploy the Echo Server sample app to test basic communication with your cluster. Run:
```
kubectl run echoserver --image=k8s.gcr.io/echoserver:1.4 --port=8080
kubectl expose deployment echoserver --type=NodePort --port=30000
```
Now point your browser to http://$(minikube ip):30000 to see it in action.
### Deploying the Guestbook Application 
The Guestbook application is a more realistic multi-tier web app deployment example in Kubernetes. It consists of a frontend PHP/Python app tier and a Redis backend database. 
Deploy it by running `kubectl apply -f https://k8s.io/examples/application/guestbook/all-in-one/guestbook-all-in-one.yaml`. Expose it to the host with `kubectl expose deployment guestbook-ui --type=NodePort --port=80` and view it at http://$(minikube ip).
### Scaling the Application
You can easily scale the number of replicas in Kubernetes. For example, to scale the Guestbook frontend to 3 replicas, run `kubectl scale deployment guestbook-ui --replicas=3`. Kubernetes will transparently upgrade the deployment to match the new replica count.
## Experimenting with Kubernetes Concepts
Now that you have sample apps deployed, dig deeper into core Kubernetes concepts:
### Workloads: Pods, Deployments, StatefulSets 
Explore different workload kinds like Pods, Deployments, StatefulSets and how they are used to manage applications on Kubernetes. For example, try updating a Deployment's container image to trigger a rolling update.
### Services and Networking
Learn how Services provide reliable access to Pods via ClusterIPs, NodePorts or LoadBalancers. See how Ingress integrates externally exposed Services with an ingress controller.
### ConfigMaps and Secrets
Use ConfigMaps to externalize configuration from containers and populate environment variables from Secrets safely. 
### Storage 
Try different storage types like emptyDir, PersistentVolumes and StatefulSets with Pod volumes. Use dynamic provisioning with StorageClasses.
### Security 
Experiment with Role-Based Access Control (RBAC), NetworkPolicies, Service Accounts and container security best practices like read-only filesystems and apparmor/selinux profiles.
This gives you a solid foundation in core Kubernetes concepts and primitives to deploy and manage production-grade applications on a single-node local dev cluster. From here you can start developing and deploying real applications on Minikube.
## Advancing Your Kubernetes Skills
Now that you understand the basics of Kubernetes and have hands-on experience with Minikube, here are some ways to further expand your skills:
### Multi-Node Clusters
For a more realistic environment, set up multi-node clusters with tools like kind, Docker Desktop swarm mode or MicroK8s. Manage cluster topology, multi-zone/region deployments and handle failover scenarios. 
### Operations Tasks
Automate operational tasks like cluster upgrades, scaling and disaster recovery using tools like kustomize, Helm and ArgoCD. Gain experience with cluster administration, monitoring and logging best practices.
### Cloud Deployments
Deploy to hosted Kubernetes offerings like Google Kubernetes Engine, AWS EKS and Azure AKS. Learn the differences between on-premises and managed Kubernetes environments. 
### Develop Applications
Build microservices applications on Kubernetes using best practices around 12-factor design, CI/CD pipelines, headless services, horizontal pod autoscaling and blue/green deployments. 
### Certifications
Earn professional credentials from CNCF like Certified Kubernetes Administrator (CKA) that validate your hands-on experience and understanding of Kubernetes technology.
This wraps up an introduction to getting started with Kubernetes on macOS using Minikube and kubectl. From here you have a solid foundation to either build applications or advance your Kubernetes skills further.
 ![Getting Started with Kubernetes on macOS](https://matthewpalmer.net/kubernetes-app-developer/articles/minikube-mac.png)