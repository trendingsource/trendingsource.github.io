---
layout: post
title: "Real-Time Communication with WebSockets in Python"
date:   2024-02-16 14:23:53 +0000
categories: "Programming"
excerpt_image: https://miro.medium.com/max/4480/1*sVniOf7_rWlz7tV-d25dbw.png
image: https://miro.medium.com/max/4480/1*sVniOf7_rWlz7tV-d25dbw.png
---

Websockets provide persistent connections between clients and servers, allowing for real-time communication outside of the traditional request-response model of the HTTP protocol. In this article, we'll explore how to leverage the websockets library in Python to build applications that support bidirectional communication.
## Establishing WebSocket Connections
The first step is to create a WebSocket server that can accept incoming connections. Using the **websockets** library, we can write an asynchronous function to handle each connection:
```python
import asyncio
import websockets
async def socket_handler(websocket):
async for message in websocket:
# handle incoming messages
await websocket.send("Message to client")
start_server = websockets.serve(socket_handler, "localhost", 8765)
asyncio.get_event_loop().run_until_complete(start_server)
asyncio.get_event_loop().run_forever()
```
This server listens on port 8765 for new WebSocket connections. For each connection, it runs the socket_handler coroutine which can send and receive messages.
To connect to this server from a client, we define another asynchronous function:
```python 
import websockets
async def connect():
async with websockets.connect("ws://localhost:8765") as websocket:
await websocket.send("Hello World!")
print(await websocket.recv())
asyncio.get_event_loop().run_until_complete(connect())
```
The `websockets.connect()` function handles establishing the WebSocket and yields the connection object.
### Sending and Receiving Messages
Once the connection is open, data can be sent between client and server by calling `await websocket.send(data)` and received with `await websocket.recv()`. The `async for` loop on the server side iterates over all incoming messages.
This basic ping-pong example demonstrates the core functionality of establishing a WebSocket connection and transmitting data in real-time. But in practice, applications would build on this to enable more complex interactions.

![](https://www.fullstackpython.com/img/visuals/websockets-flow-with-client-push.png)
## Building Distributed Applications
By integrating WebSocket support, entire distributed systems can be built where components communicate continuously. For instance, a real-time chat application may have:
- Chat server handling connections and broadcasting messages 
- Client applications updating live as new chats are received
- Presence service notifying when users come online/offline
Each component could be a independent Python process communicating over WebSocket. The chat server may handle hundreds of simultaneous user connections with low latency updates.
A **microservices architecture** is also possible, where independent services published over HTTP/JSON APIs can also exchange real-time data through dedicated WebSocket routes. This keeps HTTP for requests while WebSockets provide low-overhead pub/sub streaming.
Services like presence, status updates, activity feeds are well suited for real-time interactions. The ability to receive push notifications as they occur unlocks new types of collaborative and responsive applications.
### Scalable Server Architectures
For performance-critical servers handling many connections, it's useful to take advantage of Python's asynchronous nature. The built-in `asyncio` module provides scalable event loops that can efficiently multiplex I/O across thousands of sockets without blocking.
Some scaling techniques include:
- Run multiple independent process workers behind a load balancer like Nginx
- Gevent or uvicorn servers that spawn greenlets/threads to handle concurrent sockets  
- Database/ caching integration to avoid bottlenecks from high read/write loads
- GraphQL subscriptions protocol for publishing real-time data updates
With careful architecture and optimization, Python applications powered by websockets are capable of handling real-time interactions for very large user bases. Proper scaling ensures real-time responsiveness remains consistent as traffic grows over time.
### Client-Side Implementation 
On the client-side, asynchronous JavaScript APIs provide access to WebSockets in modern browsers. Frameworks like React, Vue, or Svelte make it easy to incorporate real-time functionality into user interfaces.
For example, in a React application we could:
- Open a WebSocket on component mount 
- Define state to hold received messages
- Dispatch actions on incoming data to update UI
- Call socket.send() on user interactions
This keeps the interface responsive as new information streams in without additional requests. Internal application state and orchestration is handled by the JavaScript runtime for rich interactive experiences.
Native desktop/mobile clients are also possible using platform-specific WebSocket libraries and interoperability with REST/GraphQL APIs. The Python server remains agnostic to the client implementation for a flexible full-stack solution.
In conclusion, websockets provide an indispensible building block for modern real-time applications. When combined with Python's asynchronous capabilities, complex distributed systems can be built to enable interactive experiences at any scale. The doors are opened to richer digital experiences through persistent live connections and data streams.
 ![Real-Time Communication with WebSockets in Python](https://miro.medium.com/max/4480/1*sVniOf7_rWlz7tV-d25dbw.png)