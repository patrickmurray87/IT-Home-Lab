# macOS Development Environment Setup

**Status:** ✅ Complete

**Difficulty:** Beginner

**Estimated Time:** 1–2 hours

**Last Updated:** August 2026

**Technologies Used**

- macOS
- Homebrew
- Git
- GitHub Desktop
- Visual Studio Code
- VMware Fusion
- Terminal
- Xcode Command Line Tools

---

# Objective

Prepare a macOS workstation for software development, virtualization, Linux administration, networking, and cybersecurity labs.

The workstation serves as the primary development platform for the IT Home Lab and provides the tools required for source control, virtual machine management, and technical documentation.

---

# Host System

| Component | Value |
|-----------|-------|
| Computer | Apple MacBook Air M2 |
| Memory | 16 GB |
| Storage | 512 GB SSD |
| Operating System | macOS |

---

# Software Installed

| Software | Purpose |
|----------|---------|
| Homebrew | Package manager for macOS |
| Git | Version control |
| GitHub Desktop | Git repository management |
| Visual Studio Code | Code editor and documentation |
| VMware Fusion | Virtual machine hypervisor |
| Xcode Command Line Tools | Required development tools for Homebrew and Git |

---

# Installation Process

## 1. Install Xcode Command Line Tools

Installed Apple's command line development tools.

These provide:

- Git
- C compiler
- Build tools
- Developer utilities required by Homebrew

Verified installation using:

```bash
xcode-select --install
```

---

## 2. Install Homebrew

Installed Homebrew using the official installation script.

Purpose:

- Install software from the Terminal
- Manage packages
- Simplify future software installation

Verified installation:

```bash
brew --version
```

Confirmed system health:

```bash
brew doctor
```

---

## 3. Install GitHub Desktop

Installed GitHub Desktop to simplify Git workflows.

Purpose:

- Clone repositories
- Commit changes
- Push updates
- Manage version control visually

---

## 4. Install Visual Studio Code

Installed VS Code as the primary editor.

Purpose:

- Technical documentation
- Markdown editing
- Source code editing
- Terminal integration

---

## 5. Install VMware Fusion

Installed VMware Fusion.

Purpose:

- Build Linux virtual machines
- Perform networking labs
- Test operating systems
- Practice system administration

This software became the foundation for the Ubuntu virtual machine project.

---

# Verification

Verified:

- Homebrew operational
- Git installed
- GitHub Desktop connected
- VS Code operational
- VMware Fusion installed
- Terminal functioning correctly

---

# Skills Practiced

- macOS Terminal
- Package management
- Development environment setup
- Version control fundamentals
- Virtualization preparation
- Software installation
- Technical documentation

---

# Lessons Learned

Prior to this project I viewed each application as a separate tool.

Completing this setup demonstrated how each component supports the overall development workflow.

Homebrew installs software.

Git tracks changes.

GitHub stores project history.

GitHub Desktop simplifies version control.

VS Code is used to create documentation and edit source files.

VMware Fusion provides isolated virtual environments for testing and learning.

Together these tools create a professional development environment that supports future Linux, networking, and cybersecurity projects.

---

# Project Outcome

A complete macOS development workstation was successfully configured.

This workstation now serves as the primary platform for virtualization, documentation, version control, and future cybersecurity labs.

---

# Next Steps

- Build Ubuntu virtual machine
- Configure SSH
- Capture network traffic with Wireshark
- Learn Linux administration
- Build Windows virtual machine

---

# Reflection

Before setting up this workstation, I viewed Git, VS Code, GitHub, Homebrew, and VMware Fusion as unrelated applications.

Building the development environment helped me understand how they work together as a complete workflow. Homebrew manages software, Git tracks changes, GitHub stores project history, VS Code is where development and documentation take place, and VMware Fusion provides isolated systems for learning and experimentation.

This project changed the way I think about building an IT environment—from installing individual applications to creating an integrated platform for continuous learning.