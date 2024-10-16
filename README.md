
# Active Directory Group Policy, User Creation, and Account Management

## Lab Overview
This lab focuses on configuring Remote Desktop for non-administrative users, automating the creation of multiple user accounts, dealing with account lockouts, and enabling/disabling accounts within an Active Directory environment.

## Steps Performed

### Part 1: Setup Remote Desktop for Non-Administrative Users on Client-1

1. **Turn on VMs**  
   Using the **Azure Portal**, powered on the **DC-1** and **Client-1** virtual machines to begin the lab.

2. **Log into Client-1**  
   Logged into **Client-1** as the domain administrator `mydomain.com\jane_admin`.

3. **Configure Remote Desktop**  
   - Opened **System Properties**.
   - Clicked on the **Remote Desktop** tab.
   - Enabled **Remote Desktop** access for **Domain Users**.
   
   With this configuration, normal non-administrative users can now log into **Client-1** via Remote Desktop. This setup is useful for granting remote access to standard users without admin privileges.  
   
   _Note: In production environments, configuring Remote Desktop access for multiple machines would typically be done using Group Policy._

---

### Part 2: Create Multiple Users and Log into Client-1

1. **Log into DC-1**  
   Logged into **DC-1** as `mydomain.com\jane_admin`.

2. **Automate User Creation via PowerShell**  
   - Opened **PowerShell ISE** as an administrator.
   - Created a new script file and pasted in the PowerShell script to automate user creation.
   - Ran the script, which created multiple user accounts within the **_EMPLOYEES** Organizational Unit (OU).
   
   The accounts were successfully created and could be viewed in **Active Directory Users and Computers (ADUC)**.

3. **Test Login with a New User Account**  
   - Logged into **Client-1** using one of the newly created user accounts.
   - Verified that the login was successful and the account functioned correctly.  
   
   _Note: The password for each account was set within the PowerShell script._

---

### Part 3: Dealing with Account Lockouts

1. **Simulate an Account Lockout**  
   - Picked a random user account from the ones previously created.
   - Attempted to log into **Client-1** with an incorrect password 10 times, causing the account to lock out.

2. **Configure Group Policy for Account Lockout**  
   - Logged into **DC-1** and opened **Group Policy Management**.
   - Configured the **Account Lockout Threshold** to lock the account after 5 failed login attempts.

3. **Test Account Lockout Threshold**  
   - Attempted to log into **Client-1** with the same random user account and intentionally entered the wrong password 6 times.
   - Observed that the account was locked out after the 6th failed attempt, confirming that the Group Policy worked as expected.

4. **Unlock the Account and Reset the Password**  
   - Logged into **DC-1** as `jane_admin` and unlocked the user account in **Active Directory Users and Computers (ADUC)**.
   - Reset the user's password and verified that they could log in successfully.

---

### Part 4: Enabling and Disabling Accounts

1. **Disable a User Account**  
   - Disabled the same user account in **Active Directory**.
   - Attempted to log into **Client-1** with the disabled account and observed that the login failed with an error message.

2. **Re-enable the Account**  
   - Re-enabled the user account in **Active Directory**.
   - Attempted to log in again, and the user was successfully able to access **Client-1**.

---

### Part 5: Observing Logs

1. **Observe Domain Controller Logs**  
   Logged into **DC-1** and reviewed the **Event Viewer** logs for any failed login attempts, account lockouts, and other related security events.

2. **Observe Client-1 Logs**  
   Similarly, checked the **Event Viewer** logs on **Client-1** to ensure that login attempts and access errors were properly logged.

---

## Conclusion
This project demonstrated several key skills:
- Configuring Remote Desktop for non-administrative users.
- Automating user account creation using PowerShell.
- Configuring account lockout policies and managing locked accounts.
- Enabling and disabling user accounts in Active Directory.
- Monitoring event logs on both the domain controller and client machines.

By completing this lab, foundational skills in managing user access, security policies, and account management within an Active Directory environment were reinforced.


