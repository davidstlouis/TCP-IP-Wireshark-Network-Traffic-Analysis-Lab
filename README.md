# TCP/IP & Wireshark Network Analysis Lab

## Project Overview

This project demonstrates TCP/IP network traffic analysis and troubleshooting using Wireshark in a Windows client-server environment hosted in Microsoft Azure.

The objective was to capture and analyze network communication between a Windows 10 Enterprise client and Windows Server 2022, examine DNS resolution, identify TCP three-way handshakes, analyze SMB file-sharing traffic, and troubleshoot network connectivity issues.

This lab simulates real-world network troubleshooting tasks performed by IT Support Specialists, Network Technicians, and System Administrators.

## Technologies Used

- Microsoft Azure
- Windows Server 2022
- Windows 10 Enterprise
- Wireshark
- Active Directory Domain Services (AD DS)
- DNS
- TCP/IP
- ICMP
- SMB File Sharing
- Windows Command Prompt & PowerShell

---

## Lab Environment

```text
Microsoft Azure Virtual Network
│
├── Windows Server 2022
│   ├── Active Directory Domain Services
│   ├── Domain: mydomain.con
│   ├── DNS Server
│   └── SMB File Sharing
│
└── Windows 10 Enterprise
    ├── Domain-Joined Client
    ├── Wireshark
    └── Network Troubleshooting Tools
```

Both virtual machines communicate over a private Azure virtual network.

## Step 1: Verify Network Configuration

I used Windows networking commands to identify the IP configurations of both virtual machines.

```cmd
ipconfig /all
```

I verified the client and server IP addresses, DNS configuration, and network connectivity.

**Screenshot:**

<!-- Insert Windows Server and Windows 10 IP configuration screenshots here -->

---

## Step 2: Capture Network Traffic Using Wireshark

I installed Wireshark on the Windows 10 Enterprise client and selected the active network interface to capture traffic.

I examined packet information, including source and destination IP addresses, protocols, and network communication between the client and server.

**Screenshot:**

<!-- Insert Wireshark packet capture screenshot here -->

---

## Step 3: Analyze ICMP Traffic

I generated ICMP traffic from Windows 10 to Windows Server using the `ping` command.

```cmd
ping <SERVER_PRIVATE_IP>
```

Wireshark display filter:

```text
icmp
```

I examined ICMP Echo Request and Echo Reply packets to verify connectivity between both virtual machines.

**Screenshot:**

<!-- Insert ICMP Echo Request and Echo Reply screenshot here -->

---

## Step 4: Analyze DNS Traffic

I used `nslookup` to generate DNS queries against my Windows Server 2022 domain controller.

```cmd
nslookup mydomain.con <SERVER_PRIVATE_IP>
```

Wireshark display filter:

```text
dns
```

I analyzed DNS queries and responses to understand how the Windows 10 client resolves domain names using the Windows Server DNS service.

**Screenshot:**

<!-- Insert DNS query and response screenshot here -->

---

## Step 5: Analyze the TCP Three-Way Handshake

I generated a TCP connection from Windows 10 to the Windows Server SMB service using PowerShell.

```powershell
Test-NetConnection <SERVER_PRIVATE_IP> -Port 445
```

Wireshark display filter:

```text
tcp.port == 445
```

I examined the three stages of TCP connection establishment:

1. **SYN:** Windows 10 initiates a connection to Windows Server.
2. **SYN-ACK:** Windows Server acknowledges the connection request.
3. **ACK:** Windows 10 acknowledges the server's response.

This demonstrated how TCP establishes reliable connections between network devices.

**Screenshot:**

<!-- Insert TCP SYN, SYN-ACK, and ACK screenshot here -->

---

## Step 6: Analyze SMB File-Sharing Traffic

I accessed an existing shared folder hosted on Windows Server 2022 from my Windows 10 client.

```text
\\<SERVER_PRIVATE_IP>\IT
```

Wireshark display filter:

```text
smb2
```

I examined SMB2/SMB3 protocol messages associated with network file access, including:

- Negotiate Protocol
- Session Setup
- Tree Connect
- Create
- Read and Write operations

This demonstrated how Windows clients communicate with file servers to access shared resources.

**Screenshot:**

<!-- Insert SMB file-sharing packet capture screenshot here -->

---

## Step 7: Troubleshoot
