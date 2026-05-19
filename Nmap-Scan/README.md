# Nmap Reconnaissance Lab - Windows Host

## Objective

The goal of this lab was to perform basic network reconnaissance against my own physical Windows machine from a Kali Linux virtual machine using Nmap.

This lab demonstrates host discovery, service enumeration, OS detection, and basic interpretation of Nmap scan results in a local ethical hacking environment.

## Lab Environment

- Attacker machine: Kali Linux VM
- Target machine: Personal physical Windows host
- Target IP address: `192.168.1.81`
- Network type: Local private LAN
- Authorization: The scan was performed only against my own device

## Tools Used

- Kali Linux
- Nmap
- Oracle VirtualBox
- Windows host machine

## Command Used

```bash
nmap -sC -sV -A 192.168.1.81
```

The command uses several useful Nmap options:

- `-sC` runs default Nmap scripts
- `-sV` detects service versions
- `-A` enables OS detection, version detection, script scanning, and traceroute

## 1. Scan Start

The scan was started from the Kali Linux VM against the Windows machine on the local network.

At this stage, Nmap confirmed that the target host was active and started a SYN stealth scan.

<img src="assets/1. Slika.png" alt="Scan start" width="900">

## 2. Open Ports and Services

Nmap detected that the host was online and found several open TCP ports.

| Port | State | Service | Description |
|---|---|---|---|
| `135/tcp` | open | msrpc | Microsoft Windows RPC |
| `139/tcp` | open | netbios-ssn | Microsoft Windows NetBIOS |
| `445/tcp` | open | microsoft-ds | SMB / Windows file sharing |
| `1059/tcp` | open | msrpc | Microsoft Windows RPC |
| `1064/tcp` | open | msrpc | Microsoft Windows RPC |
| `2179/tcp` | open | vmrdp | Virtual Machine Remote Desktop |
| `3000/tcp` | open | http | Node.js Express framework |
| `3001/tcp` | open | ssl/http | Node.js Express framework over SSL/HTTP |
| `3389/tcp` | open | ms-wbt-server | Microsoft Remote Desktop Services |

The most interesting services from a security perspective are SMB on ports `139` and `445`, RDP on port `3389`, and the Node.js Express services on ports `3000` and `3001`.

<img src="assets/2. Slika.jfif" alt="Open ports and services" width="900">

## 3. Service and OS Enumeration

Nmap detected additional information about the target Windows machine.

Detected information included:

- Device type: general purpose
- Operating system: Microsoft Windows 10/11
- Computer name: `DESKTOP-FQR1PJ8`
- Product version: `10.0.22621`
- Network distance: 1 hop
- MAC vendor: LCFC(HeFei) Electronics Technology

This confirms that the Kali VM and the Windows host are on the same local network.

<img src="assets/3. Slika.jfif" alt="Service and OS enumeration" width="900">

## 4. SMB, RDP and Scan Completion

The scan returned SMB-related information about the target Windows machine.

Important SMB finding:

```text
Message signing enabled but not required
```

This means SMB signing is available, but the system does not strictly require it.

Nmap also detected Remote Desktop Services on port `3389/tcp`.

```text
3389/tcp open ms-wbt-server Microsoft Terminal Services
```

RDP should usually be restricted to trusted devices only.

The scan completed successfully and confirmed that one host was up.

```text
Nmap done: 1 IP address (1 host up) scanned
```

<img src="assets/4. Slika.jfif" alt="SMB RDP and scan completion" width="900">

## Key Findings

The scan discovered the following:

- The target host was online
- The target system appears to be Windows 10/11
- SMB services were exposed on ports `139` and `445`
- RDP was enabled on port `3389`
- Node.js Express services were running on ports `3000` and `3001`
- SMB message signing was enabled but not required
- The target was one hop away, confirming it was on the local network

## Security Recommendations

Based on the scan results, the following defensive steps are recommended:

- Disable SMB if file sharing is not needed
- Restrict SMB access to trusted devices only
- Require SMB signing where appropriate
- Disable RDP if it is not needed
- Restrict RDP access using Windows Firewall
- Keep Windows updated
- Keep Node.js applications updated
- Avoid exposing local development services to the entire network
- Use strong passwords for Windows accounts
- Review firewall rules regularly

## Ethical Notice

This lab was performed only in a private local network against my own Windows machine.

No exploitation, password attacks, or unauthorized access attempts were performed.

The purpose of this lab is educational and defensive: to understand network reconnaissance and how to identify exposed services on a system.

## Conclusion

This lab demonstrates how Nmap can be used to perform basic reconnaissance against a Windows host in a controlled environment.

The scan successfully identified open ports, running services, operating system details, SMB configuration, RDP availability, and local network distance.

## Screenshots Folder Structure

```text
screenshots/
├── 1. Slika.png
├── 2. Slika.jfif
├── 3. Slika.jfif
└── 4. Slika.jfif
```
