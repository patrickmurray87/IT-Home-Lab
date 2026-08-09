# Ubuntu 26.04 ARM Virtual Machine Installation

**Status:** ✅ Complete

**Difficulty:** Beginner

**Estimated Time:** 2–3 hours

**Last Updated:** August 2026

**Technologies Used**

- VMware Fusion
- Ubuntu 26.04 ARM
- macOS
- OpenSSH
- Nmap
- APT
- Wireshark

## Objective

Build an Ubuntu 26.04 ARM virtual machine on an Apple Silicon MacBook Air using VMware Fusion to create a Linux environment for learning CompTIA Network+, Security+, Linux fundamentals, networking, and cybersecurity.

This virtual machine serves as the primary Linux system for future networking, SSH, Nmap, Wireshark, and scripting labs.

---

# Lab Environment

## Host System

| Component | Value |
|-----------|-------|
| Computer | Apple MacBook Air M2 |
| Memory | 16 GB |
| Storage | 512 GB SSD |
| Host Operating System | macOS |

## Virtual Machine

| Component | Value |
|-----------|-------|
| Hypervisor | VMware Fusion |
| Guest OS | Ubuntu 26.04 LTS ARM64 |
| Architecture | ARM (aarch64) |

# Virtual Machine Configuration

| Setting | Value |
|---------|-------|
| Hypervisor | VMware Fusion |
| Guest Operating System | Ubuntu 26.04 LTS ARM64 |
| Network Mode | Private to My Mac (VMware NAT) |
| CPU | Default VMware Allocation |
| Memory | Default VMware Allocation |
| Storage | Virtual Disk (Default Configuration) |

The virtual machine was configured using VMware Fusion on an Apple Silicon MacBook Air. A NAT-based virtual network was selected to allow communication between the macOS host and Ubuntu guest while keeping the virtual machine isolated from the physical network.

---

# Installation Process

## 1. Download Ubuntu

Downloaded the Ubuntu 26.04 ARM64 ISO from Ubuntu's official website.

Initially attempted to use VMware's automatic download feature, but the operating system was not detected correctly.

The issue was resolved by manually downloading the ARM64 ISO and creating the virtual machine using the downloaded image.

---

## 2. Create Virtual Machine

Created a new virtual machine in VMware Fusion.

Configured:

- Ubuntu ARM64 ISO
- Default virtual hardware
- NAT networking ("Share with my Mac")

---

## 3. Install Ubuntu

Completed the standard Ubuntu installation.

Configuration included:

- Local user account
- Standard desktop installation
- Automatic partitioning
- Default package selection

After installation the VM booted successfully into Ubuntu Desktop.

---

## 4. Verify Networking

Verified that the virtual machine successfully obtained an IPv4 address from VMware's virtual NAT network.

```bash
ip addr
```

Example output:

```
172.16.60.128/24
```

Verified the routing table.

```bash
ip route
```

---

## 5. Update Package Lists

Updated package repositories.

```bash
sudo apt update
```

Initially the Ubuntu security repository timed out.

The issue resolved itself on a later attempt and package installation proceeded normally.

---

## 6. Install Nmap

Installed Nmap using APT.

```bash
sudo apt install nmap
```

Verified installation.

```bash
nmap localhost
```

---

## 7. Examine Open Ports

Used the following command to identify listening services.

```bash
ss -tuln
```

Observed services including:

- DNS
- IPP (printing)

At this stage SSH was not yet installed.

---

## 8. Install OpenSSH Server

Installed OpenSSH Server.

```bash
sudo apt install openssh-server
```

Verified service status.

```bash
systemctl status ssh
```

Started the service.

```bash
sudo systemctl start ssh
```

Verified the service was actively listening on TCP port 22.

---

## 9. Verify SSH Service

Confirmed the SSH daemon was listening.

```bash
sudo ss -tlpn
```

Observed:

```
0.0.0.0:22
```

Performed a port scan.

```bash
nmap 172.16.60.128
```

Result:

```
22/tcp open ssh
```

---

## 10. Remote Login from macOS

Connected from the host Mac using SSH.

```bash
ssh patrick@172.16.60.128
```

Accepted the server fingerprint.

Authenticated using the Ubuntu user password.

Successfully established a remote shell.

Verified functionality by running:

```bash
hostname
pwd
whoami
ls
```

---

# Post-Installation Configuration

After the base operating system was successfully installed, the following configuration tasks were completed to prepare the virtual machine for future networking and cybersecurity labs.

**Completed Tasks**

- Updated package repositories
- Installed Nmap
- Installed OpenSSH Server
- Started the SSH service
- Verified SSH was listening on TCP port 22
- Verified communication between the macOS host and Ubuntu guest
Successfully established an encrypted remote shell session from the macOS host.

---

# Snapshot Strategy

After verifying that Ubuntu was operating correctly and SSH connectivity had been established, a VMware snapshot was created to preserve a known-good baseline.

**Purpose**

- Preserve a clean operating system installation
- Allow rapid recovery during future labs
- Reduce rebuild time after configuration errors
- Maintain a repeatable starting point for future networking and cybersecurity exercises

This snapshot represents the baseline configuration for the IT Home Lab.

---

# Verification

The virtual machine deployment was considered successful after completing the following validation steps:

- Ubuntu booted normally
- Network connectivity established
- Internet access functional
- Nmap installed
- SSH server installed
- Port 22 listening
- Remote SSH session established from macOS

---

# Troubleshooting

## VMware Automatic Installation

### Problem

VMware failed to recognize Ubuntu automatically.

### Resolution

Downloaded the ARM64 ISO manually and recreated the VM.

---

## Ubuntu Repository Timeout

### Problem

APT update timed out when contacting the Ubuntu security repository.

### Resolution

Retried package operations later after connectivity recovered.

---

## SSH Authentication

### Problem

Initial SSH attempts failed.

### Investigation

Verified:

- VM IP address
- Routing table
- Firewall status
- SSH service
- Listening ports
- SSH logs

Initial SSH attempts required systematic troubleshooting. Connectivity, routing, firewall status, listening services, and SSH logs were verified before discovering that the authentication issue was caused by an incorrect password entry. This reinforced the importance of troubleshooting methodically and validating each layer before drawing conclusions about the root cause.

---

## VMware Networking

Initially experienced communication issues between macOS and Ubuntu.

Verified:

- NAT networking
- IP addressing
- VMware bridge interfaces
- SSH listener
- Connectivity using ping

After correcting the VM networking configuration, SSH communication succeeded.

---

# Commands Used

###Network Configuration

```bash
ip addr
ip route
ping
```

###Service Management

```bash
systemctl status ssh
sudo systemctl start ssh
```

###Network Analysis 

```bash
ss -tuln
sudo ss -tlpn
nmap localhost
nmap 172.16.60.128
```

###Package Management

```bash
sudo apt update
sudo apt install nmap
sudo apt install openssh-server
```

###Remote Administration

```bash
ssh patrick@172.16.60.128
hostname
pwd
whoami
ls
```

---

# Skills Practiced

- Installing a virtual machine
- Working with ARM operating systems
- VMware Fusion configuration
- Linux installation
- Package management using APT
- Linux networking
- SSH server configuration
- Service management with systemctl

---

# Lessons Learned

This lab demonstrated how virtual machines communicate across virtual networks and how SSH enables secure remote administration.

It also reinforced that troubleshooting should follow a structured process rather than guessing.

The most valuable lesson was verifying each layer independently:

1. Network connectivity
2. IP addressing
3. Firewall status
4. Listening services
5. Application configuration
6. Authentication

Following this process isolated the issue quickly and resulted in a successful SSH connection.

# Reflection

Before this project, I understood SSH as a protocol and tool for securely accessing another computer remotely, but I didn't understand everything that had to happen behind the scenes for it to work. Working through this lab showed me that a successful SSH connection depends on multiple layers—including networking, routing, a running service, an open listening port, and authentication. Working through each layer methodically helped me understand not only how SSH works, but also how a structured troubleshooting process can be applied to virtually any networking problem.

---

# Project Outcome

This project established the Linux foundation for the IT Home Lab.

Completing this project provided practical experience with virtualization, Linux installation, package management, remote administration, network troubleshooting, and technical documentation.

The completed virtual machine now serves as the primary Linux environment for future networking, cybersecurity, and systems administration projects.

---

# Next Steps

- Capture SSH traffic with Wireshark
- Analyze the TCP three-way handshake
- Perform Nmap scans
- Practice Linux file system commands
- Build additional networking labs
- Build a Windows virtual machine for cross-platform networking labs

---

*End of Project Documentation*
