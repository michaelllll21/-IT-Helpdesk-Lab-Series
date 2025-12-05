# Lab 6 – Lab 6 Common Active Directory Issues, CMD Commands, PC Offline

## Overview
This section of my home lab documentation explores common Active Directory issues, troubleshooting with CMD commands, and resolving situations where a PC is offline in a domain environment. 
The project provides practical solutions for addressing common problems that administrators face when working with Active Directory, such as authentication failures, group policy application issues, and troubleshooting offline PCs.


## Objectives
Join a Windows 10 PC to a domain with a local user account.
Configure and apply Group Policy Objects (GPOs) to enforce settings on domain-joined computers.
Generate RSOP (Resultant Set of Policy) reports to review and troubleshoot applied policies.
Use Group Policy Management Console (GPMC) to manage and configure GPOs.
---

## Documentation
In this home lab, we will explore common Active Directory issues users might encounter, then use CMD commands to resolve PC offline problems.

---
Let's begin with some CMD commands. On the local user account Bob, open Command Prompt and type ping 12.1.10.2. 
This is the IP address of our Windows Server 2022 machine. This command will confirm that Desktop2 can communicate with the server. 
Now, let's repeat the process on the Server by pinging Desktop2 to verify the connection from the server side.

![Rename Step 1](../images/lab6/step1-1.png)

Now on our Windows Server 2022, when we ping 12.1.10.4 (local user Bob), we can see that the connection timed out. This is because the firewall on that account is preventing the ping, so we would need to disable it. To do that, open up Windows Defender Firewall → Turn off Windows Defender Firewall on or off.

![Rename Step 1](../images/lab6/step1-2.png)


Use the Helpdesk administrative login to access Windows Defender Firewall, then turn off all of the options. Afterward, select OK to apply the changes.

![Rename Step 1](../images/lab6/step1-3.png)

Now lets run the command line again on our Windows Server 2022.
Make sure you trun off in Desktop2


![Rename Step 1](../images/lab6/step1-4.png)

If we add the -t option to our ping command, such as ping 12.1.10.4 -t, it will continue running indefinitely until manually stopped. This allows us to monitor network connectivity and observe any changes in packet loss over time. The ping will automatically stop if the Desktop2 PC is shut down or restarted.



![Rename Step 1](../images/lab6/step1-5.png)


Next, on the local user Bob, run Command Prompt as an administrator using the Helpdesk administrative login. Then, type gpresult /r > c:\results.txt. This command will generate a group policy report for the PC and save it as a text file in the C: drive.
If we do not run it in administrative then the command line will deny us access.


![Rename Step 1](../images/lab6/step1-6.png)



Some additional command lines such as gpupdate /help will provide a list of available options for the gpupdate command.


![Rename Step 1](../images/lab6/step1-7.png)


Gpresult /? will display a list of available options for the command.


![Rename Step 1](../images/lab6/step1-8.png)

Gpresult /r displays the result of the Group Policy for the current user and computer.


![Rename Step 1](../images/lab6/step1-9.png)

Next, let's explore some common issues that Helpdesk teams may encounter when assisting users, such as when a user account becomes locked out. To test this, we will sign out of Bob and purposely lock his account by putting the incorrect password.

![Rename Step 1](../images/lab6/step1-10.png)

In this scenario when a user is locked out and is calling the helpdesk or admins for help, typically they would access the Active Directory Users and Computers → search for the user then unlock it from there. Lets try this out on our Helpdesk account. Open up Active Directory Users and Computers → right-click on the domain SimoTech.com and search up Bob, make sure that the entire directory is selected. Once Bob is found, double click on his name and select “Account” then select “Unlock Account”. then press “Apply” then “OK”. Now Bob can log into his account successfully.


![Rename Step 1](../images/lab6/step1-11.png)

Bob should be able to log in now once his account is unlocked.

![Rename Step 1](../images/lab6/step1-12.png)


Now let’s create an issue where Bob’s account is disabled for some reason and that he forgot his password. Let’s intentionally disable Bob’s account by clicking on his account again in Active Directory Users and Computers on the Helpdesk machine.


![Rename Step 1](../images/lab6/step1-13.png)

Now let’s imagine a scenario where Bob’s account is disabled for some reason, and he does not remember his password. As a helpdesk, we can look up Bob’s user in Active Directory Users and Computers using the Find command on the domain → select Entire Directory and search for Bob → right-click on his name and select Enable Account.

![Rename Step 1](../images/lab6/step1-14.png)


![Rename Step 1](../images/lab6/step1-15.png)


Since Bob has forgotten his password, we can provide him with a temporary password that will allow him to log in and change it to his own password upon his next login. To do this, right-click on Bob and select Reset Password. Ensure that the User must change password at next logon option is enabled.



![Rename Step 1](../images/lab6/step1-16.png)


![Rename Step 1](../images/lab6/step1-17.png)


Now, let’s create a scenario where Bob’s account is expired due to inactivity or because an administrator has set an expiration date for the account. To do this:

Select Bob in Active Directory Users and Computers.

Click on the Account tab.

Under Account expires, select End of and choose a date that has already passed.

![Rename Step 1](../images/lab6/step1-18.png)


![Rename Step 1](../images/lab6/step1-19.png)


To resolve this, the Helpdesk account would need to go to Active Directory Users and Computers → search for Bob using the Find function in the domain → select Entire Directory → open Bob’s account → go to the Account tab, then select Never under Account expires.


![Rename Step 1](../images/lab6/step1-20.png)


To make sure Bob’s account is valid, open Command Prompt on the Helpdesk account and type net user Bob /domain. This will verify that the account is active and should allow Bob to log in.

![Rename Step 1](../images/lab6/step1-21.png)


Let’s create an issue where the computer has fallen off the domain. On the Helpdesk account in Active Directory Users and Computers → select Computers → right-click on the computer and select Disable Account.


![Rename Step 1](../images/lab6/step1-22.png)

Lets use our Helpdesk account to login into desktop2. It should give us an error.



![Rename Step 1](../images/lab6/step1-23.png)


When a computer is fallen off from a domain, we can sometimes fix it by going to Active Directory Users and Computers and selecting that computer (Desktop2) and enabling it. We can log in back into our accounts now.

![Rename Step 1](../images/lab6/step1-24.png)


Now let’s try a different way of making the computer fall off the domain. We will delete Desktop2 from the domain. In Active Directory Users and Computers on the Helpdesk account, select Computers, then right-click and delete Desktop2.

Next, let’s create a new user: go to Users, right-click, and select New → User. Use First/Last Name and set the User logon as Test, then click Finish.

Now, attempt to log in to Desktop2 using the Test account. An error should appear indicating that the computer is no longer part of the domain.


![Rename Step 1](../images/lab6/step1-25.png)

![Rename Step 1](../images/lab6/step1-26.png)

To add Desktop2 back into our Computers domain, we need to log into our domain as administrator to do that type “.\administrator” and enter your password.


![Rename Step 1](../images/lab6/step1-27.png)



Next, go into File Explorer → right-click on This PC → select Properties → click on Rename this PC (Advanced) → select Change → under Member of, change it to Workgroup. Then, restart the computer.


![Rename Step 1](../images/lab6/step1-28.png)



Log in as Administrator and repeat the process to add the computer back to the domain. Go to File Explorer → right-click on This PC → select Properties → click on Rename this PC (Advanced) → select Change, then add it back to the domain as SimoTech.com. Proceed with a restart.

Now, go back to the Helpdesk account in Active Directory Users and Computers, and under Computers, you should see Desktop2 is back in the domain.


![Rename Step 1](../images/lab6/step1-29.png)


![Rename Step 1](../images/lab6/step1-30.png)



---

Congratulations! We have successfully addressed several common Active Directory issues, utilized CMD commands effectively, and resolved PC offline scenarios.

👉 Next Lab 7 : Security Groups, Mapped Drives, Personal Drives






