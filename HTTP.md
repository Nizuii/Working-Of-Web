# HTTP in detail

HTTP is a protocol or set of rules used for communicating with web browsers for the transmitting of webpage data, whether that is HTML, Images, Videos, etc... HTTPS is the secure version of HTTP. HTTPS data is encrypted so it not only stops people from seeing the data you are recieving and sending, but it also gives you assurances that we are communicating to the web server and not any impersonating medium.

## What is a URL?
**URL** stands for **Uniform Resource Locator**. It's simply the address of something on the internet. Every single things online (a page, an image, an API endpoint, a file) has a URL. Lets break down the structure of the URL:

<img src="Images/url-anatomy.svg"> 

<table>
  <tr>
    <th>Part</th>
    <th>Example</th>
    <th>What it means</th>
  </tr>
  <tr>
    <td>Scheme</td>
    <td>https:// or http://</td>
    <td>How to communicate - encrypted or not.</td>
  </tr>
  <tr>
    <td>Subdomain</td>
    <td>api., www., admin.</td>
    <td>A sub section of the site.</td>
  </tr>
  <tr>
    <td>Domain</td>
    <td>github, google, instagram</td>
    <td>The websites name.</td>
  </tr>
  <tr>
    <td>TLD</td>
    <td>.com, .org, .in</td>
    <td>Top-Level domain</td>
  </tr>
  <tr>
    <td>Port</td>
    <td>:443, :80</td>
    <td>The door on the server to knock on.</td>
  </tr>
  <tr>
    <td>Path</td>
    <td>/user/profile</td>
    <td>Which specific resource we want</td>
  </tr>
  <tr>
    <td>Query</td>
    <td>?tab=repos&sort=asc</td>
    <td>Extra filters/parameters passed to server</td>
  </tr>
  <tr>
    <td>Fragment</td>
    <td>#pinned</td>
    <td>Jumps to a section on the page (never sent to server)</td>
  </tr>
</table>

## HTTP Request

When your browser wants anything from the server, it sends requests. The request has 3 parts:

### 1. Request Line

1. **The Request Line** - tells the server what action and which resource. Example:

```bash
POST /api/login HTTP/1.1
```

- `POST` = The method (action).
- `/api/login` = The path (which resource)
- `HTTP/1.1` = The protocol version

2. **The Headers** - Metadata about the request, like sticky notes on letter.

```bash
Host: github.com              ← which site (one server can host many)
Cookie: session=abc123        ← proof you are already logged in
Authorization: Bearer eyJ...  ← your identity token
User-Agent: Chrome/120        ← what browser you are
Content-Type: application/json ← what format the body is in
```

3. **The Body** - The actual data (Only in POST, PUT, PATCH - not GET)

```bash
{"username": "ali", "password": "secret123"}
```

