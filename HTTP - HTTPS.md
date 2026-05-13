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
So imagine I am in a cafe connected to their Wi-Fi. I open `http://bank.com` and type my credentials. An unknown man on the same Wi-Fi is running a tool called WireShark. So he captures the network traffic and they might be able to capture my credentials.
```bash
POST /login HTTP/1.1
Host: bank.com

username=john&password=MySecret123
```
My password is in plain text and is readable by anyone. This is called a Man-in-the-Middle atatck. HTTP has zero protection against it. HTTPs was born to fix exactly this.

## What is HTTPS?

> **HTTPS = HTTP + TLS**

That's it. HTTPS is just regular HTTP, but wrapped inside an encryption layer called TLS. In HTTP the message is in plain text but in HTTPS the message is locked or encrypted. Ony the reciever will be able to decrypt it. The default port of HTTPS is 443. HTTPS not only encrypts the data, it also provides tamper proof, identity verification and padlock in browser.

### What is TLS?
**TLS (Transport Layer Security)** is the actual encryption protocol doing the heavy lifting inside HTTPS. TLS gives HTTPS 3 superpowers:
```bash
1. 🔒 ENCRYPTION    → No one can read your data mid-transit
2. 🔏 INTEGRITY     → No one can tamper with your data mid-transit  
3. 🪪 AUTHENTICATION → You're actually talking to the REAL server
```
Before any data flows, your browser and the server do a secret handshake to agree on encryption. Think of it like 2 spies meeting and agreeing on a secret code before talking.
```bash
Browser                                    Server
   |                                          |
   |——— 1. "Hello! I support these            |
   |        encryption methods..."  ————————> |
   |                                          |
   |<——— 2. "Cool! Let's use THIS method.     |
   |         Here's my Certificate" --------- |
   |                                          |
   |——— 3. Browser VERIFIES the certificate   |
   |    "Is this really Google? Let me check" |
   |                                          |
   |——— 4. Both sides generate a              |
   |        SHARED SECRET KEY   <———————————— |
   |                                          |
   |===== 5. All data now flows ENCRYPTED === |
```
### What is the Certificate?
When the server sends its certificate, it's basically showing us its ID card. It proves:
- This server really is `google.com`.
- A trusted authority verified this.
- It hasn't expired.
The certificate must be signed by **CA - Certificate Authority**. Lets think of CA as the passport offices of the internet. We cant make our own certificates and call it trusted.
```bash
Certificate Authority (e.g. DigiCert, Let's Encrypt)
         |
         | signs & vouches for
         ↓
   google.com's Certificate
         |
         | browser checks & trusts
         ↓
      Your Browser ✅
```

## HTTP Request Methods.
<table>
     <tr>
          <th>Method</th>
          <th>What it does</th>
          <th>Real world example</th>
     </tr>
     <tr>
          <td>GET</td>
          <td>Fetching data</td>
          <td>Opening a webpage</td>
     </tr>
     <tr>
          <td>POST</td>
          <td>Send data</td>
          <td>Submitting a form</td>
     </tr>
     <tr>
          <td>PUT</td>
          <td>Replace data completely</td>
          <td>Updating a profile</td>
     </tr>
     <tr>
          <td>PATCH</td>
          <td>Update data partially</td>
          <td>Changing just email</td>
     </tr>
     <tr>
          <td>DELETE</td>
          <td>Remove data</td>
          <td>Deleting an account</td>
     </tr>
     <tr>
          <td>HEAD</td>
          <td>GET but no body returned</td>
          <td>Checking if page exists</td>
     </tr>
     <tr>
          <td>OPTIONS</td>
          <td>Ask what methods are allowed</td>
          <td>Browser preflight</td>
     </tr>
     <tr>
          <td>TRACE</td>
          <td>Diagnostic echo</td>
          <td>Debugging</td>
     </tr>
</table>

### GET - The Fetcher

The HTTP GET method is the standard way a web client asks a server to send back a resource without changing anything on the server. Client asks for something, web browser sends a GET request that names the resource it wants (for example /index.html).
Raw GET request:
```bash
GET /users/42 HTTP/1.1 Host: api.example.com Accept: application/json (no body — GET never has one)
```
### POST - The Sender

POST sends data to the server. It is used for logins, forms, file uploads etc... It sends data to the server inside the request body hidden from the URL.
```bash
POST /login HTTP/1.1
Host: localhost
Content-Type: application/x-www-form-urlencoded

username=admin&password=Secret123
```
### PUT - The Replacer
PUT completely replaces the entire resource at a given URL. Think of it like overwriting a file completely. If put is unprotected the attacker can overwrite any data.
```bash
PUT /users/profile HTTP/1.1
Host: api.example.com

{"name": "John", "email": "new@email.com", "role": "admin"}
```
