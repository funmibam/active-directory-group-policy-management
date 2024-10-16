# Active Directory Security: NSGs, Account Lockouts, and Protocols Inspection

## Project Overview
This project involved configuring network security through Network Security Groups (NSGs), simulating account lockouts, and inspecting security logs within Active Directory (AD). Key activities included configuring account lockout policies, testing lockouts, and enabling/disabling accounts. Logs were observed to assess security operations in both the Domain Controller (DC) and client machine.

## Steps Performed

### 1. Network Security Groups (NSGs) and Inspecting Network Protocols

1. **Inspecting NSG Configuration**  
   Inspected the Network Security Groups (NSGs) associated with both the Domain Controller (DC-1) and Client-1 to ensure proper inbound and outbound rules for communication were in place.  
   
   ![Screenshot Placeholder: NSG Configuration](#)

2. **Testing Network Protocols**  
   Performed tests using different network protocols such as **ICMP** and **RDP** to ensure communication between DC-1 and Client-1 through the NSGs.

   ![Screenshot Placeholder: Network Protocol Testing](#)

### 2. Dealing with Account Lockouts

1. **Simulating a Bad Password Lockout**  
   Logged into **DC-1** and picked a random user account created earlier. Attempted to log in with incorrect passwords **10 times** to simulate a user lockout scenario.

   ![Screenshot Placeholder: Simulating Failed Login Attempts](#)

2. **Configuring Group Policy for Lockout Threshold**  
   Configured the Group Policy on DC-1 to **lock accounts after 5 failed login attempts**:
   - Used the **Group Policy Management Console (GPMC)** to modify the **Account Lockout Policy** in Active Directory.
   
   ![Screenshot Placeholder: Group Policy Configuration](#)

3. **Attempting Lockout**  
   After setting the policy, attempted to log in with the same user account **6 times** with incorrect passwords. As expected, the account was locked out after the 5th failed attempt.

   ![Screenshot Placeholder: Account Lockout in AD](#)

4. **Unlocking the Account**  
   Logged into **Active Directory Users and Computers (ADUC)** on DC-1 and unlocked the locked account. I then reset the user’s password and verified the account was functional by successfully logging in with the correct credentials.

   ![Screenshot Placeholder: Unlocking Account](#)

### 3. Enabling and Disabling Accounts

1. **Disabling a User Account**  
   Disabled the same user account in **Active Directory** using ADUC. Attempted to log in after disabling the account and observed the **error message** indicating that the account was disabled.

   ![Screenshot Placeholder: Disabling User Account](#)

2. **Re-enabling the User Account**  
   Re-enabled the account in ADUC and successfully logged in with the account, confirming that it was active again.

   ![Screenshot Placeholder: Re-enabling User Account](#)

### 4. Observing Logs

1. **Observing Logs in the Domain Controller (DC-1)**  
   Accessed the **Event Viewer** on DC-1 and examined logs related to **failed login attempts**, **account lockouts**, and **group policy changes**. Observing these logs provided valuable insights into the security operations of the domain.

   ![Screenshot Placeholder: DC-1 Event Viewer Logs](#)

2. **Observing Logs on Client-1**  
   Logged into Client-1 and used the **Event Viewer** to inspect logs pertaining to network communication and failed login attempts. These logs confirmed the network's response to the account lockout policies and other security measures.

   ![Screenshot Placeholder: Client-1 Event Viewer Logs](#)

---

## Conclusion
This project demonstrated essential Active Directory security operations such as account lockouts, enabling/disabling user accounts, and observing security logs. The project also showcased the use of Network Security Groups (NSGs) in Azure to control network communication and how to inspect related protocols.
