# 🔐 Cybersecurity Lab Environment Setup

Building an isolated virtual lab for penetration testing and ethical hacking practice.

<p align="center">
  <img src="https://img.shields.io/badge/Skill-Cybersecurity-red" alt="Skill Cybersecurity">
  <img src="https://img.shields.io/badge/Ver-Virtualbox_v7.2.22-0078D4" alt="Virtualbox v7.2.22">
 <img src="https://img.shields.io/badge/Kali_Linux-v2025.1-orange" alt="Kali Linux v2025.1">
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

The laboratory relies on a private virtual network architecture (`10.0.0.0/24`) designed to support communication between attack platforms and future target virtual machines.

## 🎯 Objectives

The main objectives of this project are to:
- Deploy Oracle VM VirtualBox hypervisor on a Parrot OS host system.
- Import and configure Kali Linux as the primary attacker environment.
- Construct an isolated custom NAT Network (`10.0.0.0/24`) for virtual machine communication.
- Assign a static IPv4 address (`10.0.0.2/24`) to Kali Linux for consistent network identity.
- Establish baseline recovery points using VirtualBox VM snapshots.
- Verify internet connectivity and external DNS resolution.
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
| 🧠 Kali RAM | 4,048 MB |
| 🌐 Virtual Network | NAT Network |
| 📡 Network Address | 10.0.0.0/24 |
| 🐧 Kali IP Address | 10.0.0.2/24 |
| 🚪 Default Gateway | 10.0.0.1 |
| 🌍 DNS Servers | 10.0.0.1, 8.8.8.8 |

## 🪜 Lab Setup Procedure

### Step 1. Install VirtualBox Hypervisor

Oracle VM VirtualBox 7.2 was installed and configured on the Parrot OS host environment.

### Step 2. Build the Isolated NAT Network

A dedicated virtual network was created within VirtualBox Global Tools to enable inter-VM communication and controlled outbound access.

**Network Configuration:**
- **Network Name:**cybersecurity_lab
- **Network CIDR:** 10.0.0.0/24
- **DHCP:** Enabled
- **IPv6:** Disabled

### Step 3. Deploy & Configure Kali Linux VM

The Kali Linux virtual machine was imported into VirtualBox and attached to the lab network.

**VM Settings:**
- **Allocated RAM:** 4,048 MB
- **Network Adapter 1:** Attached to NAT Network (`cybersecurity_lab`)
- **Adapter Type:** Intel PRO/1000 MT Desktop
- **System Integration:** Shared Clipboard (Bidirectional) and Drag-and-Drop enabled.

**Kali Linux Installation Evidence**

The screenshot below shows the Kali Linux virtual machine after installation and import into VirtualBox.

![Kali Linux installation](kali%20install.png)

### Step 4. Assign Static IPv4 Address

To ensure consistent network addressing across lab exercises, Kali Linux was assigned a static IP identity via NetworkManager (`nmcli`).

**Network Configuration:**
- **IP Address:** 10.0.0.2
- **Subnet Mask:** 255.255.255.0 (/24)
- **Gateway:** 10.0.0.1
- **DNS:** 10.0.0.1 and 8.8.8.8

**Static IP Configuration Command:**

```bash
sudo nmcli connection modify "Wired connection 1" ipv4.addresses 10.0.0.2/24 ipv4.gateway 10.0.0.1 ipv4.dns "10.0.0.1 8.8.8.8" ipv4.method manual
```

**IP Address Verification**

The following screenshot confirms that Kali Linux was assigned the configured static IP address.

![Verified IP address](verifed%20ip%20adress.png)

### Step 5. Verify Internet Access and DNS Resolution

Internet connectivity and DNS resolution were tested from the Kali Linux virtual machine.

**Connectivity Test Commands:**

```bash
ping -c 3 1.1.1.1
ping -c 3 google.com
```

Both tests completed successfully, confirming external network connectivity and DNS resolution.

**Verification Evidence**

![Internet access and DNS resolution](internet%20access%20%26%26%20DNS%20resolution.png)

### Step 6. Configure Shared Folder

convenient data exchange between the host and guest systems.
The shared folder was mounted in Kali Linux at `/media/sf_Downloads`.

**Shared Folder Evidence**

![Shared folder configuration](folder%20share.png)

### Step 7. Enable Clipboard and Drag-and-Drop

Shared Clipboard and Drag-and-Drop were configured in Bidirectional mode to support convenient text and file exchange between the host and guest systems.

**Configuration Evidence**

![Clipboard and Drag-and-Drop configuration](clipboard%20%26%20drag%E2%81%84drop.png)

### Step 8. Create VM Snapshots

Three VirtualBox snapshots were created at different stages of the lab setup to preserve recovery points:

1. `Fresh install` – Initial installation baseline.
2. `Ip configuration` – Saved state after IP configuration.
3. `phase 1 complete -baseline` – Baseline after completing the lab setup.

## 📊 Results

The following objectives were successfully achieved:

- VirtualBox installed and configured on Parrot OS.
- Kali Linux successfully imported and configured.
- Custom NAT Network established.
- Static IP address assigned to Kali Linux.
- Internet connectivity and DNS resolution verified.
- Shared folder configured between host and guest.
- Bidirectional clipboard and Drag-and-Drop tested.
- Three VirtualBox snapshots created at different stages of the setup.
  

## ⚠️ Challenges Encountered and Solutions

### 1. Slow Kali Linux Installation

During the Kali Linux installation process, particularly while installing system dependencies, the installation became extremely slow and took several hours. My system also shut down during multiple installation attempts.

**Solution:**

After three unsuccessful attempts, I disconnected my system from the network and restarted the installation. The dependency installation process then progressed significantly faster, allowing me to complete the setup.

**Lesson Learned:**

Installation delays can affect the deployment process. Troubleshooting the installation environment and adjusting the setup approach helped resolve the issue.

## 🔒 Security Considerations

- The virtual laboratory is intended for controlled and authorized security testing.
- Network configurations should be reviewed before introducing additional virtual machines.
- Snapshots provide recovery points before performing potentially disruptive security experiments.
- Testing against external systems must only be conducted with proper authorization.

---

👤 **Author:** Mercy Oyanimughan

📌 **Project Information:** Cybersecurity Lab Setup | Week 01 | Task WK1-PM1
