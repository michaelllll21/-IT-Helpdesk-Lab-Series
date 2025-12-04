# Lab 5 – Creating Organizational Units (OUs), Users, and Groups in Active Directory

## Overview
In this lab, I created Organizational Units (OUs), users, and groups inside Active Directory on the SimoTech.com domain.  
This simulates real-world IT administration where AD structures help organize users, assign permissions, and prepare for Group Policies.

## Objectives
- Create Organizational Units (OUs)
- Create department groups (Security Groups)
- Create user accounts per department
- Add users to their appropriate groups
- Verify accounts using CMD

---

## 1. Open Active Directory Users and Computers
- Log in to **Server2022**.
- Open **Server Manager → Tools → Active Directory Users and Computers**.
- Enable **View → Advanced Features**.

---

## 2. Create Organizational Units
Created the following OUs:

- `SimoTech Users`
- `SimoTech Computers`
- `SimoTech Groups`

**Steps:**
1. Right-click **SimoTech.com**
2. Click **New → Organizational Unit**
3. Type the OU name
4. Repeat for all three OUs

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

