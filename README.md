# task-4--Setup-and-use-a-firewall-on-Windows
# 🔐 Firewall Setup and Testing on Windows

## 📌 Overview
This repository contains my work for **Task 4 – Firewall Setup and Testing on Windows** as part of the Cyber Security Internship.  
The goal was to **configure, test, and document** Windows Firewall rules using **PowerShell** (and optional CMD testing).

---

## 🛠 What I Did
- Enabled Windows Firewall on all profiles.
- Added an inbound rule to **block Telnet** (TCP port 23).
- Verified the block using `Test-NetConnection` and `telnet`.
- Removed the rule to restore default settings.
- Exported the firewall configuration for documentation.

---

## 📷 Proof of Work
This repository includes:
- **Screenshots** of firewall rule creation and testing.
- **Commands used** (PowerShell & CMD).
- **Exported firewall configuration** file.
- **Detailed `report.md`** documenting the entire process.

---

## 💻 Commands Used

**PowerShell**
```powershell
# Block inbound TCP port 23 (Telnet)
New-NetFirewallRule -DisplayName "Block-Telnet-Inbound" -Direction Inbound -Protocol TCP -LocalPort 23 -Action Block -Profile Any

# Test the connection to port 23
Test-NetConnection -ComputerName localhost -Port 23

# Remove the rule
Remove-NetFirewallRule -DisplayName "Block-Telnet-Inbound"

# Export firewall configuration
netsh advfirewall export "C:\Users\$env:USERNAME\firewall-config.wfw"
