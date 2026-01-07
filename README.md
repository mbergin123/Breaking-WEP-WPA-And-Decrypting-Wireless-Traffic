# 🔓 Breaking WEP & WPA and Decrypting Wireless Traffic

## 📘 Overview
This project demonstrates how to exploit weaknesses in both Wired Equivalent Privacy (WEP) and Wi-Fi Protected Access (WPA) wireless security protocols. Using Kali Linux and industry-standard tools such as Aircrack-ng, Airdecap-ng, and Wireshark, encrypted wireless traffic was captured, cracked, decrypted, and fully analyzed at the application layer.

This project showcases real-world wireless penetration testing methodology and end-to-end network forensics skills.

---

## 🎯 Learning Objectives
- Understand how WEP and WPA wireless encryption function
- Capture encrypted 802.11 wireless traffic
- Crack WEP keys using IV-based attacks
- Crack WPA passphrases using dictionary attacks
- Decrypt wireless packet captures
- Analyze decrypted traffic in Wireshark
- Extract credentials, emails, DNS data, and HTTP objects

---

## 🛠️ Tools & Technologies Used
- Kali Linux
- Aircrack-ng Suite
- Airdecap-ng
- Wireshark
- Linux Command Line

---

## 📑 Activity Log – Step-by-Step Documentation

Step 1 — Lab Topology Identified  
Reviewed the Kali Linux wireless analysis environment.  
![Topology](images/WEPTOP.png)

Step 2 — Checked Wireless Interface Extensions  
Command used: iwconfig  
![iwconfig command](images/StartIW.png)

Step 3 — Viewed Airmon-ng Options  
Command used: airmon-ng --help  
![Airmon Command](images/StartAir.png)

Step 4 — Viewed Aircrack-ng Options  
Command used: aircrack-ng  
![Airecrack Command](images/StartAirCrack.png)

Step 5 — Viewed Airdecap-ng Options  
Command used: airdecap-ng  
![Airdecap Command](images/startairedecap.png)

Step 6 — Listed Files in Working Directory  
Command used: ls  
![LSCommand](images/lskali.png)

Step 7 — Retrieved Flag 1  
Command used: cat sampleflag.txt  
Flag 1: 999818  
![First Flag](images/FirstFlagXXX.png)

Step 8 — Retrieved Flag 2  
Command used: cat flag2.txt  
Flag 2: 555616  
![SecondFlag](images/SecondFlagXXX.png)

Step 9 — Opened WEP Capture in Wireshark  
Command used: wireshark wepcapture.cap  
![Wireshark](images/WebCap.png)

Step 10 — Verified No IP Traffic Before Decryption  
Wireshark filter applied: ip  
![No IP Address](images/NOIP.png)

Step 11 — Began WEP Key Cracking  
Command used: aircrack-ng wepcapture.cap  
![aircrack](images/aircrackwep.png)

Step 12 — WEP Key Recovered  
Recovered key: 39:80:35:D5:9C  
![Recovered Key](images/keyFound.png)

Step 13 — Decrypted WEP Traffic  
Command used: airdecap-ng -w 39:B0:35:D5:9C wepcapture.cap  
![airdecap](images/decryptWEP.png)

Step 14 — Verified Decrypted WEP File  
Command used: ls  
New file found: wepcapture-dec.cap  
![New File Found](images/decNewFile.png)

Step 15 — Verified IP Visibility After WEP Decryption  
Wireshark filter applied: ip  
![IP is Visible](images/SeeIP.png)

Step 16 — Recovered Plaintext FTP Password (WEP)  
Recovered password: PACERS123  
![Recovered Password](images/PACERS123.png)

Step 17 — Retrieved Flag 3 from DNS Traffic  
Wireshark filter applied: dns and frame contains "flag"  
Flag 3: 888912  
![Flag 3 Found](images/Flag3Found.png)

Step 18 — Viewed Plaintext POP3 Email (WEP)  
Recovered email content in plaintext.  
![Clevland Picture](images/Clevland.png)

Step 19 — Retrieved Flag 4 from Telnet Traffic  
Flag 4: 876554  
![Flag 4 Found](images/Flag4Found.png)

Step 20 — Retrieved Flag 5 from QOTD Traffic  
Wireshark filter applied: tcp.port == 17  
Flag 5: 818344  
![Flag 5 found](images/Flag5Found.png)

Step 21 — Retrieved Flag 6 from Next TCP Stream  
Flag 6: 555344  
![Flag 6 Found](images/Flag6Found.png)

Step 22 — Exported HTTP Objects (WEP)  
Recovered Cleveland Cavaliers images via HTTP export.  
![Recovered Cleveland Photos](images/ClevelandPhotos.png)

---

## 🔐 WPA Analysis

Step 23 — Verified Export Folder Exists  
Confirmed exported wep folder.  
![Web Listed](images/weplisted.png)

Step 24 — Opened WPA Capture and Verified Encryption  
Command used: wireshark wpacapture.cap  
Wireshark filter applied: ip  
No IP traffic visible.  
![NO IP Address](images/NOIP2.png)

Step 25 — Performed WPA Dictionary Attack  
Command used: aircrack-ng wpacapture.cap -w Wordlist.txt  
Recovered WPA passphrase: boneless  
![Recovered Password](images/Boneless.png)

Step 26 — Decrypted WPA Traffic  
Command used: airdecap-ng -e SECURETWO -p boneless wpacapture.cap  
New file created: wpacapture-dec.cap  
![airedecap command](images/aircrackNewFile.png)

Step 27 — Verified WPA Decryption in Wireshark  
Wireshark filter applied: ip  
![Second Round of IPs are Visable](images/SeeIP2.png)

Step 28 — Recovered Plaintext FTP Credentials (WPA)  
Recovered password: P@ssw0rd  
![Password Recovered](images/FTPPass.png)

Step 29 — Viewed Plaintext POP3 Credentials (WPA)  
POP3 credentials visible in plaintext.  
![POP3](images/popPass.png)

Step 30 — Reconstructed POP3 Email Content (WPA)  
Recovered plaintext email discussing the San Antonio Spurs.  
![San Antonio Email](images/sanemail.png)

Step 31 — Exported HTTP Objects (WPA)  
Exported HTTP objects and recovered San Antonio Spurs images.  
![San Antonio Images](images/SanImages.png)

---

## 🧠 Why This Project Is Important
This project demonstrates a complete wireless attack lifecycle including capturing encrypted traffic, cracking WEP and WPA encryption, decrypting packet captures, performing deep packet inspection, and extracting credentials, emails, DNS data, and images. It highlights the dangers of weak encryption and plaintext protocols such as FTP, Telnet, POP3, and HTTP.

---

## 📚 What I Learned
- Why WEP is fundamentally broken due to IV reuse
- How WPA handshakes can be cracked using dictionary attacks
- How encryption affects packet visibility
- How attackers extract sensitive data after decryption
- How to reconstruct full application-layer sessions using Wireshark

---

## 🔗 References
https://www.aircrack-ng.org/  
https://www.wireshark.org/

---

## ✅ Project Completed
This project demonstrates hands-on wireless penetration testing, cryptographic attacks, traffic decryption, and forensic packet analysis.
