# 🔐 Cybersecurity Lab Environment Setup

Building an isolated virtual lab for penetration testing and ethical hacking practice.

<p align="center">
  <img src="https://img.shields.io/badge/Skill-Cybersecurity-red" alt="Skill Cybersecurity">
  <img src="https://img.shields.io/badge/Ver-Virtualbox_v7.2.22-0078D4" alt="Virtualbox v7.2.22">
  <img src="https://img.shields.io/badge/Kali_Linux-v2026.2-orange" alt="Kali Linux v2026.2">
  <img src="https://img.shields.io/badge/Skill-Linux-red" alt="Skill Linux">
  <img src="https://img.shields.io/badge/Network-10.0.0.0%2F24-009688" alt="Network 10.0.0.0/24">
  <img src="https://img.shields.io/badge/Penetration_Testing-red" alt="Penetration Testing">
  <br>
  <img src="https://img.shields.io/badge/Skill-Virtualization-red" alt="Skill Virtualization">
  <img src="https://img.shields.io/badge/GitHub-181717?logo=github&logoColor=white" alt="GitHub">
  <img src="https://img.shields.io/badge/Host-Parrot_OS-red" alt="Host Parrot OS">
  <img src="https://img.shields.io/badge/Ethical_Hacking-orange" alt="Ethical Hacking">
  <img src="https://img.shields.io/badge/-Mercy_Oyanimughan-CC0000" alt="Mercy Oyanimughan">
</p>

## 📌 Project Overview

This project documents the installation and configuration of an isolated virtual cybersecurity and penetration-testing laboratory using **VirtualBox** hosted on **Parrot OS**. 

The goal of this setup is to establish a secure, controlled sandbox environment for executing network scans, conducting vulnerability assessments, analyzing traffic, and testing security tools without exposing external networks to risk.

The laboratory relies on a private virtual network architecture (`10.0.0.0/24`) designed to support seamless communication between attack platforms and future target virtual machines.

## 🎯 Objectives

The main objectives of this project are to:
- Deploy Oracle VM VirtualBox hypervisor on a Parrot OS host system.
- Import and configure Kali Linux as the primary attacker environment.
- Construct an isolated custom NAT Network (`10.0.0.0/24`) for virtual machine communication.
- Assign a static IPv4 address (`10.0.0.2/24`) to Kali Linux for consistent network identity.
- Establish baseline recovery points using VirtualBox VM snapshots.
- Verify internal routing, gateway reachability, and external DNS resolution.
- Document the full deployment process for professional portfolio standards.

## 🛡️ Purpose of the Lab

This laboratory provides a safe, contained setup for hands-on learning and ethical security testing.

Key use cases include:
- Network mapping and port scanning
- Vulnerability scanning and assessment
- Packet capture and traffic analysis
- Web application security testing
- Practical exploitation and tool experimentation

> ⚠️ **Important:** This laboratory environment must only be used for authorized security testing on systems you own or have explicit written permission to test.

## ⚙️ Lab Configuration

| Component | Configuration |
| :--- | :--- |
| 🖥️ Host OS | Parrot OS |
| 🧰 Hypervisor | VirtualBox 7.2 |
| 🐉 Security OS | Kali Linux |
| 🧠 Kali RAM | 2048 MB |
| 🌐 Virtual Network | NAT Network |
| 📡 Network Address | 10.0.0.0/24 |
| 🐧 Kali IP Address | 10.0.0.2/24 |
| 🚪 Default Gateway | 10.0.0.1 |
| 🌍 DNS Server | 8.8.8.8 |
| 🔮 Future VM Range | 10.0.0.3–10.0.0.99 |

## 🪜 Lab Setup Procedure

### Step 1. Install VirtualBox Hypervisor
Oracle VM VirtualBox 7.2 was verified and configured on the Parrot OS host environment.

### Step 2. Build the Isolated NAT Network
A dedicated virtual network was created within VirtualBox Global Tools to enable inter-VM communication and controlled outbound access.

**Network Configuration:**
- **Network Name:** NatNetwork
- **Network CIDR:** 10.0.0.0/24
- **DHCP:** Enabled
- **IPv6:** Disabled

### Step 3. Deploy & Configure Kali Linux VM
The Kali Linux virtual machine was imported into VirtualBox and attached to the lab network.

**VM Settings:**
- **Network Adapter 1:** Attached to NAT Network (`NatNetwork`)
- **Adapter Type:** Intel PRO/1000 MT Desktop
- **System Integration:** Shared Clipboard (Bidirectional) and Drag-and-Drop enabled.

### Step 4. Assign Static IPv4 Address
To ensure consistent network addressing across lab exercises, Kali Linux was assigned a static IP identity via NetworkManager (`nmcli`):
- **IP Address:** 10.0.0.2
- **Subnet Mask:** 255.255.255.0 (/24)
- **Gateway:** 10.0.0.1
- **DNS:** 8.8.8.8

### Step 5. Create Baseline VM Snapshot
Once initial connectivity was confirmed, a VirtualBox snapshot named `Fresh Installation Baseline` was captured to allow clean recovery states.

---
👤 **Author:** Mercy Oyanimughan  
📌 **Project Information:** Cybersecurity Lab Setup | Week 01 | Task WK1-PM1
