# Networkwalks-RobinVuru-B084-WK1-PM1-Cybersecurity-Lab-Setup
Project Overview & Details

Author: Robin Vuru.

Objective: Set up a virtualized cybersecurity laboratory on a Windows 11 host using Oracle VirtualBox and Kali Linux for ethical hacking, networking, and security testing.

System Specifications & Network Architecture

Host System: Windows 11 personal laptop powered by an Intel Core i7 processor with 8 GB RAM.

Virtual Environment: Oracle VirtualBox running Kali Linux on a custom NAT Network named NatNetwork.

IP Address Configuration: Network prefix set to 10.0.0.0/24 with DHCP enabled and IPv6 disabled. Kali Linux is set to automatically acquire its IP (Wired connection 1) with DNS specified as 8.8.8.8.

Implementation Steps

Software Acquisition: Downloaded and installed 7-Zip, Oracle VirtualBox, and Kali Linux.
Download 
1. 7zip- https://7-zip.org/download.html
<img width="600" height="500" alt="image" src="https://github.com/user-attachments/assets/405fd6a6-2f2b-43f9-8d91-3a20feb1c056" />


3. VirtualBox- https://virtualbox.org/wiki/Downloads
4. Kali Linux- https://kali.org/get-kali

VM & Network Setup: Imported Kali Linux into VirtualBox and configured the dedicated NatNetwork parameters.

Network Configuration: Verified automatic DHCP settings and primary adapter settings within Kali Linux.

Connectivity Verification: Executed standard Linux CLI diagnostics (ip -br addr, ip route, cat /etc/resolv.conf, ping, getent hosts, and nmap --version) to verify local IP configuration, default gateway reachability, public Internet connectivity, and DNS resolution.

Snapshot Baseline: Created a clean baseline recovery snapshot named Fresh Kali Linux_Robin Vuru- Task 1 Baseline to allow quick restoration prior to running future lab tests.

Troubleshooting & Key Lessons

Detailed diagnostic workflows for resolving common virtual lab issues, such as lost internet connectivity, unexpected DHCP IP assignments, and CPU virtualization (VT-x) settings in BIOS/UEFI.

Practical insights gained in NAT networking, DHCP/DNS mechanics, command-line network diagnostics, and environment backup strategies.

Ethical Compliance & Future Roadmap

Ethics: Strictly restricted to authorized local testing, owner-permitted target systems, and isolated VM configurations.

Next Steps: Integrate intentionally vulnerable target VMs (e.g., Metasploitable), establish static IP planning, practice Nmap scanning, analyze traffic via Wireshark, and perform web application security testin
