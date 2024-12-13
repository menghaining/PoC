**Affected Version**
Roller v6.1.2

**Description:**
When a user's password is changed, either by the user themselves or by an administrator, the current session does not expire as expected. This oversight allows the old session to remain active and usable, which is a CWE-613 insufficient session expiration weakness.

**Attack Vector:**
1. A user (e.g., user1) login in browser window tab1 and opens another tab (tab2) with the same session.
2. The user or an administrator changes the user's password.
3. Despite the password change, the user still has access to the website and can continue operations using the old session in window tab2.
