Lab: Compare Threat Types (Attack Surface & Port Scanning)

Domain: Threats, Attacks, and Vulnerabilities Date completed: August 2026 Tools used: Kali Linux, Nmap

Objective

Assess the attack surface of a network by identifying open service ports across three zones — an internet-facing border firewall, a guest network, and the internal network — to understand how open ports, exposed services, and OS fingerprinting represent real threat vectors that adversaries can exploit.

Steps Taken
Scanned the internet-facing border router/firewall from an external subnet using Nmap's SYN scan method, checking the top 100 common ports while enumerating running services and attempting OS detection.
Filtered the scan results to isolate open ports and any OS-identifying information, to evaluate exactly what an external attacker could learn.
Scanned the guest network to check whether it was properly isolated from company resources, or whether firewall management interfaces were reachable from a guest device.
Scanned the internal network, focusing on an internal server, to assess how much of the internal attack surface is exposed to anyone already inside the network (e.g. an insider threat or a compromised device).
Screenshots

(All hostnames, IP addresses, scan targets, and workgroup names have been redacted with solid black boxes before posting.)

Border firewall — open ports and OS detection

<img width="975" height="335" alt="image" src="https://github.com/user-attachments/assets/b1e9618d-5b8c-4be5-91cb-6f0b5c627587" />


Border firewall — filtered open ports

<img width="975" height="85" alt="image" src="https://github.com/user-attachments/assets/2ad06b31-872f-417c-a004-6612496d43e5" />


Border firewall — OS detection details

<img width="975" height="132" alt="image" src="https://github.com/user-attachments/assets/9298181b-04dc-4e4b-a022-171dccccd148" />


Guest network scan

<img width="975" height="388" alt="image" src="https://github.com/user-attachments/assets/eb389d17-f06b-40a1-9633-2aae43fd5886" />


Guest network — filtered open ports

<img width="975" height="166" alt="image" src="https://github.com/user-attachments/assets/f952bab5-1f16-40ff-adb6-ce09f5155483" />


Guest network — OS detection

<img width="975" height="114" alt="image" src="https://github.com/user-attachments/assets/61cf7ca4-07e5-476e-a6ee-9f3e98323d78" />


Internal network scan

<img width="975" height="489" alt="image" src="https://github.com/user-attachments/assets/c2922e57-d67e-49a4-982f-febe033faf49" />


Internal network — filtered open ports

<img width="975" height="257" alt="image" src="https://github.com/user-attachments/assets/0a7d7aca-8ce2-4750-a022-dc77d60cc079" />


Internal network — OS detection

<img width="975" height="128" alt="image" src="https://github.com/user-attachments/assets/3abb2b80-a698-4816-bed1-edc7f3712653" />


Key Findings
Border firewall: Only port 25 (SMTP) was open and discoverable from the internet — a reasonably small external attack surface, though OS fingerprinting was still possible.
Guest network: Ports 80, 443, and 8000 exposed the firewall's own management interface to anyone on the guest network — a real misconfiguration, since guest devices should never be able to reach management interfaces on core infrastructure.
Internal network: A significant number of ports were open on an internal server (SMB, RPC, MySQL, IMAP, SMTP, and more), with no firewall segmenting the client and server networks. This is evidence of poor network segmentation — any internal device (or insider threat) could reach these services directly. The server was also running Windows Server 2016, which reached end-of-life in January 2022 and is approaching end-of-service-life in January 2027, meaning it should be prioritized for replacement.
What I Learned

Open ports are only half the risk — what matters just as much is where they're reachable from. A port that's fine to expose internally can be a serious problem if it's reachable from a guest network, and a lack of network segmentation means a single compromised or malicious device can see far more of the internal attack surface than it should. OS and service fingerprinting also matters: the more specific information a scan can reveal about a target, the easier it is for an attacker to pick an exploit that will actually work.
