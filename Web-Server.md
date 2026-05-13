# Introduction to Web Server.

**Web Server** is a system that stores and delivers web content to users over the internet. Web server primarily uses HTTP or HTTPS protocols. An HTTP server (HTTP server is the software component on a web server that speaks HTTP(S) and handles the HTTP request/response cycle between clients (browsers or APIs) and the server’s files or applications.) specifically focuses on handling requests and responses between the client and the server. So basically:
- Web server requests to browser requests by sending web pages.
- HTTP server is a type of web server focused on HTTP communication.
- Some web servers support additional protocols beyond HTTP.

## Working

When a user enters a URL, the browser sends an HTTP request to the web server, which processes it and returns the required resources to display the page.  

<img width="800" height="188" alt="image" src="https://github.com/user-attachments/assets/71e1cb0a-9010-4205-95d4-9e748466b224" />

- **Client Request**: In the web browser the user enters a URL.
- **DNS Resolution**: The browser contacts a DNS server to obtain the IP address of the requested domain.
- **Establishing the connection**: Using the obtained IP address, the browser establishes a connection with the web server through TCP (TLS in the case of HTTPS)/
- **Sending HTTP request**: The browser sends an HTTP request to the server.
- **Processing Request**: The web server receives the request, processes it, and may interact with backend services or databases.
- **Serving the response**: The server sends back a response containing status codes and requested files (HTML, CSS, JavaScript, images).
- **Rendering the Web Page**: Based on the received data, the browser parses, executes scripts, and displays the web page to the user.

## Types of Web Servers.

### 1. Apache Web Server
Apache web server is a widely used open source web server developed by Apache Software Foundation. It is written in C, it is highly customizable, and distributed under the Apache License 2.0.
- It supports multiple OS (Windows, Linux, macOS).
- Allows advanced routing.
- Provides directory level configuration.

### 2. Nginx Web Server
Nginx is a high-performance web server known for speed, scalability and efficient handling of concurrent connections. It is also written in C.
- Designed to handle high traffic efficiently and serve static content.
- Functions as a reverse proxy and load balancer.
