# IT Helpdesk Lab Series

## Project Overview
This repository documents a virtualized IT Helpdesk home lab built using VirtualBox, Windows Server 2022, Windows 10, Active Directory, Group Policy, remote administration tools, ticketing workflows, and troubleshooting scenarios.

The lab simulates a small enterprise IT environment where helpdesk and junior system administration tasks are practiced and documented step by step.

## Purpose
The purpose of this project is to demonstrate hands-on IT support, Active Directory administration, Windows troubleshooting, user management, Group Policy, remote support, software deployment, and helpdesk ticketing skills.

This project serves as part of my IT support and networking portfolio.

## Lab Environment

| Component | Details |
|---|---|
| Virtualization Platform | Oracle VirtualBox |
| Server OS | Windows Server 2022 |
| Client OS | Windows 10 |
| Domain | SimoTech.com |
| Domain Controller | Server2022 |
| Client Machines | Desktop1, Desktop2 |
| Main Tools | Active Directory, DNS, DHCP, Group Policy, RSAT, PDQ Deploy, PDQ Inventory, Spiceworks |

## Skills Demonstrated
- Windows Server 2022 installation and setup
- Active Directory Domain Services configuration
- Domain controller setup
- Windows 10 domain joining
- User and group management
- Organizational Unit management
- Group Policy configuration
- RSOP and gpresult troubleshooting
- Password reset and account unlock
- Security group and permission management
- Mapped drives and personal drives
- Remote Desktop and Remote Registry
- C$ administrative share usage
- Software deployment with PDQ Deploy
- Hardware and software inventory with PDQ Inventory
- Printer setup and permission control
- Helpdesk ticketing workflow using Spiceworks
- Delegation of control
- Account lockout investigation and resolution

## Lab List

| Lab | Title | Main Skills |
|---|---|---|
| [Lab 1](labs/lab1.md) | Installing Windows Server 2022 and Preparing AD Lab | VirtualBox setup, Windows Server installation |
| [Lab 2](labs/lab2.md) | Renaming Windows Server 2022 and Installing Active Directory | AD DS installation, domain controller setup |
| [Lab 3](labs/lab3.md) | Creating Help Desk Accounts in Active Directory and Using CMD Commands | Helpdesk account creation, AD Recycle Bin, CMD verification |
| [Lab 4](labs/lab4.md) | Installing Windows 10, Joining PC to Domain, Installing RSAT, and Using Server Manager | Windows 10 setup, domain join, RSAT tools |
| [Lab 5](labs/lab5.md) | Join Windows 10 to Domain, Group Policy, and RSOP Reports | OUs, users, GPO, RSOP reports |
| [Lab 6](labs/lab6.md) | Common Active Directory Issues, CMD Commands, and PC Offline Troubleshooting | Account lockout, disabled accounts, domain trust issues |
| [Lab 7](labs/lab7.md) | Security Groups, Mapped Drives, and Personal Drives | Shared folders, security groups, mapped drives |
| [Lab 8](labs/lab8.md) | Windows 10 Remote Access: Remote Desktop and Remote Registry | RDP, Remote Registry, C$ admin share, Remote Assistance |
| [Lab 9](labs/lab9.md) | RSOP, Group Policy, Task Manager, and Disable Logoff | GPO restrictions, gpupdate, gpresult, Task Manager policy |
| [Lab 10](labs/lab10.md) | Installing and Deploying Software with PDQ | PDQ Deploy, software deployment |
| [Lab 11](labs/lab11.md) | PDQ Inventory: Hardware and Software Reporting | Inventory scan, hardware/software reports, remote admin tools |
| [Lab 12](labs/lab12.md) | Printer Setup on Server 2022 and NTFS Permissions | Print services, printer sharing, permissions |
| [Lab 13](labs/lab13.md) | Understanding Tickets Using Spiceworks | Ticket creation, assignment, priority, resolution workflow |
| [Lab 14](labs/lab14.md) | Delegate Control and Account Lockout Management | Delegated permissions, password reset rights, lockout investigation |

## Lab Screenshots
Screenshots for each lab are stored in the `images` folder.

Example structure:

```text
images/
├── lab1/
├── lab2/
├── lab3/
...
└── lab14/
