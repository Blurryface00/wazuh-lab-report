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

🧪 FIM Test: Simulated Malware File (EICAR)
** 📅 Timestamp:* July 20, 2025 @ 13:45  
** 📸 Screenshot:* IMG_1817FFB8.jpg

Created a standard antivirus test file to simulate malware detection:

```bash
mkdir -p ~/wazuh-test && cd ~/wazuh-test
echo 'X5O!P%@AP[4\\PZX54(P^)7CC)7}$EICAR-STANDARD-ANTIVIRUS-TEST-FILE!$H+H*' > eicar.txt

**🧠 This triggered Wazuh’s syscheck module for file integrity monitoring (FIM).

⚙️ Configured Custom Directory Monitoring
**📅 Timestamp: July 20, 2025 @ 13:55
**📸 Screenshot: IMG_F6FCC0FC.jpg

Updated ossec.conf to monitor the EICAR test directory:

<directories check_all="yes" realtime="yes">/home/user/wazuh-test</directories>

Restarted agent:

sudo systemctl restart wazuh-agent

🚨 FIM Alert Triggered
**📅 Timestamp: July 20, 2025 @ 14:54
**📸 Screenshot: IMG_C0968405.jpg

After modifying the test file:

echo "trigger alert" >> ~/wazuh-test/eicar.txt

Wazuh triggered:
    •    Rule Group: syscheck_file
    •    Rule: Integrity checksum changed
    •    Agent: parrot

⸻

🧪 Nmap Scan Detection (Recon Simulation)

📅 Timestamp: July 20, 2025 @ 15:05
Run from Parrot OS:

nmap -T4 -A 192.168.1.149

Expected Wazuh alert:
    •    Nmap Scan Detected
    •    Rule ID: 5712 or 5700
