
# Local Network Port Scanning (Task 1)

## 📋 Task Overview
This task focuses on learning network reconnaissance by scanning a local network to discover open ports and understand network exposure. 

---

## 🎯 Objective
To discover open ports on devices in my local network using Nmap.

---

## 🛠️ Tools Used


**Nmap (Network Mapper)** - Version 7.95
  - Industry-standard network scanning tool
  - Used for discovering hosts and services on a network
  - Free and open-source

## Operating Environment
- **Kali Linux** - A Debian-based Linux distribution designed for penetration testing and security auditing

---

## 📝 Methodology & Steps Performed

### Step 1: Environment Setup
- Installed Nmap on Kali Linux (pre-installed in most cases)
- Verified installation: `nmap --version`

### Step 2: Identify Local Network Range
- Used `ifconfig` command to find local IP address
- Identified network: **192.168.13.0/24**
- This notation means:
  - Network: 192.168.13.0
  - Subnet mask: 255.255.255.0
  - Total possible hosts: 256 (192.168.13.0 - 192.168.13.255)

### Step 3: Execute TCP SYN Scan
Ran the following command:
```bash
sudo nmap -sS 192.168.13.0/24
```

**Command Breakdown:**
- `sudo` - Required for SYN scan (requires root privileges)
- `nmap` - The scanning tool
- `-sS` - TCP SYN scan (also called "stealth scan")
- `192.168.13.0/24` - Target network range

### Step 4: Analyze and Document Results
- Captured scan output to a text file. Ran the following command:
  ```bash
  nmap -sS 192.168.1.0/24 -oN scanrep.txt
  ```
- Took screenshots of the scanning process
- Analyzed discovered hosts and open ports
- Researched services running on identified ports

---

## 🔍 Scan Results & Findings

### Scan Summary
- **Scan Duration:** 8.52 seconds
- **Total IP Addresses Scanned:** 256
- **Active Hosts Discovered:** 4
- **Scan Date:** October 20, 2025, 06:55:18

### Detailed Host Analysis

#### Host 1: 192.168.13.1
- **Status:** Up (Latency: 0.0033s)
- **MAC Address:** 00:50:56:C0:00:08
- **Vendor:** VMware
- **Open Ports:** None
- **Port States:** 1000 filtered ports (no-response)
- **Analysis:** Likely a VMware virtual network gateway or router with firewall enabled, blocking incoming scan requests

#### Host 2: 192.168.13.2
- **Status:** Up (Latency: 0.00019s)
- **MAC Address:** 00:50:56:E5:EA:AE
- **Vendor:** VMware
- **Open Ports:** 
  - **Port 53/tcp - DNS (Domain Name System)**
- **Closed Ports:** 999 closed ports
- **Analysis:** This is a DNS server, likely handling domain name resolution for the network

#### Host 3: 192.168.13.254
- **Status:** Up (Latency: 0.00017s)
- **MAC Address:** 00:50:56:FC:77:58
- **Vendor:** VMware
- **Open Ports:** None
- **Port States:** 1000 filtered ports (no-response)
- **Analysis:** Another VMware network device with firewall protection, possibly a gateway or router

#### Host 4: 192.168.13.128 (Scanning Machine)
- **Status:** Up (Latency: 0.0000080s)
- **MAC Address:** Not shown (this is the host performing the scan)
- **Open Ports:** None visible in external scan
- **Closed Ports:** 1000 closed ports
- **Analysis:** This is the Kali Linux machine used for scanning

---

## 🔐 Security Analysis

### Port 53 (DNS) - 192.168.13.2

**Service Description:**
- DNS (Domain Name System) is used to translate domain names to IP addresses
- Essential for network functionality and standard protocol for name resolution

**Potential Security Risks:**
1. **DNS Spoofing/Cache Poisoning:** Attackers could inject false DNS records, redirecting users to malicious sites
2. **DNS Amplification Attacks:** Can be exploited for DDoS attacks
3. **Information Disclosure:** DNS queries can reveal network topology and internal hostnames
4. **DNS Tunneling:** Attackers might use DNS to exfiltrate data or establish covert channels

**Mitigation Recommendations:**
- Implement DNSSEC (DNS Security Extensions) to prevent spoofing
- Configure DNS server to respond only to authorized clients
- Use firewalls to restrict DNS traffic to trusted sources only


**Hosts with Filtered Ports:** 192.168.13.1 and 192.168.13.254

**What "Filtered" Means:**
- A firewall, packet filter, or other network device is blocking the probe


---



## 🚀 Key Takeaways

1. ✅ Successfully scanned 256 IP addresses in the local network
2. ✅ Discovered 4 active hosts in a VMware virtual environment
3. ✅ Identified 1 open port (DNS on port 53)
4. ✅ Learned about port states: open, closed, and filtered
5. ✅ Understood the importance of firewalls and filtered ports
6. ✅ Gained practical experience with Nmap and TCP SYN scanning
7. ✅ Analyzed security implications of open ports
8. ✅ Developed network reconnaissance fundamentals

---


## 📂 Repository Contents

```
cybersecurity-task1-port-scanning/
├── README.md           # This file - Complete documentation
├── scanrep.txt         # Raw Nmap scan output
└── image.png           # Screenshot of scan execution
```


