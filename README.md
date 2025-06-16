# Websockets

# Server

* A server is a system or program that provides services to other programs or clients over a network.
* It listens for incoming requests on a specified port and responds accordingly.
* Servers can handle multiple connections simultaneously, each through a separate socket.
* Common server types include HTTP servers, file servers, database servers, and application servers.

# Event Emission

* Event emission is a core concept in event-driven programming.
* It involves triggering (or "emitting") named events in response to certain actions or states.
* Other parts of the program can listen for these events and execute predefined callback functions.
* This model promotes asynchronous and non-blocking behavior in applications.

# HTTP (Hypertext Transfer Protocol)

* HTTP is a protocol used for transferring data over the web.
* It follows a client-server model where the client makes requests and the server returns responses.
* HTTP is stateless, meaning each request is independent and does not retain user session data.
* It uses standard methods like GET, POST, PUT, and DELETE for various types of operations.
* HTTP operates primarily over TCP (port 80 for HTTP and 443 for HTTPS).

---

# Polling : 
Polling is a technique where the client repeatedly sends requests to the server at regular intervals to check if there is new data.

**It is like asking the server:**
"Do you have anything new?"
every few seconds, even if nothing has changed.

# Types of Polling

- **Regular Polling** – Client sends requests at fixed time intervals (e.g., every 5 seconds).

- **Long Polling** – Client sends a request and the server waits until it has data to respond with. Once the response is received, the client immediately sends another request.

# Advantages of Polling
- Simple to implement	Works with standard HTTP. No special protocols needed.
- Reliable	Works on all browsers and servers.
- Firewall friendly	Uses normal HTTP ports, so it avoids common network issues.
- Control over frequency	You decide how often to poll, balancing speed vs. load.

# Disadvantages of Polling
- Inefficient	Most requests return "no new data", wasting bandwidth and server resources.
- Increased server load	Many clients polling frequently can overwhelm the server.
- Higher latency	Data may arrive late because the client has to wait until the next polling cycle.
- Not real-time	There’s always a delay between when the data is ready and when the client asks for it.


## In order to tackle this Websocket was introduced : 
# What is a WebSocket?
WebSocket is a communication protocol that provides full-duplex (two-way), persistent connections between a client (usually a browser) and a server over a single TCP connection.

It is commonly used when real-time communication is required—such as in chat apps, live notifications, multiplayer games, financial dashboards, etc.

# Websocket Flow : 
## 1. Persistent Connection
When using WebSockets, the client (usually a browser or app) sends a special HTTP request called a WebSocket handshake. The server agrees to this handshake and upgrades the connection to a WebSocket.

After this handshake, the connection stays open.

Unlike HTTP (which closes after each request/response), this connection does not close unless either the client or server explicitly does so.

This means both the client and server are continuously connected, and no need to reconnect or repeat handshakes for every message.

## 2. Data is Sent Only When Needed
After the connection is open:

The client does not need to repeatedly ask the server if there’s new data (unlike in polling).

The server can push data to the client as soon as something changes or becomes available.

Likewise:

The client can send data to the server at any moment — without waiting for a specific request-response pattern.

Example:
In Polling:
Client sends a request every 5 seconds to ask: “Do you have new chat messages?”

Server replies: “Nope”... repeatedly until a new message arrives.

**In WebSocket:**
Once connected:

When a new chat message is received by the server, it immediately pushes it to the client — without the client asking.

If the user types and sends a message, the client sends it through the open WebSocket instantly.





