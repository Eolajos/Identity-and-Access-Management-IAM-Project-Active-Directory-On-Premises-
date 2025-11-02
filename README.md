# Active Directory Simulation – EMATECH

This project is the deployment of a Windows Server Domain Controller (Active Directory) for a company called **EMATECH**. It includes domain setup, client configuration, OU design, group policies, and access control in an enterprise environment.

---

## Company Structure

**EMATECH** is a small IT services firm with the following structure:

- 1 x Windows Server (AD Domain Controller)
- 1 x Windows 8 Client PC (Sales Department)
- 1 x Windows 8  Client PC (IT Department)

---

## Project Objectives

- Configure an AD Domain Controller on Windows Server
- Join client PCs to the domain
- Create Organizational Units (OUs)
- Implement basic Group Policies for access control
- Simulate a centralized IT environment

---

## Network Design

```
Internet
   ↓
Router (Gateway: 10.0.5.1)
   ↓
Switch
 ┌──────┬─────────────┬──────────────┐
 │      │             │              │
Server  PC1 (Win 8)   PC2 (Win XP)
```

| Device        | IP Address      | Role                        |
|---------------|----------------|-----------------------------|
| Windows Server| 10.0.2.15  | AD Domain Controller (DC)   |
| Windows 8 PC  | DHCP    | Client (Accounts)           |
| Windows 8 PC | DHCP    | Legacy Client               |

---

## Domain Configuration

- **Domain Name**: `EMATECH.COM`
- **Server Name**: `EMATECH`
- **Static IP**: `10.0.2.15`
- **AD Roles Installed**: AD DS, DNS (DHCP)

---

## Organizational Units (OUs)

Created using **Active Directory Users and Computers**:

```
EMATECH.COM
├── OU: IT Department
│   └── Users: Brian.IT
    └── Users: Charles.IT

├── OU: Sales
│   └── Users: Aminat.Finance
```

---

## Group Policy (GPO)

Created and linked using **Group Policy Management Console (gpmc.msc)**:

- **GPO Name**: `DisableShutDown`
- **Linked to**: OU: Finance Department
- **Policy Configured**:
  - `Computer Configuration` > `Administrative Templates` > `System` > `Removable and Prevent Access to ShutDown,Restart, Sleep and Hibernate`
  - Set **"All Removable Shutdiwn Access: Deny all access"** to **Enabled**

Result: Pc cannot Shutdown for all users in the **Accounts OU**.

---

## Screenshots

- AD Domain Structure
- GPO Editor Screenshot
- PC joined to domain
- Result of denied USB access

---

## Key Takeaways

- Gained practical experience with Windows Server roles and domain setup
- Implemented centralized access control using Group Policy
- Learned how to structure users and departments with OUs
- Applied IAM concepts in a real-world simulated environment

---

## Author

**Emmanuel O. Olajoseph**  
Cybersecurity Analyst  
