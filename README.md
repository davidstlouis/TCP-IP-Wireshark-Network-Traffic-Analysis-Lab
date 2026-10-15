# TCP/IP & Wireshark Network Analysis Lab

## Project Overview

This project demonstrates TCP/IP network traffic analysis and troubleshooting using Wireshark in a Windows client-server environment hosted in Microsoft Azure.

The objective was to capture and analyze network communication between a Windows 10 Enterprise client and Windows Server 2022, examine DNS resolution, identify TCP three-way handshakes, and troubleshoot network connectivity issues.

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


<img width="1470" height="956" alt="Screenshot 2026-10-15 at 6 39 24 PM" src="https://github.com/user-attachments/assets/ccf15d5a-75f9-40d8-aafa-ff08cb825757" />

---

## Step 2: Capture Network Traffic Using Wireshark

I installed Wireshark on the Windows 10 Enterprise client and selected the active network interface to capture traffic.

I examined packet information, including source and destination IP addresses, protocols, and network communication between the client and server.


<img width="1470" height="956" alt="Screenshot 2026-10-15 at 6 41 27 PM" src="https://github.com/user-attachments/assets/26b39a86-18c1-4ecc-aaa5-668cfd8bb073" />
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

<img width="1470" height="956" alt="Screenshot 2026-10-15 at 6 44 00 PM" src="https://github.com/user-attachments/assets/dbc46a7e-9aa9-4cda-9803-bee684fc4326" />

<img width="1470" height="956" alt="Screenshot 2026-10-15 at 6 44 09 PM" src="https://github.com/user-attachments/assets/bb8b698c-7dff-43bd-b771-1939a54b2f88" />


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

<img width="1470" height="956" alt="Screenshot 2026-10-15 at 6 49 47 PM" src="https://github.com/user-attachments/assets/f47a4e45-7247-41ea-b41e-fd889f41ccbc" />

<img width="1470" height="956" alt="Screenshot 2026-10-15 at 6 49 55 PM" src="https://github.com/user-attachments/assets/9665b328-a610-4d9f-b071-e857b985932b" />


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

<img width="1470" height="956" alt="Screenshot 2026-10-15 at 6 55 11 PM" src="https://github.com/user-attachments/assets/597f4751-4e92-4fe1-9d5c-4a44745fb216" />

<img width="1470" height="956" alt="Screenshot 2026-10-15 at 6 55 23 PM" src="https://github.com/user-attachments/assets/2e261970-5f5b-42b1-ba01-4cfe151bc856" />

---


