---
layout: post
title: "Understanding Kubernetes Architecture and Managing Logs"
date:   2024-01-31 13:29:19 +0000
categories: "Tech"
excerpt_image: https://k21academy.com/wp-content/uploads/2020/06/Kubernetes_Architecture-1-2048x1211.png
image: https://k21academy.com/wp-content/uploads/2020/06/Kubernetes_Architecture-1-2048x1211.png
---

### Accessing Logs from Kubernetes Clusters
Logging is an essential part of managing any application deployed on Kubernetes. Being able to access and analyze logs helps troubleshoot issues and monitor application health and performance. **Kubernetes cluster logs containerized application logs** in an organized way to make them easy to retrieve and inspect.
There are a few main ways to access logs from applications running as pods on Kubernetes. The most direct method is using the **Kubectl logs** command which pulls logs from a specific pod. For example, `kubectl logs pod-name -n namespace` retrieves logs from the pod named "pod-name" in the specified namespace. 
You can also use the Kubernetes Dashboard which provides a visual interface for browsing and downloading logs from any pod in the cluster. Another option for large production clusters is to configure log aggregation using a central **log aggregation system like Elasticsearch or Splunk** which collects and indexes logs from all nodes and pods for advanced searching and analysis.

![](https://phoenixnap.com/kb/wp-content/uploads/2021/04/full-kubernetes-model-architecture.png)
### Understanding the Kubernetes Architecture 
The Kubernetes architecture follows a master-nodes model with control and data planes that help achieve scalability and fault tolerance. At the core is:
**ETCD** which acts as the cluster database storing all Kubernetes objects and their desired state. 
The **Kubernetes API Server** exposes the Kubernetes API and acts as the front end for all external communication with the cluster. 
The **Controller Manager** runs controllers that make desired state match actual state like replication controllers for deployments.
The **Scheduler** watches for newly created pods with no assigned node and selects the best suited node for running the pod based on resource availability and constraints.
These control plane components run on master nodes. **Worker nodes** run the applications containers and various pod infrastructure components like Docker to manage containers, the Kubelet to communicate with the API server, and kube-proxy for service load balancing.
### Components on the Kubernetes Master Node
The master node runs control plane components that handle centralized **cluster orchestration and management functionality**. Chief among these is the Kubernetes API Server which serves the Kubernetes API and acts as the front-end for the cluster handling all external interactions and requests. 
Other key components include the **ETCD database** which stores all cluster data and desired state, the **Controller Manager** that drives controllers to make actual state match desired state like replication controllers for deployments, and the **Scheduler** that selects nodes for running pods based on resource needs and constraints.
There is typically just **one master node** to coordinate the cluster, but multiple masters can be run for high availability using solutions like Kubernetes HAproxy. The master is critical and must remain highly **available and fault tolerant** for the cluster to function properly.
### Components on Kubernetes Worker Nodes 
Worker nodes are where the actual applications containers run. They have the following core components:
**Pods** which group one or more containers together to form deployable and manageable units that share volumes and network resources.
**Docker** (or other container runtimes) which manages image pulls, runs, stops, deletes containers forming each pod. 
**Kubelet** which is the primary node agent, communicating with the API Server to run, monitor, and restart pods and containers on the node based on configuration. 
**Kube-proxy** load balances requests to services across pods on the node, providing a virtual IP for service discovery.
Together these components allow pods to be reliably deployed and managed across a distributed infrastructure of worker nodes with the control plane coordinating orchestration.
### Inspecting Container Logs with Kubectl
The `kubectl logs` command provides a simple way to view logs from pods running on the Kubernetes cluster. You can see live container logs, troubleshoot issues or check application output.
To view logs from a specific pod called `myapp-pod`, use:
```
kubectl logs myapp-pod
``` 
To see only the last 10 lines, add the `--tail` flag: 
```
kubectl logs --tail=10 myapp-pod
```
You can also filter logs from a time period using `--since` in minutes, seconds or hours format like `--since=5m`. This helps view logs within a time window like the last 5 minutes.
`kubectl logs` offers flexible options for log viewing and troubleshooting pods deployed on Kubernetes.
 ![Understanding Kubernetes Architecture and Managing Logs](https://k21academy.com/wp-content/uploads/2020/06/Kubernetes_Architecture-1-2048x1211.png)