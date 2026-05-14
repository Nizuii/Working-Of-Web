# HTTP Headers - The Basics
Every time your browser talks to a website, it's sending and recieving HTTP messages. These messsages have 2 parts:
- **Headers**: metadata (Information about the message)
- **Body**: the actual content (HTML, JSON, Images, etc...)

Think of headers like the envelope on a letter, they tell the postal system (and the recipient) how to handle what's inside, before they even open it.

<img width="730" height="465" alt="image" src="https://github.com/user-attachments/assets/0330cab7-2990-4bda-b465-05e658da6e1c" />

## Types of HTTP Headers
Headers are grouped by their purpose. Here is what each type does:

- **Request Headers**: Sent by the browser to the server. They tell the server who you are and what you want. Examples: `Host`, `User-Agent`, `Accept`, `Cookie`, `Authorization`.  
- **Response Headers**: Sent by the server back to the browser. They tell the browser how to handle the response. Example: `content0type`, `set-cookie`, `location`.  
- **General Headers**: It can appear in both request and response.  
- **Security Headers**: A special category of response headers that tell the browser to enforce security protections.

## HTTP Security Headers.
A server can instruct the browser to enforce security rules by including certain headers in the response. If these headers are missing, attackers can exploit the browser itself against the users through XSS, clickjacking, protocol downgrader attacks and more. Think of security headers as the server saying "Heyy browser, here are the rules you must follow when displaying my content."

<img width="719" height="567" alt="image" src="https://github.com/user-attachments/assets/44ddbc7b-a478-4b78-9be0-341a596fe3de" />

- **Strict-Transport-Security (HSTS)**: Forces the browser to only connect over HTTPS. Even if a user types `http://`. This blocks SSL stripping attacks where a MITM downgrades the connection to plain HTTP.
- **Content-Security-Policy (CSP)**: The most powerful security header. It tells the browser exactly which sources of scripts, images and styles are allowed. If an attacker injects a <script> tag pointing to their evil server, CSP blocks it from running.
- **X-Frame-Options**: Prevents your page from being loaded inside an <iframe> on another site. Without this, an attacker can overlay an invisible iframe over a button on their page (clickjacking) and trick users into clicking something on your site without knowing.
- **X-Content-Type-Options: nosniff**: Stops the browser from "guessing" what type a file is. If a server says a file is text/plain but an attacker uploaded a .js file, some browsers would run it anyway (MIME sniffing). This header stops that.
