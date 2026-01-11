# Challenge 2: Web Server Vulnerabilities

---

## Background / Scenario
You were hired to conduct a penetration test for a customer. As part of the assessment, you were required to identify vulnerabilities caused by web server misconfiguration. The objective was to exploit directory listing to locate sensitive files and retrieve the Challenge 2 code. Remediation techniques were then researched and proposed to prevent directory listing exploits.

---

## Instructions
In this challenge, you must find vulnerabilities on an HTTP server. Misconfiguration of the web server allowed directory listing, which enabled the viewing of files and subdirectories through a web browser. Using reconnaissance techniques, you were required to locate the Challenge 2 flag file stored in a vulnerable directory.

---

## Step 1: Preliminary Setup
- Logged into the server at `10.5.5.12` using the credentials `admin / password`
- Set the application security level to **Low**

<img width="1366" height="643" alt="challenge 2 pic 1" src="https://github.com/user-attachments/assets/dad42ace-649f-4ed1-bccc-19dc71ecd693" />

<img width="1366" height="643" alt="challenge 2 pic 2" src="https://github.com/user-attachments/assets/5aad4301-0a06-44a7-bdea-25915e08e29e" />


---

## Step 2: Identify Viewable Directories
- Performed reconnaissance with nikto on the web server to identify directories with indexing enabled
<img width="1366" height="643" alt="challenge 2 pic 3" src="https://github.com/user-attachments/assets/19e80e81-2d4c-44f4-9d83-99caead8d831" />
- Found the two viewable directories as **/config/** and **/docs/**                                                                                                                                                                                          
<img width="1366" height="643" alt="challenge 2 pic 4" src="https://github.com/user-attachments/assets/abbea289-63b1-4b9b-a821-2b558b6dadae" />

- Used a web browser and URL manipulation to confirm accessible directories
<img width="1366" height="643" alt="challenge 2 config dir" src="https://github.com/user-attachments/assets/72265454-6681-4444-bbce-414152e60f66" />

<img width="1366" height="643" alt="challenge 2 index for doc" src="https://github.com/user-attachments/assets/3cd02fa9-a4fa-4d76-9364-fb25cfbb4813" />

**Which directories can be accessed through a web browser to list their contents?**  
➡️ **Answer:**  
/config/                                                                                                                          
/docs/


---

## Step 3: Locate the Challenge 2 Flag File
- Created URLs to access viewable subdirectories
- Browsed directory contents to locate the file containing the Challenge 2 code

**In which two subdirectories can you look for the file?**  
➡️ **Answer:**  
db_form.html                                                                                                                                                                                                                                                            
DVWA_v1.3.pdf

**What is the filename with the Challenge 2 code?**  
➡️ **Answer:**  
db_form.html

**Which subdirectory held the file?**  
➡️ **Answer:**  
/config/

**What is the message contained in the flag file?**  
➡️ **Answer:**  
aWe-4975
 
<img width="1366" height="643" alt="challenge 2 message" src="https://github.com/user-attachments/assets/884f73ea-a59d-457e-9022-a3e5b5d531c1" />


---

## Step 4: Research and Propose Directory Listing Remediation
**What are two remediation methods for preventing directory listing exploits?**

➡️ **Answer:**
1. Disable Directory Listing on the Web Server
Configure the web server (e.g., Apache, Nginx, IIS) to disable directory indexing so that directory contents are not displayed when no index file is present.  
2. Implement Proper Access Controls and Permissions
Restrict access to sensitive directories using authentication and authorization controls, and ensure file system permissions prevent unauthorized viewing of directory contents.

---

## Conclusion
This challenge demonstrated how web server misconfigurations, such as enabled directory listing, can expose sensitive files and directories to unauthorized users.

---

## Disclaimer
This activity was conducted in a controlled lab environment for educational purposes only. Unauthorized penetration testing is illegal.

