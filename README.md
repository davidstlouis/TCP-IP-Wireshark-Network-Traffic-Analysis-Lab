# TCP/IP & Wireshark Network Traffic Analysis Lab

## Project Overview

This project demonstrates basic network traffic analysis and troubleshooting using Wireshark and Windows networking utilities.

The objective was to capture and analyze TCP/IP network packets, examine DNS resolution, identify the TCP three-way handshake, compare TCP and UDP traffic, and troubleshoot common network connectivity issues.

This lab simulates real-world networking tasks performed by IT Support Specialists, Network Technicians, and System Administrators.

## Technologies Used

- Wireshark
- TCP/IP Networking
- Windows Command Prompt
- Windows PowerShell
- DNS
- ICMP
- TCP & UDP

---

## Lab Environment

```text
Windows Computer
│
├── Wireshark
│   ├── Packet Capture
│   ├── Protocol Filtering
│   └── Traffic Analysis
│
├── Command Prompt / PowerShell
│   ├── ping
│   ├── nslookup
│   ├── ipconfig
│   ├── tracert
│   └── Test-NetConnection
│
└── Network
    ├── DNS Server
    └── Web Server
```

## Step 1: Capture Network Traffic

I installed Wireshark and selected my active network adapter to capture network traffic.

I examined packet information, including source and destination IP addresses, protocols, and packet details.

**Screenshot:**

<!-- Insert Wireshark packet capture screenshot here -->

---

## Step 2: Analyze ICMP Traffic

I generated ICMP traffic using the Windows `ping` command.

```cmd
ping 1.1.1.1
```

I applied the following Wireshark display filter:

```text
icmp
```

I examined ICMP Echo Request and Echo Reply packets to understand how devices test network reachability.

**Screenshot:**

<!-- Insert ICMP Echo Request and Reply screenshot here -->

---

## Step 3: Analyze DNS Traffic

I used `nslookup` to generate DNS queries and analyze the name resolution process.

```cmd
nslookup example.com 1.1.1.1
```

Wireshark display filter:

```text
dns
```

I identified DNS queries, responses, DNS server addresses, and the IP addresses returned during name resolution.

**Screenshot:**

<!-- Insert DNS query and response screenshot here -->

---

## Step 4: Analyze the TCP Three-Way Handshake

I generated TCP traffic using PowerShell:

```powershell
Test-NetConnection example.com -Port 80
```

Wireshark display filter:

```text
tcp.port == 80
```

I examined the three stages of the TCP connection process:

1. **SYN:** Client requests a connection.
2. **SYN-ACK:** Server acknowledges the request.
3. **ACK:** Client acknowledges the response and establishes the connection.

I also used the following filter to identify initial TCP connection requests:

```text
tcp.flags.syn == 1 && tcp.flags.ack == 0
```

**Screenshot:**

<!-- Insert TCP three-way handshake screenshot here -->

---

## Step 5: Compare TCP and UDP Traffic

I analyzed the differences between TCP and UDP using Wireshark display filters.

| Protocol | Display Filter | Description |
|---|---|---|
| TCP | `tcp` | Connection-oriented protocol with acknowledgments and retransmission mechanisms |
| UDP | `udp` | Connectionless protocol with minimal overhead |
| DNS | `dns` | Resolves domain names into IP addresses |
| ICMP | `icmp` | Used for network diagnostics and error reporting |

This helped me understand how different network protocols support communication between devices.

**Screenshot:**

<!-- Insert TCP and UDP comparison screenshot here -->

---

## Step 6: Network Connectivity Troubleshooting

I used Windows networking commands to investigate connectivity and name resolution.

**View network configuration:**

```cmd
ipconfig /all
```

**Test network reachability:**

```cmd
ping 1.1.1.1
```

**Test DNS resolution:**

```cmd
nslookup example.com
```

**Trace network routes:**

```cmd
tracert example.com
```

These commands helped me identify IP configuration details, test connectivity, verify DNS resolution, and examine network paths.

**Screenshot:**

<!-- Insert network troubleshooting screenshot here -->

---

## Step 7: Analyze Network Traffic Results

I reviewed captured packets and compared them with the results of my Windows networking commands.

| Test | What I Analyzed |
|---|---|
| ICMP | Echo Requests and Echo Replies |
| DNS | Queries, responses, and resolved IP addresses |
| TCP | SYN, SYN-ACK, and ACK packets |
| UDP | Connectionless datagram communication |
| Connectivity | IP addressing, DNS resolution, and network reachability |

This demonstrated how packet captures can help identify and troubleshoot network communication issues.

**Screenshot:**

<!-- Insert packet analysis results screenshot here -->

---

## Skills Demonstrated

- TCP/IP Networking
- Wireshark Packet Analysis
- Network Troubleshooting
- DNS Resolution
- TCP Three-Way Handshake
- TCP and UDP Protocol Analysis
- ICMP Connectivity Testing
- IP Addressing
- Network Diagnostics
- Windows Command Prompt
- Windows PowerShell

---

## What I Learned

This lab strengthened my understanding of TCP/IP networking and how devices communicate across networks.

I gained practical experience capturing and analyzing network packets, identifying common networking protocols, examining TCP connection establishment, and troubleshooting connectivity issues using Wireshark and Windows networking utilities.

These skills are directly applicable to IT Support, Help Desk, Network Support, and System Administrator positions.

---

## Author

**David Saint Louis**  
Information Technology / Cybersecurity

[LinkedIn](https://www.linkedin.com/in/david-saint-louis-)
