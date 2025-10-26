# ICMP (INTERNET CONTROL MESSAGE PROTOCOL)

The Network's Diagnostic Protocol



Key Functions:



* Error Reporting: "Destination Unreachable", "Time Exceeded"



* Network Diagnostics: ping and traceroute



* Connection Testing: Host discovery, path MTU discovery



## ICMP Message Types:



* Echo Request (Type 8) / Echo Reply (Type 0): Used by ping



* Destination Unreachable (Type 3): Can't reach target



* Time Exceeded (Type 11): Used by traceroute (TTL expired)

---

# ARP (ADDRESS RESOLUTION PROTOCOL)

The Local Network Translator



How ARP Works:

Question: "Who has IP 192.168.1.1? Tell 192.168.1.100"

• ARP Request (Broadcast): Sent to entire local network

• ARP Reply (Unicast): "I have 192.168.1.1, my MAC is aa:bb:cc:dd:ee:ff"



Key Points:



* Layer 2 Protocol: Works only within same local network



* ARP Cache: Stores IP-to-MAC mappings temporarily



* No Authentication: Trusts whatever reply comes first (security vulnerability!)

---

# DHCP (DYNAMIC HOST CONFIGURATION PROTOCOL)

The Automatic Network Configurator



DHCP Process (DORA):



* DISCOVER: Client broadcasts "Is there a DHCP server?"



* OFFER: Server responds "I can offer you IP X"



* REQUEST: Client says "I'll take IP X"



* ACKNOWLEDGE: Server confirms "OK, IP X is yours for lease time Y"

---

# DNS (DOMAIN NAME SYSTEM)

The Internet's Phonebook



DNS Resolution Process:



* Check local cache (browser, OS)



* Query local DNS resolver (usually ISP or company DNS)



* Recursive query to root servers → TLD servers → authoritative servers



* Return IP address to client



*DNS Record Types:*



* A Record: IPv4 address



* AAAA Record: IPv6 address



* CNAME Record: Alias to another domain



* MX Record: Mail servers



* NS Record: Name servers

---

## HANDS-ON LAB - NETWORK DISCOVERY



**Exercise 1: ICMP Network Discovery**



*\# Discover your network information*

`ipconfig /all`                    # Windows

`ifconfig`                       # Linux/Mac

`ip a`                             # Modern Linux



\# Ping your gateway

`ping <your-gateway-ip>`



\# Ping sweep (discover live hosts) - Replace network range

`for /L %i in (1,1,254) do @ping -n 1 -w 100 192.168.1.%i | find "Reply"`

</br>

**Exercise 2: ARP Table Analysis**



\# View ARP cache

`arp -a`                           # Windows

`arp -n`                           # Linux/Mac



\# Clear ARP cache and observe repopulation

`arp -d \*`                         # Windows (admin)

`sudo ip -s -s neigh flush all`    # Linux



\# After clearing, ping a local IP and check ARP table again

</br>

**Exercise 3: DNS Analysis with Wireshark**

Clear DNS cache:



`ipconfig /flushdns`            # Windows

`sudo systemd-resolve --flush-caches`  # Linux



Start Wireshark capture with filter: dns



Perform DNS lookup:

`nslookup google.com`

`dig google.com`                # Linux/Mac



Analyze DNS packets in Wireshark

---

# 4. RED TEAMER PERSPECTIVE

Why These Protocols Matter for Attacks:



## ICMP-Based Attacks:



* ICMP Reconnaissance: Ping sweeps to discover live hosts



* ICMP Tunneling: Exfiltrate data through ICMP packets



* Time Exceeded Attacks: Network mapping with traceroute



## ARP-Based Attacks:



* ARP Spoofing/Poisoning: Redirect traffic through your machine (Man-in-the-Middle)



* MAC Flooding: Overwhelm switch CAM tables



## DHCP-Based Attacks:



* Rogue DHCP Server: Offer malicious DNS servers to clients



* DHCP Starvation: Exhaust DHCP pool



## DNS-Based Attacks:



* DNS Cache Poisoning: Redirect domains to malicious IPs



* DNS Tunneling: C2 communication through DNS queries



* DNS Reconnaissance: Discover internal network structure





