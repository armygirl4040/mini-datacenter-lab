# mini-datacenter-lab
Home lab simulating a small data center using VirtualBox, Linux VMs, and basic networking
# Mini Data Center Lab

This project simulates a small data center using VirtualBox, Linux virtual machines, and basic networking on a single laptop.

## Phase 1: Host setup

- Installed Oracle VM VirtualBox on Windows 11.
- Host machine:
  - CPU: [your CPU]
  - RAM: [your RAM]
  - Disk: [your disk size]

## Phase 2: First Linux VM

# Mini Data Center Lab

This project simulates a small data center environment using VirtualBox, Linux virtual machines, and basic networking. The goal is to build hands-on experience with virtualization, server setup, networking, troubleshooting, and documentation — the same foundational skills used in real data center operations.

---

## 📌 Project Overview

This home lab walks through the process of:

- Installing and configuring VirtualBox on a Windows 11 host
- Creating and configuring Linux virtual machines
- Setting up internal networking between VMs
- Testing connectivity and basic services
- Documenting issues, fixes, and lessons learned

Each phase is documented step-by-step to show the full workflow and thought process.

---

## 🧱 Phase 1: Host Setup

ASUS Laptop
- OS: Windows 11
- CPU: Intel Core i7-975OH
- RAM: 8 GB
- Disk: 475 GB

**Software Installed:**
- Oracle VM VirtualBox  
  - Version: *[Add version]*  
  - Installed using the official Windows installer

**Notes:**
- Verified VirtualBox opens correctly
- Pinned VirtualBox to taskbar for easy access
- Confirmed virtualization support is enabled in BIOS (if applicable)

---

## 🖥️ Phase 2: Creating the First Linux VM

**VM Details:**
- Name: `lab-server-01`
- OS: Ubuntu Server (latest LTS)
- CPU: 2 vCPUs
- RAM: 2–4 GB
- Disk: 20–25 GB (VDI, dynamically allocated)

**Steps Completed:**
1. Downloaded Ubuntu Server ISO
2. Created new VM in VirtualBox
3. Attached ISO as virtual optical drive
4. Booted VM and installed Ubuntu Server
5. Set hostname, user account, and password
6. Installed OpenSSH Server (optional but recommended)

**Initial Commands Run:**
```bash
sudo apt update
sudo apt upgrade -y
hostnamectl
ip a
