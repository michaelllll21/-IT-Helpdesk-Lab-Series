# Lab 3 — Creating Help Desk Accounts in Active Directory & Using CMD Commands

## Overview
In this lab, I demonstrate how to create a dedicated **Help Desk account** inside **Active Directory** and verify it using essential **CMD (Command Prompt)** commands.  
This simulates real-world IT Helpdesk responsibilities such as provisioning accounts, assigning permissions, and checking configurations.

---

## Objectives
- Create a Help Desk account in Active Directory  
- Enable the AD Recycle Bin  
- Assign appropriate permissions  
- Use CMD commands to verify account and network settings  

---

## Step 1 — Enable the Active Directory Recycle Bin
1. Open **Active Directory Administrative Center**.  
2. Click **SimoTech.com (local)**.  
3. Select **Enable Recycle Bin** → click **OK**.  
4. You should now see **Deleted Objects** under the domain.

---

## Step 2 — Open Server Manager & ADUC
1. Open **Server Manager**.  
2. On the top right, go to **Tools → Active Directory Users and Computers (ADUC)**.  
3. Pin both tools to the taskbar for convenience.

---

## Step 3 — Enable Advanced Features
In ADUC:  
- Click **View** → select **Advanced Features**.

---

## Step 4 — Create the Help Desk Account
1. In ADUC, expand your domain → click **Users**.  
2. Right-click **Administrator** → select **Copy**.  
   - This duplicates administrative permissions.  
3. Fill in the details:  
   - **First Name:** Helpdesk  
   - **Last Name:** Helpdesk  
   - **User logon name:** Helpdesk  
4. Create a password → click **Finish**.

You should now see your **Helpdesk** account with the same group memberships as Administrator.

---

## Step 5 — Open CMD (Command Prompt)
Search **Command Prompt** from the Start menu.

---

## Step 6 — Use Important CMD Commands

### 🔹 View basic IP info
