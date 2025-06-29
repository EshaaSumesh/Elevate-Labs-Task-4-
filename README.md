# Task 4: Setup and Use a Firewall on Windows

## Objective
Configure and test basic firewall rules to allow or block traffic using **Windows Defender Firewall with Advanced Security**.

---

## Tools Used
- Windows Defender Firewall (Advanced Settings)
- Command Prompt
- Telnet Client (enabled via DISM)

---

##  Steps Performed

### 1. Opened Firewall Configuration Tool
- Opened Run dialog (`Windows + R`)
- Entered `wf.msc` to launch **Windows Defender Firewall with Advanced Security**
- Navigated to the **Inbound Rules** section

### 2. Listed Current Rules
- Explored both **Inbound** and **Outbound Rules**
- Verified existing firewall rule set before making changes

### 3. Created Inbound Rule to Block Port 23 (Telnet)
- In **Inbound Rules**, selected **New Rule**
- Chose:
  - **Rule Type**: Port
  - **Protocol**: TCP
  - **Specific Local Port**: 23
  - **Action**: Block the connection
  - **Profile**: Domain, Private, Public (all selected)
  - **Name**: `Block Telnet Port 23`
- Confirmed the new rule was added and active

### 4. Enabled Telnet Client
Telnet Client was not installed by default, so the following command was used in **elevated Command Prompt**:

```cmd
dism /online /Enable-Feature /FeatureName:TelnetClient
The operation completed successfully.
```

### 5. Tested the Firewall Rule
After enabling the Telnet Client, opened Command Prompt

Ran the command:
```cmd
telnet 127.0.0.1
Connecting To 127.0.0.1...Could not open connection to the host on port 23: Connect failed
```

This confirms that the firewall successfully blocked inbound traffic on port 23, simulating the protection against Telnet-based connections.

### 6. Removed the Test Rule
Returned to Inbound Rules

Located Block Telnet Port 23

Right-clicked and selected Delete

This restored the firewall to its original configuration
