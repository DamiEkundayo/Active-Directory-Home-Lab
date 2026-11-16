# 07 — Group Policy: Control Panel restriction

**Objective:** Restrict access to Control Panel and PC Settings for the test user through a domain Group Policy Object. On `DC01`, created `TEST GPO`, linked it to `homelab.test`, and enabled **User Configuration → Policies → Administrative Templates → Control Panel → Prohibit access to Control Panel and PC settings**. The GPO was scoped for the test user; the initial test failed, and permissions were adjusted to permit policy processing.

## Evidence and walkthrough

### 1. TEST GPO linked to homelab.test and security filtering

![TEST GPO linked to homelab.test and security filtering](../screenshots/07-group-policy/01-20261116-192903.png)

### 2. Control Panel restriction policy enabled

![Control Panel restriction policy enabled](../screenshots/07-group-policy/02-20261116-192315.png)

### 3. gpupdate force succeeds for computer and user policies

![gpupdate force succeeds for computer and user policies](../screenshots/07-group-policy/03-20261116-194549.png)

### 4. Initial gpresult output: no user GPO applied

![Initial gpresult output: no user GPO applied](../screenshots/07-group-policy/04-20261116-195247.png)

### 5. Control Panel initially accessible: policy not yet enforced

![Control Panel initially accessible: policy not yet enforced](../screenshots/07-group-policy/05-20261116-201148.png)

### 6. GPO security permissions inspection

![GPO security permissions inspection](../screenshots/07-group-policy/06-20261116-201858.png)

### 7. Updated GPO security permissions for domain policy processing

![Updated GPO security permissions for domain policy processing](../screenshots/07-group-policy/07-20261116-202239.png)

### 8. Final gpresult shows TEST GPO under Applied Group Policy Objects

![Final gpresult shows TEST GPO under Applied Group Policy Objects](../screenshots/07-group-policy/08-20261116-202931.png)

### 9. Control Panel restriction confirmed with Windows Restrictions message

![Control Panel restriction confirmed with Windows Restrictions message](../screenshots/07-group-policy/09-20261116-203032.png)

## Result

**Completed and verified:** Following the security-permission change and policy refresh, `gpresult` listed **TEST GPO** as applied to `HOMELAB\jsmith`. Opening Control Panel displayed the Windows message: “This operation has been cancelled due to restrictions in effect on this computer. Please contact your system administrator.” This is evidence the custom restriction was enforced.
