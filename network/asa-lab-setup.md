# 🛡️ Cisco ASA 5506-X Home Lab VLAN Segmentation

## 🛠️ Objective

Design a segmented lab network behind an AT&T Fiber modem using a Cisco ASA 5506-X as the core security gateway.

### Goals:
- Preserve existing home network: `192.168.1.0/24` (AT&T DHCP)
- Create 3 internal VLANs:
  - **SERVERS**: VLAN 10 → `192.168.10.0/24`
  - **USERS**: VLAN 20 → `192.168.20.0/24`
  - **PHONES**: VLAN 30 → `192.168.30.0/24`

## 🔌 Physical Topology

[AT&T Modem]
│
Gi1/1 (outside) → ASA 5506-X
│
Gi1/8 (802.1Q trunk) → Cisco Switch
├── VLAN 10 → Access Port → Server
├── VLAN 20 → Access Port → PC
└── VLAN 30 → Access Port → VoIP/IoT


## 🔧 ASA Interface Configuration

```bash
interface GigabitEthernet1/1
 nameif outside
 ip address dhcp setroute
 security-level 0
 no shutdown

interface GigabitEthernet1/8
 no nameif
 no ip address
 no security-level
 no shutdown

interface GigabitEthernet1/8.10
 vlan 10
 nameif SERVERS
 ip address 192.168.10.1 255.255.255.0
 security-level 100
 no shutdown

interface GigabitEthernet1/8.20
 vlan 20
 nameif USERS
 ip address 192.168.20.1 255.255.255.0
 security-level 100
 no shutdown

interface GigabitEthernet1/8.30
 vlan 30
 nameif PHONES
 ip address 192.168.30.1 255.255.255.0
 security-level 100
 no shutdown
