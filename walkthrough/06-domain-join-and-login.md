# 06 — Windows 11 domain join and sign-in

The Windows 11 Pro client was joined to `homelab.test`. John Smith (`HOMELAB\jsmith`) successfully signed in. The screenshots below provide sign-in and account-context evidence; the precise join-wizard sequence is not captured in this selected set.

## Evidence and walkthrough

### 1. Domain sign-in verified using whoami

![Domain sign-in verified using whoami](../screenshots/06-domain-join/01-20261116-191210.png)

### 2. Local administrators group check on the Windows 11 client

![Local administrators group check on the Windows 11 client](../screenshots/06-domain-join/02-20261116-191404.png)

### 3. Windows 11 sign-in screen displaying John Smith

![Windows 11 sign-in screen displaying John Smith](../screenshots/06-domain-join/03-20261116-193730.png)

## Result

**Completed:** Windows 11 client joined to `homelab.test` and `HOMELAB\jsmith` logged in successfully.
