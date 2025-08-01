# pfSense Setup Guide

## Overview
pfSense serves as the central network gateway for the Aegis lab, providing:
- Network segmentation between LAB-WAN (VNET5) and LAB-LAN (VNET1)
- Firewall protection and traffic filtering
- NAT services for internal networks
- DHCP services for lab VMs
- DNS services for lab VMs

## Step 1: VM Creation

### VM Specifications
- **CPU**: 1 core
- **RAM**: 1 GB
- **Storage**: 20 GB
- **Network Adapters**: 2 (WAN & LAN)

### Network Adapter Configuration
- **Network Adapter 1 (NAT)**: Connected to VNET5 (WAN) - 172.16.50.0/24
- **Network Adapter 2 (Host-Only)**: Connected to VNET1 (LAN) - 192.168.10.0/24

## Step 2: pfSense Installation

1. Boot from the pfSense ISO
2. Accept the Copyright agreement


![Image](/assets/pfsense-license-accept.png)


3. Select "Install pfSense"


![Image](/assets/pfsense-install.png)


4. Configure WAN interface to obtain IP via DHCP


![Image](/assets/pfsense-wan-select.png)
![Image](/assets/pfsense-dhcp.png)


5. Skip the LAN interface assignment (configure later)


![Image](/assets/pfsense-lan-skip.png)


7. Continue with installation process


![Image](/assets/pfsense-continue-wan.png)


8. Wait for Netgate ID verification (will timeout for CE edition)


![Image](/assets/pfsense-netgate-check.png)


9. Select "pfSense CE" when license check fails


![Image](/assets/pfsense-install-ce.png)


10. **File System Configuration:**
   - Accept ZFS (recommended)
   - Use GPT partitioning scheme


![Image](/assets/pfsense-zfs-gpt.png)


11. **Storage Configuration:**
    - Select striping (single disk setup)
    - Choose the main disk
    - **⚠️ Confirm data wipe** - this will erase the disk


![Image](/assets/pfsense-disk-select.png)
![Image](/assets/pfsense-stripe.png)


12. **Version Selection:**
    - Select latest stable build (2.8.0 at time of writing)


![Image](/assets/pfsense-version-select.png)


13. **Installation Process:**
    - Wait for package downloads and installation
    - Select to reboot after installation


![Image](/assets/pfsense-installing.png)
![Image](/assets/pfsense-reboot.png)


14. **Post-Installation Interface Setup:**
    - Select option **2** from console menu
    - Configure LAN interface: `192.168.10.1/24`
    - **Skip IPv6** configuration for this lab
    - **Decline DHCP server** setup (configure via web interface)


![Image](/assets/pfsense-done.png)
![Image](/assets/pfsense-option-2.png)
![Image](/assets/pfsense-option-2-done.png)


15. **Verification:**
    - Confirm interface assignments are correct
    - Note the web interface URL for next steps


![Image](/assets/pfsense-finished.png)


## Step 3: Web Interface Configuration

**Access via:** https://192.168.10.1

### Initial Setup Wizard
- **Username:** admin
- **Password:** pfsense (change immediately)

### System Configuration
- [ ] **Hostname:** firewall
- [ ] **Domain:** aegiscorp.org  
- [ ] **Primary DNS:** 8.8.8.8
- [ ] **Secondary DNS:** 1.1.1.1

### Interface Configuration
#### WAN Interface (em0)
- **Type:** DHCP
- **Network:** 172.16.50.0/24
- **Gateway:** Auto-assigned

#### LAN Interface (em1)  
- **Static IP:** 192.168.10.1/24
- **DHCP Range:** 192.168.10.100 - 192.168.10.200
