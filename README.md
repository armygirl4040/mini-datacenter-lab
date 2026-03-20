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
  Version 7.2.6 r172322  
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
6. Installed OpenSSH Server 

**Initial Commands Run:**
```bash
sudo apt update
sudo apt upgrade -y
hostnamectl
ip a

Absolutely, Lisa — you’re moving through this lab with real momentum, and you’re ready for the part that turns your project from “a couple of VMs” into an **actual mini data center**.

You’ve completed:

- **Phase 1:** Host setup  
- **Phase 2:** First Linux VM  

Now we step into **Phase 3**, which is where your environment becomes a *networked system* instead of isolated machines. This is the phase that shows hiring managers you understand how servers talk to each other, how networks are structured, and how to troubleshoot connectivity — all core data center skills.

Below is your full **Phase 3** written in clean, GitHub‑ready Markdown. You can paste this directly into your README.

---

# 🛰️ Phase 3: Networking Setup
## 🌐 **Network Types Created in VirtualBox**

### **1. NAT Network (Internet Access)**
Used for:
- Package updates  
- Downloading tools  
- External connectivity  

### **2. Host‑Only Network (Management Network)**
Used for:
- SSH access from your Windows laptop  
- Admin tasks  
- Monitoring  

### **3. Internal Network (Server‑to‑Server Traffic)**
Used for:
- VM‑to‑VM communication  
- Testing routing  
- Simulating private data center networks  

---

## 🛠️ **Network Configuration Steps**

### **Step 1 — Create Host‑Only Network**
1. Open **VirtualBox → Tools → Network**  
2. Select **Host‑Only Networks**  
3. Click **Create**  
4. Set:
   - IPv4: `192.168.56.1`
   - Netmask: `255.255.255.0`
   - DHCP: Off (you’ll assign static IPs)

### **Step 2 — Create Internal Network**
1. Open **VM Settings → Network**  
2. Adapter 2 → Enable  
3. Attached to: **Internal Network**  
4. Name: `intnet-lab`

### **Step 3 — Attach Networks to VM**
For `lab-server-01`:
- **Adapter 1:** NAT  
- **Adapter 2:** Host‑Only  
- **Adapter 3:** Internal Network  

This gives your VM:
- Internet  
- Management access  
- Private server‑to‑server communication  

---

## 🧩 **Assign Static IP Addresses**

Edit the Netplan config:

```
sudo nano /etc/netplan/00-installer-config.yaml
```

Example configuration:

```
network:
  version: 2
  ethernets:
    enp0s3:
      dhcp4: true        # NAT
    enp0s8:
      dhcp4: false       # Host-only
      addresses:
        - 192.168.56.10/24
    enp0s9:
      dhcp4: false       # Internal network
      addresses:
        - 10.10.10.10/24
```

Apply changes:

```
sudo netplan apply
```

---

## 🧪 **Connectivity Tests**

### **Check IPs**
```
ip a
```

### **Ping the gateway**
```
ping 192.168.56.1
```

### **Test internet**
```
ping google.com
```

### **Test internal network**
(Once you add a second VM)
```
ping 10.10.10.11
```

---

## 📝 **Troubleshooting Notes**


