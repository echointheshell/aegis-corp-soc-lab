# 🛡️ Aegis Corporation Lab

The Aegis Corporation Lab is a virtualised environment designed to simulate a simple network infrastructure with integrated security monitoring, threat simulation, and analysis capabilities. The aim is to provide an isolated and controlled environment for hands-on exposure to the tools and techniques associated with security operations and adversary tradecraft.

## 🏗️ Architecture

![Lab Network Diagram](assets/lab-diagram-v1.1.png)

### Network Segments
- **WAN Network (VNET5)**: `172.16.50.0/24` - External-facing network (WAN)
- **LAN Network (VNET1)**: `192.168.10.0/24` - Internal network (LAN)

### Core Components

| Component              | Purpose                                        |
| ---------------------- | ---------------------------------------------- |
| **pfSense Firewall**   | Network security gateway                       |
| **Wazuh SIEM**         | Security monitoring & alerting                 |
| **Zeek**               | Intrusion detection                            |
| **Kali Linux**         | Penetration testing & attack simulation        |
| **REMnux**             | Malware analysis                               |
| **MITRE Caldera**      | Adversary emulation platform                   |
| **Windows AD/DC**      | Domain services & target environment           |
| Windows 11 Workstation | GPO and Security policies & target environment |
| Linux Server 22.04     | Syslog and web server & target environment     |
| **OWASP Juice Shop**   | Vulnerable web application                     |

## 📖 Documentation

- [pfSense Setup](docs/pfsense/pfsense-configuration.md)
- [pfSense Configuration](docs/pfsense/pfsense-setup-guide.md)

## 🔗 Resources

- [MITRE ATT&CK Framework](https://attack.mitre.org/)
- [OWASP Testing Guide](https://owasp.org/www-project-web-security-testing-guide/)
- [Wazuh Documentation](https://documentation.wazuh.com/)
- [pfSense Documentation](https://docs.netgate.com/pfsense/en/latest/)

## ⚠️ Disclaimer

This lab is for educational and authorized testing purposes only. All malware samples, attack tools, and techniques should only be used in controlled environments and/or with explicit permission.

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
