
# 🔐 Networkwalks-RobinVuru-B084-WK1-PM1-Cybersecurity-Lab-Setup

## 📌 1. Project Overview & Details

* **Author:** Robin Vuru
* **Batch/ID:** B084 (WK1-PM1)
* **Objective:** This project covers installing and configuring VirtualBox, importing Kali Linux as a VM, creating a private NAT Network, configuring Kali's network connectivity with a consistent static IP, verifying internet and DNS, taking a clean VM snapshot for recovery, and documenting the entire setup to prepare the environment for future cybersecurity projects.

---

## 💻 2. System Specifications & Network Architecture

| Component | Configuration Details |
| --- | --- |
| **Host System** | Windows 11 Laptop (Intel Core i7, 8 GB RAM) |
| **Hypervisor** | Oracle VirtualBox 7.2.22|
| **Guest OS** | Kali Linux 2026.3 |
| **Virtual Network Name** | `NatNetwork` |
| **IP Prefix** | `10.0.0.0/24` |
| **DHCP / IPv6** | DHCP: **Enabled** | IPv6: **Disabled** |
| **Primary Adapter Configuration** | `Wired connection 1` (Automatic DHCP) |
| **DNS Server** | `8.8.8.8` (Google Public DNS) |

---

## ⚙️ 3. Step-by-Step Implementation Procedure

### 🛠️ Step 1: Software Acquisition & Tooling

Downloaded and verified essential installation files for extraction, virtualization, and security testing.

#### **A. 7-Zip**

* **Resource:** [7-Zip Official Downloads](https://7-zip.org/download.html)
* **Purpose:** Archival tool installed initially to extract Kali Linux 2026.3.

> *Figure 1.1: 7-Zip Official Download Interface*

---

#### **B. Oracle VirtualBox**

* **Resource:** [VirtualBox Official Downloads](https://virtualbox.org/wiki/Downloads)
* **Purpose:** Type-2 Hypervisor managing virtual machines and private networks.

> *Figure 1.2: Oracle VirtualBox Platform Packages Download Page*

---

#### **C. Kali Linux**

* **Resource:** [Kali Linux Official Downloads](https://kali.org/get-kali)
* **Purpose:** Penetration testing Linux distribution equipped with security tools.
* ⚠️ **Note:** *Extract the downloaded Kali archive using 7-Zip prior to importing into VirtualBox.*

> *Figure 1.3: Kali Linux Pre-built Virtual Machine Selection*

---

### 🌐 Step 2: Virtual Machine & Network Configuration

1. **NAT Network Setup:** Built a custom NAT Network (`NatNetwork`) under `10.0.0.0/24` with local DHCP enabled to isolate traffic while providing outbound internet connectivity.

> *Figure 1.4:  Configuration Interface*
3.  **VM Import:** Imported the extracted Kali Linux image into VirtualBox and tuned base memory/processor parameters for optimal host balance.

> *Figure 1.5: Imported Interface*
4. **Guest Interface Tuning:** Verified `Wired connection 1` settings within Kali Linux to dynamically request an IP via DHCP and set DNS targeting `8.8.8.8`.

> *Figure 1.6: Configuration Interface*

```text
               Personal Laptop (Windows 11)
                     Intel Core i7 | 8 GB RAM
                                |
                                v
                       Oracle VirtualBox
                                |
                                v
               +----------------------------------+
               |      NatNetwork (10.0.0.0/24)    |
               |         DHCP Server Enabled      |
               +----------------------------------+
                                |
             +------------------+------------------+
             |                                     |
             v                                     v
     Kali Linux (VM)                       [Future Target VM]
  IP: Dynamic (DHCP)                      Metasploitable / DVWA
    DNS: 8.8.8.8

```

---

### 🔍 Step 3: Connectivity Verification Diagnostics

Ran core Linux CLI tools inside the Kali terminal to validate full stack connectivity:

* **Interface IP Check:** `ip -br addr` *(Confirmed assigned dynamic IPv4 address)*
* **Default Routing:** `ip route` *(Verified path to default gateway)*
* **DNS Resolution Config:** `cat /etc/resolv.conf` *(Confirmed active DNS point to `8.8.8.8`)*
* **Gateway Reachability:** `ping -c 4 <gateway-ip>`
* **Internet Reachability:** `ping -c 4 8.8.8.8`
* **Domain Name Resolution:** `getent hosts kali.org`
* **Tool Availability:** `nmap --version`

---

### 📸 Step 4: Baseline Recovery Snapshot

Created a clean recovery snapshot prior to initiating active security assessments to ensure quick system rollback.

* **Snapshot Name:** `Fresh Kali Linux_Robin Vuru- Task 1 Baseline`
* **Status:** Clean state saved and baseline verified.

---

## 🐞 4. Troubleshooting & Key Learnings

### 🔧 Troubleshooting Protocols

* **Connectivity Drops:** Verified adapter alignment to `NatNetwork` in VM settings and recycled NetworkManager services via CLI.
* **IP Collisions / Unexpected DHCP Leasing:** Cleaned stale DHCP leases and validated the scope range within VirtualBox Network Manager.
* **Hardware Virtualization Blockers:** Enabled Intel Virtualization Technology (**VT-x**) within system BIOS/UEFI settings to address hypervisor kernel module errors.

### 💡 Key Takeaways

1. **NAT Networking Isolation:** Understanding how shared virtual networks handle inter-VM communication alongside host outbound network translation.
2. **Network Diagnostics:** Proficiency with command-line tools (`ip`, `ping`, `getent`, `cat`) to verify network layers systematically.
3. **Snapshot Management:** Recognizing snapshots as critical safety mechanisms before conducting disruptive security tests.

---

## ⚖️ 5. Ethical Compliance & Future Roadmap

### 🛡️ Ethical Usage Notice

> All operational activities documented within this laboratory setup are strictly restricted to isolated, self-contained environments and owner-authorized target platforms. Unauthorized scanning or exploit delivery against external systems is strictly prohibited.

### 🚀 Future Roadmap & Next Steps

* 🎯 **Target Integration:** Deploy intentionally vulnerable endpoints (e.g., Metasploitable, OWASP Juice Shop).
* 📑 **Static IP Schema:** Configure persistent static addressing for multi-node lab exercises.
* 🔎 **Reconnaissance Practice:** Conduct host discovery, port scanning, and service enumeration using **Nmap**.
* 📊 **Traffic Analysis:** Capture and inspect raw packets using **Wireshark**.
* 🌐 **Web Security:** Perform authorized vulnerability scanning against local web applications.
