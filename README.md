# Wireshark-W1
As part of a simulated Security Operations Center (SOC) Analyst role, I completed a series of 6 practical Wireshark labs. The objective was to analyze live network packet captures to identify attackers, extract unencrypted data, detect brute-force attacks, and investigate a VoIP scam call. 

📖 **Project Overview**
Role: SOC Analyst (Simulated)
Tools Used: Wireshark
Platform: NetworkWalks Labs
![](CompletedTasks.PNG)

🔬 Lab Write-ups
Lab 1 & 2: Identify the Attacker & Follow TCP Stream (Parts 1 & 2)
Objective: Locate the attacker's IP address and rebuild TCP conversations to read hidden messages.

**Methodology**
Filtered traffic to identify anomalous IP addresses interacting with internal hosts.
Used the Follow > TCP Stream feature to reassemble fragmented data packets into readable text, revealing hidden communications.
![](wireshark 1.PNG)
![](w2.PNG)
![](w3.PNG)

**Lab 3: HTTP Plain Text Credentials**
Objective: Demonstrate the risks of unencrypted authentication by extracting credentials from HTTP traffic.

**Methodology**
Filtered using http.request.method == "POST" to locate the sign-in form submission.
Inspected the HTML Form URL Encoded layer to extract the plain-text username and password.
Key Takeaway: Highlighted the critical need for HTTPS to prevent credential sniffing.
![](w5.png)
![](Lab6Result.png)

**Lab 4: Catch the Brute Force Attacker**
Objective: Detect a password-guessing attack against an FTP server.
**Methodology**
Filtered for ftp traffic and observed a high volume of USER admin requests.
Identified the attacker's IP by tracking the source of repeated 530 Login incorrect responses from the server.
![](bruteforce.PNGP)
![](Lab7Result.png)

**Lab 5: Catch the Call Scammer (VoIP Analysis)**
Objective: Investigate a VoIP call to identify the caller and replay the conversation.
**Methodology:**
Analyzed SIP (Session Initiation Protocol) traffic to locate the INVITE packet and identify the originating extension.
Examined RTP (Real-time Transport Protocol) packets to determine the voice codec (Payload Type).
Utilized Telephony > VoIP Calls to reconstruct and play back the audio stream, listening for the scammer's opening lines.
![](VOIP1.PNG)
![](VOIP2.PNG)

**🧠 Core Wireshark Filters Used**
Throughout this project, I heavily utilized the following display filters:
ip.addr == [IP_ADDRESS] - To isolate traffic to/from a specific host.
http.request.method == "POST" - To find form submissions.
ftp - To analyze file transfer and login attempts.
sip and rtp - To isolate VoIP signaling and voice payloads.
tcp.stream eq [number] - To view a specific, reconstructed TCP conversation.

⚠️ Disclaimer
This project was completed in a controlled, sandboxed lab environment provided by NetworkWalks. No live networks were targeted or captured without permission. All data analyzed was pre-captured for educational purposes.









