# Wireshark Packet Analysis

**Status:** ✅ Complete

**Difficulty:** Beginner

**Estimated Time:** 30–45 minutes

**Last Updated:** August 2026

## Technologies Used

- Wireshark
- SSH
- TCP/IP
- Ubuntu 26.04 ARM
- macOS
- VMware Fusion

---

# Objective

Capture and analyze SSH traffic between the macOS host and an Ubuntu virtual machine using Wireshark to understand how network communication appears at the packet level.

This project focused on observing encrypted SSH traffic, identifying client/server communication, and becoming familiar with Wireshark's interface and filtering capabilities.

---

# Lab Environment

| Component | Value |
|-----------|-------|
| Host | Apple MacBook Air M2 |
| Guest | Ubuntu 26.04 ARM |
| Hypervisor | VMware Fusion |
| Network | VMware NAT |
| Analysis Tool | Wireshark |

---

# Lab Tasks

Completed the following:

- Captured live network traffic
- Applied display filters
- Identified SSH packets
- Observed client/server communication
- Verified TCP port 22 traffic
- Examined packet details
- Viewed Ethernet, IP, TCP, and SSH protocol layers

---

# Capture Process

## Start Packet Capture

Started Wireshark on the VMware virtual network interface.

Generated SSH traffic by connecting from macOS to the Ubuntu virtual machine.

```bash
ssh patrick@172.16.60.128
```

---

## Filter SSH Traffic

Applied the display filter:

```text
tcp.port == 22
```

This isolated the SSH session from the remaining network traffic.

---

## Analyze Packet Details

Examined several protocol layers including:

- Ethernet II
- IPv4
- TCP
- SSH

Observed communication between:

```
172.16.60.1
↓

172.16.60.128
```

After authentication, packet contents appeared as encrypted SSH payloads.

---

# Observations

During analysis, the following behaviors were observed:

- TCP packets traveled between the host and virtual machine.
- SSH communication occurred over TCP port 22.
- Packet payloads were encrypted after authentication.
- Client and server exchanged encrypted packets throughout the session.
- Wireshark clearly displayed the protocol stack for each packet.

---

# Verification

Successfully verified:

- Packet capture functioning
- VMware virtual networking
- SSH communication
- TCP port 22 traffic
- Encrypted SSH session
- Packet inspection using Wireshark

---

# Skills Practiced

- Packet capture
- Wireshark navigation
- Display filters
- Protocol identification
- TCP analysis
- SSH traffic analysis
- Basic network troubleshooting

---

# Lessons Learned

This project demonstrated that although SSH encrypts application data, Wireshark can still reveal valuable metadata including:

- Source and destination IP addresses
- Port numbers
- Protocol hierarchy
- Packet timing
- TCP sequence and acknowledgment numbers

Understanding this distinction reinforced the importance of encryption while also demonstrating how network administrators can troubleshoot encrypted protocols without viewing sensitive application data.

---

# Reflection

Before completing this lab, Wireshark appeared overwhelming due to the volume of captured traffic.

Learning how to apply display filters transformed the analysis process by isolating the packets relevant to the SSH session. This made it much easier to follow client-server communication and understand how encrypted protocols appear on the network.

This project also reinforced the relationship between concepts previously studied for CompTIA Network+, including TCP, IP addressing, ports, and secure remote administration.

---

# Next Steps

- Analyze the TCP three-way handshake
- Capture ICMP traffic
- Compare SSH and HTTP traffic
- Analyze DNS queries
- Capture DHCP traffic