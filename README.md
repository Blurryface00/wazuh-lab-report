# wazuh-lab-report
Hands on wazuh siem simulation
# 🛡️ Wazuh Home Lab Simulation Report

*Date:* July 20, 2025  
*Environment:* VMware Workstation | Ubuntu 24.04 | Parrot OS | Wazuh v4.12

---

## ✅ Lab Overview

| Component        | Status     |
|------------------|------------|
| Wazuh Manager    | ✔️ Installed (Ubuntu 24.04) |
| Parrot OS Agent | ✔️ Registered and Active |
| Bridged Network | ✔️ Configured (VMnet0) |

---

## 🛠️ Key Actions & Commands

### Wazuh Manager Install
```bash
curl -sO https://packages.wazuh.com/4.12/wazuh-install.sh
sudo bash wazuh-install.sh -a
