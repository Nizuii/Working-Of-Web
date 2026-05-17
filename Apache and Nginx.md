# Intoduction to Apache & Nginx.

Before diving into what apache and nginx is lets take a recap of what web server is. Imagine we open our browser and type `www.google.com`. Our browser is making a request like " Give me this page please". A web server is the software that answers this request, finds the right page and sends it back to our browser. Apache and Nginx are both web servers. They are different programs that does the same job but in different ways.

Lets compare both apache and nginx with a restaurant analogy.

<table>
  <tr>
    <th>Apache Server</th>
    <th>Nginx Server</th>
  </tr>
  <tr>
    <td>
      Apache assigns a dedicated waiter (a process/thread) to each customers the moment they walk in. The waiters stay with them the whole time even when the customer is just thinking about what to order.  
      Works great for small restaurants. Gets overwhelmed when 10,000 customers arrive at once. We would need 10,000 waiters. 
    </td>
    <td>
      Nginx uses a single fast manager who keeps an eye on all tables simultaneously. When a customer needs something, the manager quickly handles it and moves on to the next. No waiter is ever idle.  
      Built for massive crowds. 10,000 customers? The same manager handles them all efficiently.
    </td>
  </tr>
</table>

## What does each one actually does.

<img width="877" height="252" alt="image" src="https://github.com/user-attachments/assets/b5f2d256-5af1-46ce-96de-3864d6b70415" />

### Apache

- Born in 1995.
- It is widely used and have a lots of documentation.
- It can run PHP directly.
- It is slower under very high traffic.

### Nginx

- Born in 2004.
- Built to handle massive traffic efficiently.
- Extremely fast at serving static files
- Often used as a reverse proxy (traffic router)
- Lower memory usage under heavy load
