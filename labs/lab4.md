# Lab 4 — Installing Windows 10, Joining a PC to the Domain, Installing RSAT, and Using Server Manager

## Overview
In this lab, we will install **Windows 10**, join it to our **SimoTech.com** domain using the **Helpdesk account**, install **RSAT (Remote Server Administration Tools)**, and verify domain management using **Server Manager**.  
This simulates real-world helpdesk responsibilities and domain onboarding tasks.

---

## Objectives
- Install and set up Windows 10 in VirtualBox
 Windows 10 Installation Media Tool.

- Join a Windows 10 PC to the SimoTech.com domain  
- Log in using the Helpdesk domain account  
- Install RSAT to manage Active Directory from a client machine  
- Use Server Manager to confirm domain controller communication  

---

## Step 1 — Install Windows 10
1. Create a new virtual machine in VirtualBox named **Windows10**.  
2. Attach your **Windows 10 ISO**.  
3. Install Windows normally until you reach the desktop.  
4. Set a local administrator password and complete setup.

---

## Step 2 — Set the PC Name
1. Open **File Explorer → This PC → Properties**.  
2. Click **Rename this PC (Advanced)**.  
3. Rename it to something clean such as:  
   **WIN10-CLIENT**  
4. Restart the virtual machine.

---

## Step 3 — Check Network Connectivity
Open **Command Prompt** and test the connection to the domain controller:

