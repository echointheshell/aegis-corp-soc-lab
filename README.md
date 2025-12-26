# 🛡️ Aegis Corporation Lab

The Aegis Corporation Lab is a virtualized environment designed to simulate a mini segmented enterprise network with integrated security monitoring, adversary emulation, and infrastructure as code capabilities.
The aim is to provide an isolated and controlled sandbox for hands on exposure to detection engineering, incident response automation, and adversary tradecraft using industry frameworks such as MITRE ATT&CK.

## 🏗️ Architecture

![Lab Network Diagram](assets/lab-diagram-v4.0.png)

### Network Segments
- **VNET10**: `172.16.50.0/24` - External networks/Gateway (WAN)
- **VNET1**: `192.168.10.0/24` - User devices (LAN)
- **VNET2**: `192.168.20.0/24` - Server infrastructure (LAN)
- **VNET3**: `192.168.30.0/24` - External-facing services (DMZ)
- **VNET4**: `192.168.40.0/24` - Security operations (LAN)
- **VNET5**: `192.168.50.0/24` - Adversarial network (LAN)

### Core Components

| Component                       | Hostname    | vCPU | RAM (GB) | Disk (GB) | Purpose                                             |
| ------------------------------- | ----------- | ---- | -------- | --------- | -------------------------------------------------- |
| **pfSense Firewall + Suricata** | net-fw-01   |   2  |     2    |     20    | Network security gateway                           |
| **Windows 11 Workstation**      | lan-ws-01   |   2  |     4    |     80    | GPOs, security policies & network services         |
| **Windows AD/DC**               | srv-dc-01   |   2  |     3    |     60    | Domain services & target environment               |
| **Ansible controller**          | srv-auto-01 |   2  |     2    |     30    | Automation for infrastucture and security          |
| **OWASP Juice Shop**            | dmz-web-02  |   1  |     1    |     25    | Vulnerable web application                         |
| **Wazuh SIEM**                  | sec-siem-01 |   4  |     8    |     100   | Security monitoring, alerting & Response           |
| **Kali Linux + MITRE Caldera**  | adv-atk-01  |   4  |     4    |     80    | Penetration testing, sversary simulation & DFIR    |

## 📖 Documentation

- [pfSense Setup](docs/pfsense/pfsense-setup.md)
- [pfSense Configuration](docs/pfsense/pfsense-configuration.md)

## 🔗 Resources

- [MITRE ATT&CK Framework](https://attack.mitre.org/)
- [OWASP Testing Guide](https://owasp.org/www-project-web-security-testing-guide/)
- [Wazuh Documentation](https://documentation.wazuh.com/)
- [pfSense Documentation](https://docs.netgate.com/pfsense/en/latest/)

## ⚠️ Disclaimer

This lab is for educational and authorized testing purposes only. All malware samples, attack tools, and techniques should only be used in controlled environments and/or with explicit permission.

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
