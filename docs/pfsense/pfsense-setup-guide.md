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
<div align="center">
  <img src="https://github.com/echointheshell/aegis-corp-soc-lab/blob/2bb37400c1bb01f0aa470ac447c4dcdeef49358a/assets/pfsense-license-accept.png" alt="Description" width="700" />
</div>
3. Select "Install pfSense"
<div align="center">
  <img src="https://github.com/echointheshell/aegis-corp-soc-lab/blob/fba923a1a991b6a1555f5f0a8e4f321ad8a7f5b1/assets/pfsense-install.png" alt="Description" width="700" />
</div>
4. Configure WAN interface to obtain IP via DHCP
<div align="center">
  <img src="https://github.com/echointheshell/aegis-corp-soc-lab/blob/fba923a1a991b6a1555f5f0a8e4f321ad8a7f5b1/assets/pfsense-wan-select.png" alt="Description" width="700" />
</div>
<div align="center">
  <img src="https://github.com/echointheshell/aegis-corp-soc-lab/blob/fba923a1a991b6a1555f5f0a8e4f321ad8a7f5b1/assets/pfsense-dhcp.png" alt="Description" width="700" />
</div>
6. Skip the LAN interface assignment (configure later)
<div align="center">
  <img src="https://github.com/echointheshell/aegis-corp-soc-lab/blob/fba923a1a991b6a1555f5f0a8e4f321ad8a7f5b1/assets/pfsense-lan-skip.png" width="700" />
</div>
7. Continue with installation process
<div align="center">
  <img src="https://github.com/echointheshell/aegis-corp-soc-lab/blob/fba923a1a991b6a1555f5f0a8e4f321ad8a7f5b1/assets/pfsense-continue-wan.png" alt="Description" width="700" />
</div>
8. Wait for Netgate ID verification (will timeout for CE edition)
<div align="center">
  <img src="https://github.com/echointheshell/aegis-corp-soc-lab/blob/fba923a1a991b6a1555f5f0a8e4f321ad8a7f5b1/assets/pfsense-netgate-check.png" alt="Description" width="700" />
</div>
9. Select "pfSense CE" when license check fails
<div align="center">
  <img src="https://github.com/echointheshell/aegis-corp-soc-lab/blob/fba923a1a991b6a1555f5f0a8e4f321ad8a7f5b1/assets/pfsense-install-ce.png" alt="Description" width="700" />
</div>
10. **File System Configuration:**
   - Accept ZFS (recommended)
   - Use GPT partitioning scheme
<div align="center">
  <img src="https://github.com/echointheshell/aegis-corp-soc-lab/blob/fba923a1a991b6a1555f5f0a8e4f321ad8a7f5b1/assets/pfsense-zfs-gpt.png" alt="Description" width="700" />
</div>
11. **Storage Configuration:**
    - Select striping (single disk setup)
    - Choose the main disk
    - **⚠️ Confirm data wipe** - this will erase the disk
<div align="center">
  <img src="https://github.com/echointheshell/aegis-corp-soc-lab/blob/fba923a1a991b6a1555f5f0a8e4f321ad8a7f5b1/assets/pfsense-stripe.png" alt="Description" width="700" />
</div>
<div align="center">  
  <img src="https://github.com/echointheshell/aegis-corp-soc-lab/blob/fba923a1a991b6a1555f5f0a8e4f321ad8a7f5b1/assets/pfsense-disk-select.png" alt="Description" width="700" />
</div>
12. **Version Selection:**
    - Select latest stable build (2.8.0 at time of writing)
<div align="center">
  <img src="https://github.com/echointheshell/aegis-corp-soc-lab/blob/fba923a1a991b6a1555f5f0a8e4f321ad8a7f5b1/assets/pfsense-version-select.png" alt="Description" width="700" />
</div>
13. **Installation Process:**
    - Wait for package downloads and installation
    - Select to reboot the system after installation has completed
<div align="center">
  <img src="https://github.com/echointheshell/aegis-corp-soc-lab/blob/fba923a1a991b6a1555f5f0a8e4f321ad8a7f5b1/assets/pfsense-installing.png" alt="Description" width="700" />
</div>
<div align="center">
  <img src="https://github.com/echointheshell/aegis-corp-soc-lab/blob/fba923a1a991b6a1555f5f0a8e4f321ad8a7f5b1/assets/pfsense-reboot.png" alt="Description" width="700" />
</div>
14. **Post-Installation Interface Setup:**
    - Select option **2** from console menu
    - Configure LAN interface: `192.168.10.1/24`
    - **Skip IPv6** configuration for this lab
    - **Decline DHCP server** setup (configure via web interface)
<div align="center">
  <img src="https://github.com/echointheshell/aegis-corp-soc-lab/blob/fba923a1a991b6a1555f5f0a8e4f321ad8a7f5b1/assets/pfsense-done.png" alt="Description" width="700" />
</div>
<div align="center">
  <img src="https://github.com/echointheshell/aegis-corp-soc-lab/blob/fba923a1a991b6a1555f5f0a8e4f321ad8a7f5b1/assets/pfsense-option-2.png" alt="Description" width="700" />
</div>
<div align="center">
  <img src="https://github.com/echointheshell/aegis-corp-soc-lab/blob/fba923a1a991b6a1555f5f0a8e4f321ad8a7f5b1/assets/pfsense-option-2-done.png" alt="Description" width="700" />
</div>
15. **Verification:**
    - Confirm interface assignments are correct
    - Note the web interface URL for next steps
<div align="center">
  <img src="https://github.com/echointheshell/aegis-corp-soc-lab/blob/fba923a1a991b6a1555f5f0a8e4f321ad8a7f5b1/assets/pfsense-finished.png" alt="Description" width="700" />
</div>

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
