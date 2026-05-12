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
Everytime we visit a website, dozens of these request and response cycle happen in milliseconds. HTTP is text based that means every request and response are in readable plain text. HTTP is client-server that means clients always initiates the request. The default port of HTTP is 80. HTTP is stateless that means server remembers nothing between requests. This is how a raw HTTP request looks like:
```bash
GET /login HTTP/1.1
Host: example.com
User-Agent: Mozilla/5.0
Accept: text/html
```

And a response:
```bash
HTTP/1.1 200 OK
Content-Type: text/html
Content-Length: 1234

<html>...page content here...</html>
```
