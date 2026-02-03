# Day-38-100-Days-challenge-in-cybersecurity-
# Day 38: Authorization Bypass & Privilege Escalation

## 📝 Project Overview
This module explores the mechanics of **Authorization Bypass** and how it serves as a primary vector for **Privilege Escalation** in web applications. It demonstrates how a breakdown in server-side logic allows a low-privileged user to perform administrative actions.

## 🔍 Key Concepts

### 1. Authentication vs. Authorization
- **Authentication:** Validating identity (e.g., "I am User A").
- **Authorization:** Validating permissions (e.g., "User A is allowed to delete records").
- **The Vulnerability:** The server confirms identity but skips the permission check for specific sensitive endpoints.

### 2. Common Exploit Vectors
* **Cookie/Header Manipulation:** Modifying plain-text roles (e.g., `isAdmin=true`).
* **Insecure Direct Object Reference (IDOR):** Changing a `user_id` parameter to target an administrative account.
* **Forced Browsing:** Directly accessing `/admin` or `/config` pages that lack middleware protection.

## 🛠️ The Exploit Path
1. **Discovery:** Mapping hidden administrative endpoints.
2. **Interception:** Capturing traffic via tools like **Burp Suite**.
3. **Tampering:** Modifying parameters to escalate privileges.
4. **Execution:** Successfully performing unauthorized actions.

## 🛡️ Mitigation Strategies (The Fix)
> **Golden Rule:** Never trust user-supplied input for authorization.

- **Server-Side Validation:** Always verify roles against a secure database session, not a client-side cookie.
- **Implement RBAC:** Use a strictly defined Role-Based Access Control system.
- **JWT Security:** If using tokens, ensure they are digitally signed and the `alg` header is restricted.

---
*Part of the 100 Days of Hacking Challenge.*
