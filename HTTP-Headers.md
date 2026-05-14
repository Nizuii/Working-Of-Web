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
