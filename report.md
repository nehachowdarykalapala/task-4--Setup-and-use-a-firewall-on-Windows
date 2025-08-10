# 🚀 Task 4 – Firewall Setup and Testing on Windows

## 📌 Objective
To configure and test basic firewall rules on Windows using **PowerShell** and **Windows Firewall** — blocking insecure traffic, verifying the block, removing the rule, and documenting the process.

---

## 🛠 Steps Performed

1. Opened **PowerShell as Administrator** to manage firewall settings.
2. Added a rule to **block inbound Telnet traffic** (TCP port 23) on all profiles.
3. Verified that the rule worked by testing connectivity to port 23.
4. Removed the Telnet block rule to restore default behavior.
5. Exported the current firewall configuration to a `.wfw` file for backup and documentation.
6. Recorded all commands for future reference.

---

## 💻 Commands Used

```powershell
# 1️⃣ Block inbound TCP port 23 (Telnet)
New-NetFirewallRule -DisplayName "Block-Telnet-Inbound" -Direction Inbound -Protocol TCP -LocalPort 23 -Action Block -Profile Any

# 2️⃣ Test the connection to port 23 to confirm block
Test-NetConnection -ComputerName localhost -Port 23

# 3️⃣ Remove the test block rule
Remove-NetFirewallRule -DisplayName "Block-Telnet-Inbound"

# 4️⃣ Export the firewall configuration
netsh advfirewall export "C:\Users\$env:USERNAME\firewall-config.wfw"
