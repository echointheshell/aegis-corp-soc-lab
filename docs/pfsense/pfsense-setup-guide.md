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
  <img src="/assets/pfsense-license-accept.png" alt="Description" width="700" />
</div>
3. Select "Install pfSense"
4. Configure WAN interface to obtain IP via DHCP
5. Skip the LAN interface assignment (configure later)
6. Continue with installation process
7. Wait for Netgate ID verification (will timeout for CE edition)
8. Select "pfSense CE" when license check fails
9. **File System Configuration:**
   - Accept ZFS (recommended)
   - Use GPT partitioning scheme
10. **Storage Configuration:**
    - Select striping (single disk setup)
    - Choose the main disk
    - **⚠️ Confirm data wipe** - this will erase the disk
11. **Version Selection:**
    - Select latest stable build (2.8.0 at time of writing)
12. **Installation Process:**
    - Wait for package downloads and installation
    - Select to reboot the system after installation has completed
13. **Post-Installation Interface Setup:**
    - Select option **2** from console menu
    - Configure LAN interface: `192.168.10.1/24`
    - **Skip IPv6** configuration for this lab
    - **Decline DHCP server** setup (configure via web interface)
14. **Verification:**
    - Confirm interface assignments are correct
    - Note the web interface URL for next steps

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
