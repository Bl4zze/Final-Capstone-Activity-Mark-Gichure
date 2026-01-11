# Challenge 3: Exploit Open SMB Server Shares

---

## Background / Scenario
You were hired to conduct a penetration test for a customer. As part of the assessment, you were required to identify systems running SMB services, enumerate shared directories, and determine whether any shares were accessible without authentication. The objective was to locate the Challenge 3 code within an unsecured SMB share and propose remediation strategies to prevent unauthorized access.

---

## Instructions
In this challenge, you must discover if there are any unsecured shared directories located on an SMB server within the `10.5.5.0/24` network. Using reconnaissance and enumeration tools, you will identify anonymous-accessible SMB shares, access them, and retrieve the Challenge 3 flag file.

---

## Step 1: Scan for Potential Targets Running SMB
- Scanned the `10.5.5.0/24` network with nmap command **'nmap 10.5.5.0/24'** for hosts with open ports associated with SMB services and found the host 10.5.5.14 with ports 139 and 445 open. These ports are associated with SMB services.

**Which host on the 10.5.5.0/24 network has open ports indicating it is likely running SMB services?**  
➡️ **Answer:**  
10.5.5.14

<img width="1366" height="643" alt="challenge 3 nmap scan 2" src="https://github.com/user-attachments/assets/8b376a2a-d5df-403c-add9-f6b6a2a58e7e" />


---

## Step 2: Enumerate SMB Shares Accessible by Anonymous Users
- Enumerated SMB shares on the identified host using enum4linux with the command **enum4linux -S 10.5.5.14**
<img width="1366" height="643" alt="challenge 3 enum4linux scan 1" src="https://github.com/user-attachments/assets/358a63f0-f33e-4431-9afc-427e61c1beda" />

<img width="1366" height="643" alt="challenge 3 shares" src="https://github.com/user-attachments/assets/e2fbd7bd-795c-4c0b-b300-b86cf2e68926" />

- Determined which shares could be accessed without valid user credentials using the commad smbmap -H 10.5.5.14
<img width="1366" height="643" alt="challenge 3 smbmap command" src="https://github.com/user-attachments/assets/d5fb90e8-9c92-4860-b419-badd37f84dd5" />


**What shares are listed on the SMB server? Which ones are accessible without a valid user login?**  
➡️ **Answer:**  
homes                                                                                                                         workfiles
print$                                                                                                                      IPC$                                                                                                                                                                                                                                              

---

## Step 3: Locate and Retrieve the Challenge 3 File
- Accessed the SMB server using an SMB client
- Navigated through shared directories to locate the file containing the Challenge 3 code
- Downloaded and opened the file locally
<img width="1366" height="643" alt="challenge 3 print$ share" src="https://github.com/user-attachments/assets/6f5fcffd-c84e-47b8-9fb5-334ea565c4a7" />

**In which share is the file found?**  
➡️ **Answer:**  
print$

**What is the name of the file with the Challenge 3 code?**  
➡️ **Answer:**  
sxij42.txt

**What is the Challenge 3 code?**  
➡️ **Answer:**  
NWs39691

<img width="1366" height="643" alt="challenge 3 flag message" src="https://github.com/user-attachments/assets/b2ab3e0b-c5e1-4893-8645-61562b41157b" />


---

## Step 4: Research and Propose SMB Attack Remediation
**What are two remediation methods for preventing SMB servers from being accessed?**

➡️ **Answer:**
1. Disable Anonymous and Guest Access
Configure the SMB server to require authenticated users only, and disable anonymous or guest access to all shared directories.
2. Restrict Access Using Firewall Rules and Network Segmentation
Limit SMB access to trusted hosts and networks by blocking SMB ports (TCP 445/139) at the firewall and isolating SMB servers within restricted network segments. 

---

## Conclusion
This challenge demonstrated how unsecured SMB shares can expose sensitive files and allow unauthorized access when proper authentication and access controls are not enforced.

---

## Disclaimer
This activity was conducted in a controlled lab environment for educational purposes only. Unauthorized penetration testing is illegal.

