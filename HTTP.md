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
