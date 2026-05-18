# What is OWASP?

**OWASP** stands for **Open Worldwide Application Security Project**. It's a non profit foundation that works to improve software security. Think of it as a free, open community that produces tools, documentation, and standards than anyone can use. The most famous thing OWASP produces is the OWASP Top 10 — a regularly updated list of the 10 most critical web application security risks. It's essentially the industry's "most wanted" list of vulnerabilities.

## A01:2025 — Broken Access Control
Access contols sometimes called authorization is how a web application grants access to content and functions to some users and not others. These checks are performed after authentication, and govern what ‘authorized’ users are allowed to do.

### How it emerges:
1. **Missing Server Side Checks**: A developer hides the "Delete User" button in the UI, but forgets to check on the server whether the person sending the delete request actually has admin rights. An attacker doesn't need the button — they can just send the request directly.
2. **Insecure Direct Object References (IDOR)**: Our profile URL is `example.com/user/1001`. What happens if we change 1001 to 1002? If the server doesn't verify that you own account 1002, you will see someone else's private data.
3. **Privilege Escalation**: It means a normal user trying to gain higher privileges. Example: If a form submission includes a hidden filed `role=user`. An attacker intercepts that with a tool like Burp suite and changes it to `role=admin` before sending it.
4. **JWT/Token manipulation**: Applications sometimes use tokens (like JWTs) that encode your role. If these tokens aren't properly signed or validated, an attacker can modify the payload — changing `"role": "user"` to `"role": "admin"`.

### How to Mitigate:
1.  Enforce checks on the server, always. Never trust the client. Every sensitive action must be verified on the server. It doesn't matter what the UI shows or hides.
2.  Deny by default. Your code should start from "deny everything" and then explicitly grant access. Never start from "allow everything" and try to block.
3.  Check ownership, not just login. For IDOR attacks, don't just check "is the user logged in?" — check "does this logged-in user own this resource?"
4.  Use proper role-based access control (RBAC). Define clear roles (user, moderator, admin) and enforce them consistently across every endpoint and function.
5.  Rate limiting and monitoring. If someone is hitting /user/1, /user/2, /user/3 rapidly, that's suspicious. Log and alert on unusual access patterns.
