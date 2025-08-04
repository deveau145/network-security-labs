# 📃 Weekly Log - Week 3 (Aug 4 - Aug 10)

## 🏋️ Summary

This week focused on completing the switch configuration for LAB-SW1 and formally documenting VLAN assignments, SSH access, and trunk uplinks in GitHub.

---

## 🔧 Key Work Completed

### 🔹 LAB-SW1 VLAN & Port Configuration

* Configured VLANs 10 (SERVERS), 20 (USERS), 30 (MGMT), 40 (IOT), 50 (CAMERAS)
* Labeled ports by role:

  * VLAN 10: UCS & DL360e Servers
  * VLAN 20: Workstations (Linux/Windows)
  * VLAN 30: CIMC, iLO, SSH management ports
  * VLAN 40: Smart plugs, printers
  * VLAN 50: IP cameras, NVR
* Trunked Gi1/0/1 to ASA Gi1/8 (allowed VLANs: 10-50)

### 🔐 SSH Setup

* SSH access restricted to VLAN 30 (MGMT)
* IP: `192.168.30.2`
* SSH v2 with 2048-bit RSA key
* Username: `admin` (password redacted)

### 🔹 GitHub Updates

* Updated `network/switch-config.md` with:

  * Port layout
  * VLAN summaries
  * Configuration commands used
* Confirmed all config was entered manually and verified live

---

## 🔹 Notes

* HOME-SW2 role swap was documented but not committed to GitHub (not lab-related)
* SSH verified from VLAN 30
* Diagram update pending: topology diagram still reflects earlier state

---

## ✅ Next Steps (Week 4 Goals)

* Add ASA subinterface setup to `asa-lab-setup.md`
* Create NAT rules for VLANs
* Begin documenting ACLs
* Start basic GRC planning repo (SimplyCyber, AuditScripts)
* Update `topology-diagram.png` with latest switch + ASA config

---

## 📂 GitHub Tasks

* [ ] Add this log to `logs/progress-week-03.md`
* [ ] Push changes to `asa-lab-setup.md`
* [ ] Update topology diagram if ASA config is completed
