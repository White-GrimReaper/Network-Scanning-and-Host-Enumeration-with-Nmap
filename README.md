<h1>Network Scanning and Host Enumeration with Nmap</h1>

<h2>Objective</h2>
Explore Nmap—an essential tool for a SOC analyst to scan networks, find active devices, and take a closer look at the services they’re running to discover unknown devices, evaluate potential vulnerabilities, and monitor unauthorized access attempts.
<br />

<h2>Required Tools/Prerequisites</h2>

- <b>Nmap</b>
- <b>Terminal/Command Prompt Access</b>

<h2>Step 1: Install Nmap</h2>

<h2>Step 2: Run a Basic Host Scan</h2>
1. Open terminal or command prompt <br>
2. Discover your IP and subnet using ipconfig on Windows or ip/ifconfig on Linux/macOS <br>
3. Look for your local IP address and subnet <br>
In this case, local IP address is 192.168.1.77 and subnet range is 192.168.1.0/24

<h2>Step 3: Scan for Active Devices</h2>
1. Run a ping scan to find live hosts on your network <br>
&emsp; a. nmap -sn 192.168.1.0/24

<h2>Step 4: Port Scan and Service Detection</h2>
1. Pick an IP from the results. Run a deeper scan to identify open ports and services <br>
<b>Nmap -sV 192.168.1.1</b>
<p align="center">
<img src="https://i.imgur.com/8u9SXXy.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
  
- Open Port <br>
&emsp; - 53/tcp <br>
&emsp; - 80/tcp <br>
&emsp; - 443/tcp <br>

- Service and Version <br>
&emsp; - Domain and dnsmasq 2.89 <br>
&emsp; - http and lighttpd 1.4.59 <br>
&emsp; - ssl/http lighttpd 1.4.59 <br>

2. Save results to a file for reporting: <br>
&emsp; - Nmap -sV -oN scan_results.txt 192.168.1.1 <br>

<h2>Step 5: Document your findings</h2>
1. Create Notes <br>
2. Nmap scans reveal the status of hosts and services on the local network <br>
&emsp; - 192.168.1.1 – Router is active and running with three open ports, 53 for DNS, 80 for HTTP, and 443 for HTTPS connections. These ports are commonly used for managing your router and handling DNS requests <br>
&emsp; - 192.168.1.71 – This host is an iPhone and seems to be active with two ports open <br>

<h2>Step 6: Investigate and Interpret</h2>
- Reflect on what is discovered <br>
- Any IP Addresses look unfamiliar <br>
- Which services are usually expected on the network <br>
- Is there a device running FTP or telnet unexpectedly <br>

The IP addresses scanned are familiar devices that are connected to this network such as the router (192.168.1.1) and the iPhone, which is my personal phone (192.168.1.71) and other devices in my personal household. Any devices that are not recognizable (which I don’t see in the network based on the scan) are worth keeping an eye on. Services found such as DNS, HTTP/HTTPS on the router are expected in the network. Thankfully, there are no FTP or Telnet services detected. Overall, the scan helps understand the network landscape and highlights the importance of monitoring unexpected devices or services.

<h2>Summary</h2>
-	Perform key Nmap scan types, including host discovery, port scanning, service detection, OS detection, and vulnerability scanning <br>
-	Identify active hosts and confirm the services running on the target device <br>
-	Validate vulnerability scan results through re-checking vendor verification, manual review, and correlation <br>
-	Strengthening investigation skills by distinguishing real findings from false positives <br>
-	Document scan outputs clearly and concisely for reporting and escalation <br>
