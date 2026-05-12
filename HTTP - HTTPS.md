# HTTP/HTTPS IN DETAIL.

## The Foundation: What is HTTP?

**HTTP - Hypertext Markup Language** is a set of rules that defines how messages are sent and recieved over the web. It works by sending the request from the client browser to the web server and recieving the response from the web server to client browser.

```bash
You (Browser)                        Web Server
     |                                    |
     |------- HTTP Request -------------->|
     |        "GET /index.html"           |
     |                                    |
     |<------ HTTP Response --------------|
     |        "200 OK + page content"     |
```
Everytime we visit a website, dozens of these request and response cycle happen in milliseconds.
