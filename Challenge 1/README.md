# Challenge 1: SQL Injection


---

## Background / Scenario
You were hired to conduct a penetration test for a customer. As part of the assessment, you were required to identify SQL Injection vulnerabilities, extract user credentials, crack a user password, gain authenticated access to a remote system, and retrieve the Challenge 1 code. Remediation strategies were then researched and proposed to prevent future SQL Injection attacks.

---

## Instructions
In this challenge, you must discover user account information on a server and crack the password of Bob Smith’s account. You will then locate the file that contains the Challenge 1 code and use Bob Smith’s account credentials to open the file located at `192.168.0.10` to view its contents.

---

## Step 1: Preliminary Setup
- Opened a web browser and navigated to `10.5.5.12`
- Logged in using the credentials `admin / password`
<img width="1366" height="643" alt="VirtualBox_Ethical-Hacker-Kali_10_01_2026_20_29_14" src="https://github.com/user-attachments/assets/3c2115b5-1917-43d0-b3df-ad0c2a922567" />

- Set the DVWA security level to **Low** and submitted the changes

 
<img width="1366" height="643" alt="VirtualBox_Ethical-Hacker-Kali_10_01_2026_20_30_46" src="https://github.com/user-attachments/assets/3134d562-f754-429f-8619-05266cb9c7a9" />


---

## Step 2: Retrieve the User Credentials for Bob Smith’s Account
- Identified the database table containing usernames and password hashes with command **1' UNION SELECT table_name, table_schema 
FROM information_schema.tables 
WHERE table_schema=database()-- -**
<img width="1366" height="643" alt="payload 1 revamped" src="https://github.com/user-attachments/assets/974a4a0c-5561-4188-a24f-8272fe815996" />

- Located a vulnerable input form that allowed SQL Injection
- Injected SQL commands to retrieve Bob Smith’s username and password hash with the payload 1' UNION SELECT user, password FROM users#

<img width="1366" height="643" alt="payload 2 revamped" src="https://github.com/user-attachments/assets/35ffd34d-afbb-4492-a366-1dd0b2ae329e" />


---

## Step 3: Crack Bob Smith’s Account Password
- Saved the retrieved password hash which was **5f4dcc3b5aa765d61d8327deb882cf99** locally
- Used https://crackstation.net to crack the password hash

**What is the password of Bob Smith’s account?**  
➡️ **Answer:**  
password
 
<img width="1919" height="891" alt="Screenshot 2026-01-11 083743" src="https://github.com/user-attachments/assets/c91879bb-df77-47f0-a54d-9b8a747aea91" />


---

## Step 4: Locate and Open the File with the Challenge 1 Code
- Logged into `192.168.0.10` with ssh using Bob Smith’s credentials
<img width="808" height="250" alt="logged in as bob smith with ssh" src="https://github.com/user-attachments/assets/757a71b9-fd0b-4fc8-b573-980f1462b770" />

- Navigated to the user’s home directory
- Located and opened the file containing the Challenge 1 code

**What is the name of the file with the code?**  
➡️ **Answer:**  
my_passwords.txt

**What is the message contained in the file?**  
➡️ **Answer:**  
8748wf8j
 
<img width="1366" height="643" alt="flag for the challenge" src="https://github.com/user-attachments/assets/33d0f16d-d21c-4ed3-b7af-84d2fb11ded3" />


---

## Step 5: Research and Propose SQL Injection Remediation
**What are five remediation methods for preventing SQL Injection exploits?**

➡️ **Answer:**
1. Use Prepared Statements (Parameterized Queries)
Ensure all database queries use prepared statements so user input is treated strictly as data and not executable SQL code. 
2. Implement Server-Side Input Validation
Validate and sanitize all user inputs on the server side by enforcing strict data types, formats, and length restrictions.
3. Use Stored Procedures Securely
When stored procedures are used, ensure they do not dynamically build SQL queries with user input. 
4. Apply Least Privilege to Database Accounts
Configure database users with the minimum permissions required, limiting the impact of a successful injection attack. 
5. Use Web Application Firewalls (WAFs)
Deploy a WAF to detect and block common SQL Injection patterns before they reach the application. 

---

## Conclusion
This challenge demonstrated how SQL Injection vulnerabilities can be exploited to extract sensitive data, compromise user accounts, and gain unauthorized system access if proper security controls are not implemented.

---

## Disclaimer
This activity was conducted in a controlled lab environment for educational purposes only. Unauthorized penetration testing is illegal.
