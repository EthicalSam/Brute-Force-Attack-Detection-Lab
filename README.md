# Brute-Force Attack Detection Lab using Wireshark

## Objective
Simulated a brute-force login attack against DVWA (Damn Vulnerable Web Application) using Hydra in an isolated lab environment, and captured/analyzed the attack traffic using Wireshark to validate detection capability.

## Tools Used
- DVWA (Damn Vulnerable Web Application)
- Hydra
- Wireshark
- Kali Linux (Apache2, MySQL)

## Steps Performed

**1. Started Required Services**
Started Apache2, MySQL, and DVWA services on Kali Linux to host the vulnerable web application locally.



![Starting Services](01%20Starting%20Services.png)



**2. Configured DVWA Database**
Set up the DVWA database via the Setup page, confirming PHP modules and database connectivity were correctly configured.



![Database Setup](02%20Database%20Setup.png)



**3. Set DVWA Security Level to Low**
Configured DVWA's security level to "Low" to simulate a real-world vulnerable login form with no rate limiting or CAPTCHA protection.



![Security Level Setup](03%20Security%20Level%20Setup.png)



**4. Selected Wireshark Capture Interface**
Selected the Loopback (lo) interface in Wireshark to capture traffic between Hydra and DVWA, since both were running on the same local machine.



![Wireshark Interface Selection](04%20Wireshark%20Interface%20Selection.png)



**5. Performed Brute-Force Attack Using Hydra**
Created a custom password wordlist and launched Hydra against the DVWA Brute Force login form. Hydra successfully identified valid credentials (admin/123456) within seconds.



![Hydra Successful Attack](05%20Hydra%20Successful%20Attack.png)



**6. Captured and Analyzed Attack Traffic in Wireshark**
Applied an HTTP display filter in Wireshark to isolate the attack traffic. Identified multiple GET requests to the login form with different username/password combinations, and observed that credentials were transmitted in plaintext within the URL — along with the Hydra tool signature visible in the User-Agent header.



![Credential Visible](06%20Credential%20Visible.png)



## Key Learnings
- Gained hands-on experience simulating a brute-force attack in a safe, isolated lab environment using Hydra.
- Learned to capture and analyze attack traffic using Wireshark's Loopback interface and HTTP display filters.
- Identified a real security weakness: DVWA (Low security) transmits login credentials in plaintext via GET requests, making them fully visible in network traffic.
- Recognized tool-based attack signatures (e.g., Hydra's User-Agent string) as an indicator of automated attack activity.
- Understood the complete offense-to-defense loop: simulating an attack, capturing it, and analyzing it from a detection standpoint.
