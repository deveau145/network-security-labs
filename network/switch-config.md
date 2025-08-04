# 🔧 LAB-SW1 Configuration Summary

## 📋 Overview

`LAB-SW1` is the primary Layer 2 switch for the segmented lab environment, connected to the Cisco ASA 5506-X. It supports five VLANs:

| VLAN ID | Name     | Subnet            | Purpose                         |
|---------|----------|-------------------|----------------------------------|
| 10      | SERVERS  | 192.168.10.0/24   | UCS, DL360e, NAS, VMs            |
| 20      | USERS    | 192.168.20.0/24   | Workstations (Linux, Windows)    |
| 30      | MGMT     | 192.168.30.0/24   | iLO, CIMC, switch/AP management  |
| 40      | IOT      | 192.168.40.0/24   | Smart plugs, printers, sensors   |
| 50      | CAMERAS  | 192.168.50.0/24   | IP cameras, NVRs                 |

- **Trunk to ASA:** Interface `Gi1/0/1`

---

## 🔐 IP and SSH Access

- **Management VLAN:** 30  
- **Switch IP:** `192.168.30.2`  
- **SSH Enabled:** Version 2 with RSA 2048-bit key  
- **Username:** `admin`  
- **Password:** `[REDACTED]`  
- SSH is only accessible from VLAN 30.

---

## 🗂️ Port Layout and VLAN Assignments

### VLAN 10 - SERVERS
```bash
interface range Gi1/0/2 - 3
 description *** UCS C220 Server ***
 switchport access vlan 10
 switchport mode access
 spanning-tree portfast
 no shutdown

interface range Gi1/0/4 - 7
 description *** DL360e Server ***
 switchport access vlan 10
 switchport mode access
 spanning-tree portfast
 no shutdown

interface Gi1/0/8
 description *** UCS MGMT (CIMC) ***
 switchport access vlan 30
 switchport mode access
 spanning-tree portfast
 no shutdown

interface Gi1/0/9
 description *** DL360e iLO ***
 switchport access vlan 30
 switchport mode access
 spanning-tree portfast
 no shutdown

interface range Gi1/0/10 - 12
 description *** MGMT Access / Laptops ***
 switchport access vlan 30
 switchport mode access
 spanning-tree portfast
 no shutdown

interface range Gi1/0/15 - 17
 description *** IOT Devices ***
 switchport access vlan 40
 switchport mode access
 spanning-tree portfast
 no shutdown

interface range Gi1/0/13 - 14
 description *** IP Cameras / NVR ***
 switchport access vlan 50
 switchport mode access
 spanning-tree portfast
 no shutdown

interface range Gi1/0/18 - 19
 description *** Lab Workstation (Linux/Win) ***
 switchport access vlan 20
 switchport mode access
 spanning-tree portfast
 no shutdown

interface range Gi1/0/20 - 24
 description *** SPARE / Mirror ***
 switchport access vlan 1
 switchport mode access
 shutdown

interface Gi1/0/1
 description *** Trunk to ASA ***
 switchport trunk allowed vlan 10,20,30,40,50
 switchport mode trunk
 spanning-tree portfast trunk
 no shutdown

ip domain-name lab.local
crypto key generate rsa
 2048
ip ssh version 2
username admin secret <REDACTED>
line vty 0 4
 login local
 transport input ssh

show vlan brief
show interfaces status
show ip interface brief
show ip ssh
show version | include image
show run | section line vty
show run | include username

