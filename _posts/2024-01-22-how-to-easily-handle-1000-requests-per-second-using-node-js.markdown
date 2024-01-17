---
layout: post
title: "How to Easily Handle 1000 Requests Per Second using Node.js"
date:   2024-01-22 13:34:54 +0000
categories: "Tech"
excerpt_image: https://tsh.io/wp-content/uploads/2019/09/concurrency-node-js-requests-per-second.png
image: https://tsh.io/wp-content/uploads/2019/09/concurrency-node-js-requests-per-second.png
---

With the rising popularity of Node.js and asynchronous programming, handling a large number of concurrent requests has become significantly easier compared to traditional synchronous frameworks like PHP. In this article, we will discuss how a simple "Hello World" Node.js app can handle thousands of requests per second (rps) even on a single core CPU. We will also explore scaling the app using clusters to maximize throughput.
### Maximizing Throughput with Event Loop and Callbacks 
Node.js is built on a single-threaded event loop model that processes asynchronous callbacks and events in a non-blocking way. This allows Node.js to efficiently handle multiple concurrent connections without creating a new thread for each request. When an I/O event like a HTTP request occurs, the callback for that event is added to the event queue. While that callback is processing, Node.js can continue accepting and queuing other requests. This allows Node.js to handle many connections with very few resources compared to multi-threaded systems.

![](https://i.stack.imgur.com/Gfhc4.png)
### A Simple "Hello World" App 
To demonstrate this asynchronous behavior, we can create a simple "Hello World" Express app:
```js
const express = require('express');
const app = express();
app.get('/', (req, res) => {
res.send('Hello World!');
});
app.listen(3000);
```
This app uses the Express framework to define a route that sends a "Hello World" response. Due to Node.js's asynchronous model, requests to this route will be processed concurrently without blocking.
### Load Testing with Apache Bench
To measure the throughput of this app, we can use the Apache Bench (ab) tool to simulate multiple concurrent requests. Running ab with -n 100000 to make 100,000 requests and -c 100 to use 100 concurrent connections:
```
ab -n 100000 -c 100 http://localhost:3000/
```
On a single core CPU, this can easily handle over 1000 requests per second (rps) even with such a basic app. The non-blocking model allows Node.js to maximize throughput.
### Increasing Throughput with Clustering
While a single process Node.js app can handle thousands of rps, we can further increase throughput using Node.js "clustering". Clustering takes advantage of all CPU cores by spawning child processes to handle the load. 
The master process listens for connections and distributes them across worker processes using round-robin load balancing. This allows us to maximize CPU utilization and handle significantly more concurrent connections.
### Load Balancing with Nginx
For true **large-scale applications**, we'll want to introduce an external load balancer like **Nginx** to further distribute the load across **multiple** Node.js **clusters** running on different machines. Nginx can handle the TCP connections and proxy requests to the Node.js clusters, providing **high availability** and allowing **horizontal scaling**.
By leveraging Node.js's asynchronous model and clustering capabilities, it's easy to build **highly scalable real-time** apps that can handle thousands of concurrent users. With external load balancing, these apps can scale to serve **millions** of requests per second on commodity hardware. This makes Node.js a powerful platform for building **low-latency** web services.
### Database Integration and Scalable Storage
While Node.js excels at **real-time** and **highly concurrent** request processing, **database operations** can still introduce blocking that limits overall throughput. Modern **NoSQL databases** like MongoDB are well-suited for asynchronous Node.js apps as they support **non-blocking drivers**. 
For **rapid reads and writes** of large amounts of **real-time** data, an in-memory distributed cache like **Redis** also pairs well. And for **petabyte-scale** datasets, a scalable **cloud storage service** like **S3** can provide **limitless storage capacity**.
By using the right databases and caches, a Node.js app's throughput can scale **near linearly** even with database access. And the app’s infrastructure can scale **horizontally on demand** using cloud computing resources.
### Building for Scale from Day One
When building applications for large scale usage, it's important to implement **scaling solutions** like clustering from the beginning. Tools like PM2 make it easy to run Node.js apps in cluster mode. And frameworks like **Koa** and **Express** support techniques like request load shedding out of the box.
Designing for and practicing **scalable patterns** early allows an application to easily expand as needs grow. It also prevents significant refactoring later. With Node.js, databases, and services optimized for concurrency, building **massively scalable systems** is easier than ever.

 ![How to Easily Handle 1000 Requests Per Second using Node.js](https://tsh.io/wp-content/uploads/2019/09/concurrency-node-js-requests-per-second.png)