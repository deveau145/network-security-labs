# 🧪 Cisco ASA Enterprise Lab – Home Network Segmentation & Security Stack

Welcome to my expanding home cybersecurity lab! This project simulates a small-to-medium business environment using real Cisco equipment, virtual machines, Windows Server infrastructure, and cloud-connected services.

## 🎯 Lab Objectives

- Deploy segmented internal networks using **Cisco ASA 5506-X** and **VLANs**
- Build a functional **Windows Server domain** with DNS, DHCP, and Active Directory
- Integrate **on-prem AD with Microsoft 365** using Azure AD Connect
- Deploy and test **SIEM solutions** (e.g., Wazuh, Splunk, Elastic)
- Simulate real-world traffic, user accounts, and endpoint behavior
- Practice **incident response**, log correlation, and security automation

---

## 🏗️ Network Design (Planned)

        [AT&T Modem/Router]
                │
        [ASA 5506-X Firewall]
                │ trunk
          ┌─────┼─────┐
          │     │     │
       VLAN10 VLAN20 VLAN30
       SERVERS USERS PHONES
          │     │     │
    [Windows] [Client] [IoT]
      Server   PCs     Devices


- `192.168.10.0/24` – Servers & AD
- `192.168.20.0/24` – Workstations
- `192.168.30.0/24` – IoT & Phones

---

## 📁 Project Structure

| File/Folder         | Description                                    |
|---------------------|------------------------------------------------|
| `network/`          | ASA configs, switch configs, and diagrams      |
| `servers/`          | Windows Server setup and AD integration        |
| `vms/`              | VM provisioning and host configuration         |
| `logs/`             | Weekly progress logs and troubleshooting notes |

---

## 🔧 Technologies Used

- **Cisco ASA 5506-X**
- **Cisco 3750G Switch** (Layer 3 capable)
- **Windows Server 2022**
- **Ubuntu / Kali / CentOS VMs**
- **Azure AD Connect**
- **Wazuh, Splunk, or Elastic Stack** (for SIEM)

---

## 🚧 Status

- ✅ ASA VLAN and NAT configuration complete
- 🔄 Switch config and access port setup in progress
- 🔲 Windows Server provisioning
- 🔲 SIEM selection & deployment
- 🔲 O365 AD sync and testing

---

## 📌 Goals

- Create a functional hybrid lab environment
- Simulate blue team and red team scenarios
- Build portfolio evidence of hands-on security skills

---

## 🔗 Contact

**John Underwood**  
Cybersecurity Analyst | Linux & Networking Enthusiast  
[LinkedIn](https://www.linkedin.com/in/johncunderwood/) • [GitHub](https://github.com/deveau145)

