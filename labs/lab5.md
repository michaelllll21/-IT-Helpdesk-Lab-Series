# Lab 5 – Lab 5 Join Windows 10 to Domain (Local User), Group Policy, RSOP Reports

## Overview
In this lab, I created Organizational Units (OUs), users, and groups inside Active Directory on the SimoTech.com domain.  
This simulates real-world IT administration where AD structures help organize users, assign permissions, and prepare for Group Policies.

## Objectives
Join a Windows 10 PC to a domain with a local user account.
Configure and apply Group Policy Objects (GPOs) to enforce settings on domain-joined computers.
Generate RSOP (Resultant Set of Policy) reports to review and troubleshoot applied policies.
Use Group Policy Management Console (GPMC) to manage and configure GPOs.
---

##Documentation
In this home lab, we will create another virtual machine running Windows 10, named Desktop2, to simulate a local user account for testing purposes. This virtual machine will represent an employee in our lab environment. For example, if this user encounters password issues, we can reset it using the Help Desk account on our primary Windows 10 virtual machine.

---

To create the new virtual machine, click on Machine → New, then name it Desktop2. Select the Windows ISO image from your downloads, choose Skip unattended installation, and then click Finish.




---

## 3. Create Department OUs under SimoTech Users
Inside **SimoTech Users**, created:

- `IT`
- `HR`
- `Finance`
- `Sales`

**Steps:**
1. Right-click **SimoTech Users**
2. Select **New → Organizational Unit**
3. Enter the department name

---

## 4. Create Security Groups
Inside **SimoTech Groups**, created:

- `IT_Group`
- `HR_Group`
- `Finance_Group`
- `Sales_Group`

Each group:
- Group scope: **Global**
- Group type: **Security**

---

## 5. Create Users for Each Department
Created users:

| Department | Username  | Full Name        |
|-----------|-----------|------------------|
| IT        | ituser1   | IT User 1        |
| HR        | hruser1   | HR User 1        |
| Finance   | finuser1  | Finance User 1   |
| Sales     | sales1    | Sales User 1     |

**Steps:**
1. Right-click the department OU (ex: IT)
2. Click **New → User**
3. Enter first name, last name, username
4. Set password
5. Finish user creation

---

## 6. Add Users to Their Groups
Example: adding `ituser1` to `IT_Group`

**Steps:**
1. Open **SimoTech Groups**
2. Double-click **IT_Group**
3. Go to **Members** tab
4. Click **Add**
5. Enter: `ituser1`

Repeat for all departments.

---

## 7. Verify User Account Using CMD
Open Command Prompt and run:

