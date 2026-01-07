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

## 🖥️ Lab Topology
![Topology](WEPTOP.png)

---

## 📑 Activity Log – Step-by-Step Documentation

Step 1 — Lab Topology Identified  
Reviewed the Kali Linux wireless analysis environment.  
Screenshot: WEPTOP.png

Step 2 — Checked Wireless Interface Extensions  
Command used: iwconfig  
Screenshot: iwconfig_no_wireless.png

Step 3 — Viewed Airmon-ng Options  
Command used: airmon-ng --help  
Screenshot: StartAir.png

Step 4 — Viewed Aircrack-ng Options  
Command used: aircrack-ng  
Screenshot: StartAirCrack.png

Step 5 — Viewed Airdecap-ng Options  
Command used: airdecap-ng  
Screenshot: startairdecap.png

Step 6 — Listed Files in Working Directory  
Command used: ls  
Screenshot: lskali.png

Step 7 — Retrieved Flag 1  
Command used: cat sampleflag.txt  
Flag 1: 999818  
Screenshot: FirstFlagXXX.png

Step 8 — Retrieved Flag 2  
Command used: cat flag2.txt  
Flag 2: 555616  
Screenshot: SecondFlagXXX.png

Step 9 — Opened WEP Capture in Wireshark  
Command used: wireshark wepcapture.cap  
Screenshot: WebCap.png

Step 10 — Verified No IP Traffic Before Decryption  
Wireshark filter applied: ip  
Screenshot: NOIP.png

Step 11 — Began WEP Key Cracking  
Command used: aircrack-ng wepcapture.cap  
Screenshot: aircrackwep.png

Step 12 — WEP Key Recovered  
Recovered key: 39:80:35:D5:9C  
Screenshot: keyFound.png

Step 13 — Decrypted WEP Traffic  
Command used: airdecap-ng -w 39:B0:35:D5:9C wepcapture.cap  
Screenshot: decryptWEP.png

Step 14 — Verified Decrypted WEP File  
Command used: ls  
New file found: wepcapture-dec.cap  
Screenshot: decNewFile.png

Step 15 — Verified IP Visibility After WEP Decryption  
Wireshark filter applied: ip  
Screenshot: SeeIP.png

Step 16 — Recovered Plaintext FTP Password (WEP)  
Recovered password: PACERS123  
Screenshot: PACERS123.png

Step 17 — Retrieved Flag 3 from DNS Traffic  
Wireshark filter applied: dns and frame contains "flag"  
Flag 3: 888912  
Screenshot: Flag3Found.png

Step 18 — Viewed Plaintext POP3 Email (WEP)  
Recovered email content in plaintext.  
Screenshot: Clevland.png

Step 19 — Retrieved Flag 4 from Telnet Traffic  
Flag 4: 876554  
Screenshot: Flag4Found.png

Step 20 — Retrieved Flag 5 from QOTD Traffic  
Wireshark filter applied: tcp.port == 17  
Flag 5: 818344  
Screenshot: Flag5Found.png

Step 21 — Retrieved Flag 6 from Next TCP Stream  
Flag 6: 555344  
Screenshot: Flag6Found.png

Step 22 — Exported HTTP Objects (WEP)  
Recovered Cleveland Cavaliers images via HTTP export.  
Screenshot: ClevelandPhotos.png

---

## 🔐 WPA Analysis

Step 23 — Verified Export Folder Exists  
Confirmed exported wep folder.  
Screenshot: weplisted.png

Step 24 — Opened WPA Capture and Verified Encryption  
Command used: wireshark wpacapture.cap  
Wireshark filter applied: ip  
No IP traffic visible.  
Screenshot: NOIP2.png

Step 25 — Performed WPA Dictionary Attack  
Command used: aircrack-ng wpacapture.cap -w Wordlist.txt  
Recovered WPA passphrase: boneless  
Screenshot: Boneless.png

Step 26 — Decrypted WPA Traffic  
Command used: airdecap-ng -e SECURETWO -p boneless wpacapture.cap  
New file created: wpacapture-dec.cap  
Screenshot: aircrackNewFile.png

Step 27 — Verified WPA Decryption in Wireshark  
Wireshark filter applied: ip  
Screenshot: SeeIP2.png

Step 28 — Recovered Plaintext FTP Credentials (WPA)  
Recovered password: P@ssw0rd  
Screenshot: FTPPass.png

Step 29 — Viewed Plaintext POP3 Credentials (WPA)  
POP3 credentials visible in plaintext.  
Screenshot: popPass.png

Step 30 — Reconstructed POP3 Email Content (WPA)  
Recovered plaintext email discussing the San Antonio Spurs.  
Screenshot: SanEmail.png

Step 31 — Exported HTTP Objects (WPA)  
Exported HTTP objects and recovered San Antonio Spurs images.  
Screenshot: SanImages.png

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
