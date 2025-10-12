## Week-2
## Day 2: Network Reconnaissance & Threat Emulation
# Mission Parameters:

Time Allotment: 90-120 minutes

# Primary Objective: Learn to profile and scan network targets using Nmap.

Success Criteria: Execute targeted scans against external and internal hosts, interpreting the results to identify attack vectors.

*Phase 1:* Fix Network Discovery <br/>
*Task 1.1:* Find Your Network Range

bash
`ip route show` <br/>
Expected Output & Verification: <br/>
<img width="664" height="78" alt="Screenshot 2025-10-12 103528" src="https://github.com/user-attachments/assets/9f7aa07c-e368-4675-b225-3e3a4d7960cf" />
<br/>
Look for a line like: <br/>
default via 192.168.1.1 dev ens33 proto static <br/>
OR <br/>
192.168.1.0/24 dev ens33 proto kernel scope link src 192.168.1.115
<br/>
Document your network range: 192.168.1.0/24 (yours may differ)

---

*Task 1.2*: Proper Network Discovery

bash
`nmap -sn 192.168.1.0/24`<br/>
(Replace with your actual network range from above)
<img width="852" height="312" alt="image" src="https://github.com/user-attachments/assets/7863c084-44ce-40d0-9c24-e8894d7339b9" />
<br/> <br/>
Expected Output: A list of live IP addresses on your network.

---
---

*Phase 2:* Perfect External Scanning <br/>
*Task 2.1:* Correct Target & Syntax

bash
`nmap -sS -sV -T4 scanme.nmap.org` <br/>
(Notice: -sV not -sv, -sC omitted for now to be less aggressive)
<img width="1051" height="285" alt="image" src="https://github.com/user-attachments/assets/d9535d13-3002-4145-aef0-db5e1edf8db0" />
<br/>
Expected Output & Verification:
You should get a clean output showing open ports 22, 80, 9929 without the "giving up" warning.

---

*Task 2.2 Your task :* Add Script Scanning

bash
`nmap -sS -sV -sC -T4 --max-retries 2 scanme.nmap.org` <br/>
(--max-retries 2 makes it less aggressive)

---
---

*Phase 3:* Internal Scanning Practice <br/>
*Task 3.1:* Scan Your Kali Machine By Using your ip.

---

bash
nmap `-sS -sV -sC -T4 -oA day2_scan scanme.nmap.org` <br/> <br/>
<img width="990" height="347" alt="image" src="https://github.com/user-attachments/assets/bcff987d-c592-4691-b9a8-663ea1d2b0d6" /> 
<br/> <br/>
bash
`ls -la day2_scan*`<br/><br/>
<img width="757" height="118" alt="image" src="https://github.com/user-attachments/assets/a9d95e1c-f0ae-417d-a8ba-fb4efa2d5c8a" />
<br/>
Verification: You should see three files created.
