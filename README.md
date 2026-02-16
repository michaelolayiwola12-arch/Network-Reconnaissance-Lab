# Internal Network Reconnaissance Lab

## 📖 Objective
To perform internal network discovery and service enumeration on a local subnet to identify active hosts, gateways, and exposed services.

---

## 🛠 Tools Used
- Kali Linux
- Nmap
- iproute2 (ip addr, ip route)

---

## 🔍 Step 1: Identify Network Configuration

Command used:
ip addr show
ip route show


Findings:
- IP Address: 192.168.0.104
- Subnet: 192.168.0.0/24
- Default Gateway: 192.168.0.1

---

## 🔍 Step 2: Discover Active Hosts

Command used:
nmap -sn 192.168.0.0/24


Discovered hosts:
- 192.168.0.1 (Gateway)
- 192.168.0.2
- 192.168.0.3
- 192.168.0.4
- 192.168.0.104 (Kali)

---

## 🔍 Step 3: Service Enumeration on Gateway

Command used:
nmap -sV -p 22,23,80,443,53 192.168.0.1


Open ports identified:
- 53/tcp (DNS - dnsmasq)
- 80/tcp (HTTP)
- 443/tcp (HTTPS)

---

## 🗺 Network Diagram

Internet  
│  
192.168.0.1 (Router/Gateway)  
│  
192.168.0.0/24  
├── 192.168.0.2  
├── 192.168.0.3  
├── 192.168.0.4  
└── 192.168.0.104 (Kali)

---

## 🔐 Security Observations

- Flat network (no VLAN separation)
- Router management interface accessible via HTTP and HTTPS
- DNS service exposed internally
- No Telnet or SSH open on gateway

---

## 🎯 Conclusion

This lab demonstrates structured internal network reconnaissance methodology including subnet identification, host discovery, and service enumeration.
