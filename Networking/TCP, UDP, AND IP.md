# CORE CONCEPTS TO MASTER :-



## TCP (TRANSMISSION CONTROL PROTOCOL)

The Reliable Postal Service



Key Characteristics:



* Connection-Oriented: Requires established connection before data transfer



* Reliable Delivery: Uses acknowledgements and retransmissions



* Ordered Data: Uses sequence numbers to maintain order



* Flow Control: Prevents overwhelming the receiver



* Error Checking: Ensures data integrity

---

## THE TCP THREE-WAY HANDSHAKE :-



This is non-negotiable knowledge:

1\. SYN (Synchronize)

   • Client → Server: "I want to connect, my starting sequence number is X"

 

2\. SYN-ACK (Synchronize-Acknowledge)

   • Server → Client: "I acknowledge your request, my starting sequence number is Y"

 

3\. ACK (Acknowledge)

   • Client → Server: "I acknowledge your acknowledgement, let's start transferring data!"

---

## TCP FLAGS - THE CONTROL MESSAGES :-



Each flag is 1 bit (on/off) in the TCP header:



* SYN (Synchronize): Initiates connection establishment



* ACK (Acknowledge): Acknowledges received packets



* FIN (Finish): Gracefully terminates connection



* RST (Reset): Immediately terminates connection (abort)



* PSH (Push): "Push" data immediately to application



* URG (Urgent): Marks data as urgent

---

###### 

## UDP (USER DATAGRAM PROTOCOL) :-



The "Fire and Forget" Protocol



Key Characteristics:



* Connectionless: No handshake, no connection establishment



* Unreliable: No delivery guarantees, no retransmissions



* Faster: Lower overhead, no sequence tracking



* Simple: Minimal header structure



*When UDP is Preferred:*



* DNS queries (fast response needed)



* VoIP/Video streaming (speed over reliability)



* Gaming (real-time requirements)

---

## IP (INTERNET PROTOCOL - IPv4) :-



The Addressing System



IPv4 Packet Structure:



* Source IP Address: Where it's from



* Destination IP Address: Where it's going



* Time-to-Live (TTL): Prevents infinite loops (decremented by each router)



* Protocol: Identifies TCP (6) or UDP (17)


---


## Answers to Your Advanced Questions:



"How do TCP flags help evade detection in port scanning?"



SYN Scan (-sS): Stealthy - doesn't complete handshake, looks like connection attempts that failed



ACK Scan (-sA): Bypasses stateless firewalls - tests if ports are "unfiltered"



FIN Scan (-sF): Sends FIN flag to closed ports - some systems don't log FIN packets



NULL Scan (-sN): Sends no flags - triggers responses from closed ports on some systems



XMAS Scan (-sX): Sends FIN, PSH, URG - "lit up like a Christmas tree"

</br>

"TCP vs UDP for backdoor connections?"



TCP: More reliable, easier to maintain persistent connections, but more detectable



UDP: Stealthier (less monitoring), faster for C2, but can be unreliable



Real-world: Advanced implants use both - TCP for reliability, UDP for stealth when needed

