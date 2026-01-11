# Challenge 4: Analyze a PCAP File

---

## Instructions
A PCAP file captured during reconnaissance was analyzed to identify sensitive information transmitted in clear text. The Challenge 4 flag was retrieved by inspecting network traffic.

---

## Step 1: Analyze the PCAP File
- Opened `SA.pcap` in Wireshark
<img width="1366" height="643" alt="challenge 4 SA pcap wireshark" src="https://github.com/user-attachments/assets/e8543573-09f4-4e72-98c2-cae6cbedb1df" />

- Identified the target IP address as 10.5.5.11 and explored the http packets to identify exposed directories

<img width="1366" height="643" alt="challenge 4 ip of target" src="https://github.com/user-attachments/assets/7844f664-0bef-4131-9c83-de54ff134f37" />

- Found the paths **10.5.5.11/database-offline.php/, 10.5.5.11/data/ and 10.5.5.11/test/** in the http packets
<img width="1366" height="643" alt="challenge 4 http database" src="https://github.com/user-attachments/assets/7820a8e5-2e4f-4b52-a6a1-e1b75307bcd3" />

<img width="1366" height="643" alt="challenge 4 wireshark data directory" src="https://github.com/user-attachments/assets/b5905aeb-8847-4769-b997-1626f14cdbc4" />


**What is the IP address of the target computer?**  
➡️ **Answer:**  
10.5.5.11

**What directories are revealed?**  
➡️ **Answer:**  
10.5.5.11/data, 10.5.5.11/database-offline.php, 10.5.5.11/test

---

## Step 2: Locate the Challenge 4 File
- Used a web browser to access discovered URLs
<img width="1366" height="643" alt="database offline php" src="https://github.com/user-attachments/assets/337307ba-db33-44a8-a7f7-8edbc2efb481" />

<img width="1366" height="643" alt="challenge 4 data directory" src="https://github.com/user-attachments/assets/19725cc9-f469-4a69-ae52-60791de5e9be" />

<img width="1366" height="643" alt="challenge 4 tests directory" src="https://github.com/user-attachments/assets/83284c17-0e0c-44d2-b5ec-dba06c225d92" />

- Located and opened the file containing the Challenge 4 code which was in the /data/user_accounts.xml path

**What is the URL of the file?**  
➡️ **Answer:**  
http://10.5.5.11/data/user_accounts.xml

**What is the content of the file?**  
➡️ **Answer:**  
username, password and signatures

**What is the Challenge 4 code?**  
➡️ **Answer:**  
21z-1478K

<img width="1366" height="643" alt="challenge 4 code" src="https://github.com/user-attachments/assets/628944c7-3cd1-478b-b98c-d9e5943ed214" />


---

## Step 3: Research and Propose Remediation
**What are two methods to prevent file content from being transmitted in clear text?**

➡️ **Answer:**
1. Using protocols like HTTPS, SFTP, FTPS, or SSH encrypts the data as it travels over the network. This ensures that even if someone intercepts the transmission, they cannot read the content without the encryption key. 
2. Encrypting the file itself before sending it using tools like PGP/GPG, AES encryption, or BitLocker. The file remains encrypted until the intended recipient decrypts it, adding an extra layer of security even if the transmission channel is compromised.  

---

## Disclaimer
This penetration testing activity was conducted in a controlled lab environment for educational purposes only. Unauthorized testing of systems is illegal.

