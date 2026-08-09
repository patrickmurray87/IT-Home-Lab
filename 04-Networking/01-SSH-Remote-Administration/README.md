# SSH Remote Administration

**Status:** ✅ Complete

**Difficulty:** Beginner

**Estimated Time:** 1–2 hours

**Last Updated:** August 2026

**Technologies Used**

- OpenSSH
- Ubuntu 26.04 ARM
- macOS
- VMware Fusion
- Nmap
- Wireshark

---

# Objective

Configure Secure Shell (SSH) to remotely administer an Ubuntu virtual machine from a macOS host.

This project demonstrates the installation, configuration, verification, troubleshooting, and validation of a secure remote administration service within a virtual lab environment.

---

# Lab Environment

| Component | Value |
|-----------|-------|
| Host System | macOS |
| Guest System | Ubuntu 26.04 ARM |
| Hypervisor | VMware Fusion |
| Network | VMware NAT |
| Remote Protocol | SSH |
| Transport Protocol | TCP |
| Default Port | 22 |

---

# Network Topology

```
MacBook Air (macOS)
        │
        │ SSH (TCP Port 22)
        ▼
Ubuntu 26.04 ARM Virtual Machine
```

The Ubuntu virtual machine was connected to VMware's NAT network, allowing secure communication between the macOS host and Linux guest while remaining isolated from the physical network.

---

# Skills Practiced

- OpenSSH Server installation
- Remote administration
- Linux service management
- Network troubleshooting
- Port verification
- Nmap scanning
- Wireshark packet analysis
- Linux command-line administration

---

# Implementation

## 1. Verify Network Connectivity

Confirmed the Ubuntu virtual machine had received an IP address.

```bash
ip addr
```

Verified the routing table.

```bash
ip route
```

Confirmed connectivity from the macOS host.

```bash
ping 172.16.60.128
```

---

## 2. Install OpenSSH Server

Installed the OpenSSH Server package.

```bash
sudo apt install openssh-server
```

---

## 3. Verify Service Status

Confirmed the SSH service was installed and operational.

```bash
systemctl status ssh
```

Started the service if required.

```bash
sudo systemctl start ssh
```

---

## 4. Verify Listening Port

Confirmed that the SSH daemon was listening on TCP port 22.

```bash
sudo ss -tlpn
```

Observed:

```
0.0.0.0:22
```

This confirmed that the SSH service was actively accepting incoming connections.

---

## 5. Verify with Nmap

Performed a network scan against the Ubuntu virtual machine.

```bash
nmap 172.16.60.128
```

Result:

```
22/tcp open ssh
```

This independently verified that the SSH service was reachable across the network.

---

## 6. Connect from macOS

Established a remote session from the macOS Terminal.

```bash
ssh patrick@172.16.60.128
```

Accepted the server fingerprint during the initial connection.

Authenticated using the Ubuntu user password.

After authentication, a secure remote shell was successfully established.

---

## 7. Verify Remote Session

Executed several commands remotely to verify functionality.

```bash
hostname
pwd
whoami
ls
```

These commands confirmed:

- Successful authentication
- Remote command execution
- Access to the user's home directory
- Proper communication between the host and guest systems

---

# Wireshark Analysis

Captured SSH traffic using Wireshark while establishing the remote session.

Observed:

- TCP three-way handshake
- SSH protocol negotiation
- Encrypted client/server communication
- Bidirectional packet exchange over TCP port 22

Although the packet contents could not be read, this demonstrated one of SSH's primary security features: encrypted communication between client and server.

---

# Troubleshooting

## Initial Authentication Failure

### Problem

The first SSH connection attempts failed during authentication.

---

### Investigation

Rather than assuming a single cause, each dependency was verified individually.

Validated:

- IP address
- Routing table
- Network connectivity
- Firewall status
- SSH service
- Listening ports
- SSH logs

This systematic approach confirmed that the network and SSH service were functioning correctly.

---

### Root Cause

The authentication failure was ultimately traced to an incorrect password entry rather than a network or configuration problem.

Correcting the password resulted in a successful SSH connection.

---

### Key Takeaway

Working through each layer independently prevented unnecessary configuration changes and reinforced the value of structured troubleshooting.

---

# Verification

The project was considered successful after confirming:

- SSH service installed
- SSH service running
- TCP port 22 listening
- Nmap detected an open SSH service
- Successful remote login from macOS
- Remote commands executed successfully
- SSH traffic captured in Wireshark

---

# Commands Used

```bash
ip addr
ip route
ping
sudo apt install openssh-server
systemctl status ssh
sudo systemctl start ssh
sudo ss -tlpn
nmap 172.16.60.128
ssh patrick@172.16.60.128
hostname
pwd
whoami
ls
```

---

# Lessons Learned

This project demonstrated that successful remote administration depends on multiple services functioning together.

A successful SSH connection requires:

- Network connectivity
- Proper IP addressing
- Valid routing
- A running SSH service
- An open listening port
- Successful authentication

Verifying each layer individually proved to be significantly more effective than guessing or making configuration changes without evidence.

---

# Reflection

Prior to this project, I understood SSH as a command used to remotely access another computer.

Completing this lab provided a deeper understanding of the technologies operating behind the scenes, including networking, service management, authentication, encryption, and remote administration.

Perhaps the most valuable lesson was learning that effective troubleshooting is a structured process rather than trial and error. The same methodology used to diagnose this SSH issue can be applied to many other networking and systems administration problems.

---

# Project Outcome

Successfully configured secure remote administration between a macOS host and an Ubuntu virtual machine.

This project established the foundation for future Linux administration, networking, automation, and cybersecurity labs by enabling secure command-line access to the Linux environment.

---

# Next Steps

- Configure SSH key-based authentication
- Analyze the TCP three-way handshake in Wireshark
- Capture additional network protocols
- Perform advanced Nmap scans
- Build Windows-to-Linux remote administration labs