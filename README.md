# 🔍 Local Network Port Scanning using Nmap

## 📌 Objective

To discover active hosts and open ports within the local network in order to understand which services are exposed and identify potential security risks.

---

## 🧰 Tools Used

- **Nmap** – For scanning IP addresses and detecting open ports on the local network.

---

## ✅ What I Did

1. **Identified Local IP Range**  
   - Local IP: `192.168.1.70`  
   - Subnet Mask: `255.255.255.0`  
   - IP Range: `192.168.1.0/24`

2. **Scanned the Network** using Nmap with a TCP SYN scan:
   ```bash
    nmap -sS 192.168.1.0/24 -oN local_network_scan.txt
   -sS: Performs a stealthy TCP SYN scan
   -oN: Saves the output to a normal text file (output-task1.txt)
3. **Documented and Analyzed the Results**
  - Extracted IPs with open ports
  - Mapped ports to common services
  - Identified device types and inferred potential risks

---

## Scan Summary

| IP Address    | Open Ports          | Services                   | Notes                                      |
| ------------- | ------------------- | -------------------------- | ------------------------------------------ |
| 192.168.1.1   | 53, 80, 443         | DNS, HTTP, HTTPS           | Likely router; filtered ports too |
| 192.168.1.88  | 49152, 62078        | Dynamic, iPhone-sync       | Possibly an iOS device                     |
| 192.168.1.231 | None (all closed)   | —                          | Device detected, but no open ports         |
| 192.168.1.70  | 135, 139, 445, 3306 | MSRPC, NetBIOS, SMB, MySQL | Windows system with exposed services       |

---

## Security Observations
- The router (192.168.1.1) exposes common services like DNS and HTTP(S); remote admin should be disabled unless needed.
- 192.168.1.70 exposes SMB (file sharing) and MySQL:
  - These can be potential entry points if not firewalled or secured.
- The iOS device exposes sync services — no immediate concern.
- 192.168.1.231 is likely well-secured with no visible open ports.

---

## 📂 Files in this Repository
### ▶️  [`Documents/`](./Documents/)
- output-task1.txt – Raw Nmap scan results
- Task-1 Local Network Scan - Word document containing analysis of the scan
- Screenshot of the scan result

---

## 🧠 Learnings
- Understood how to perform stealth scans on a network
- Learned how to interpret open ports and map them to services
- Gained awareness of local device exposure and the importance of port filtering
