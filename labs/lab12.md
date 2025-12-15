Lab 12 –  Lab 12 Printer Setup on Server 2022, NTFS Permissions

## Overview
This repository documents my home lab focused on Printer Setup on Server 2022 and NTFS Permissions using VirtualBox. The lab explores configuring printers on a Windows Server 2022 machine, setting up shared printers for network use, and managing NTFS file permissions to control access to shared resources.


## Objectives
Printer Setup on Server 2022: Learn how to install and configure printers on Windows Server 2022 and share them with network users.
NTFS Permissions: Understand how to set and manage NTFS file permissions for controlling access to shared resources on the server.
Printer Sharing: Configure printer sharing and permissions to ensure that only authorized users can access and print to the shared printers.

---

## Documentation
In this home lab, we will focus on how to install and configure network printers, as well as explore file and printer security through NTFS permissions.

Let's open up Server Manager on our Windows Server 2022 VM. Select Manage → Add Roles and Features.


![Rename Step 1](../images/lab11/step1-1.png)


Select Next until you reach Select Server Roles, then click on Print and Document Services. Select Add Features, then click Next.



![Rename Step 1](../images/lab11/step1-1.png)



For Role Services, it shows the different service installations, such as options for using Internet Printing Services or UNIX-based computers for LPD printing. In this case, we will focus on Print Server. Select Next, then click Install.



![Rename Step 1](../images/lab11/step1-1.png)




![Rename Step 1](../images/lab11/step1-1.png)



Once the installation is complete, we can verify that the printing services are installed by reopening Server Manager. We should notice that Print Services appears on the left side.




![Rename Step 1](../images/lab11/step1-1.png)



Lets open up “Tools” → “Print Management”



![Rename Step 1](../images/lab11/step1-1.png)



In Print Management, we can see the different drivers, printers, ports, and the server "Server2022 (local)" for our Desktop2 computer.


![Rename Step 1](../images/lab11/step1-1.png)





Now lets create a printer, right-click then “Add Printer..”.



![Rename Step 1](../images/lab11/step1-1.png)



Select “Add a new printer using an existing port:”



![Rename Step 1](../images/lab11/step1-1.png)



Then select “Install a new driver”.



![Rename Step 1](../images/lab11/step1-1.png)



Here, we will select any driver. I will select "Microsoft MS-XPS Class Driver 2", then click Next.


![Rename Step 1](../images/lab11/step1-1.png)



Make sure to uncheck "Share this printer," then click Next and finally select Finish.


![Rename Step 1](../images/lab11/step1-1.png)



![Rename Step 1](../images/lab11/step1-1.png)




Now, when we look into the properties of our new printer, we can see the different settings we can configure. For example, if we wanted to list the printer in Active Directory for another user to install, we could do that in the Sharing tab. We will enable this in just a bit.


![Rename Step 1](../images/lab11/step1-1.png)



We can also see the different ports available for the printer in the Ports tab.


![Rename Step 1](../images/lab11/step1-1.png)


Lets look into the “Security” tab in the properties of our printer. Here we want to remove the users “EVERYONE” and limit certain users to have access to our printer. Click on “Advance”


![Rename Step 1](../images/lab11/step1-1.png)



Select "Everyone", then click Remove.


![Rename Step 1](../images/lab11/step1-1.png)


Now, let's add HR to the permissions by clicking on Add, then Select a principal → type in "HR", and select OK. For basic permissions, we will only allow HR to Print, then click OK → Apply, and finally OK.


![Rename Step 1](../images/lab11/step1-1.png)


Now, we can see in the Security tab that HR is a member of this security group, and it shows the permissions HR has for this printer. This printer should also automatically show up for anyone in the HR group.


![Rename Step 1](../images/lab11/step1-1.png)




Now, let's list this printer in the directory. Click on the Sharing tab, then enable "Share this printer" and "List in the directory", and click Apply.



![Rename Step 1](../images/lab11/step1-1.png)




Let's verify that by going to Active Directory Users and Computers, right-clicking on the domain SimoTech.com, selecting "Find", then selecting the dropdown under "Find:" and choosing "Printers".


![Rename Step 1](../images/lab11/step1-1.png)


![Rename Step 1](../images/lab11/step1-1.png)




Click on "Find Now", and our printer should show up in the directory.


![Rename Step 1](../images/lab11/step1-1.png)


Now that the printer is in the directory, let's log into Desktop2 as Bob and install the printer from the directory. Open up Control Panel on Desktop2 → View Devices and Printers → Add Printer. The scan will search for the printer in the directory. Select Next, then Finish.



![Rename Step 1](../images/lab11/step1-1.png)


Congratulations! We have successfully added a printer on our Server 2022 domain and explored file and printer security through NTFS permissions for effective access control.



---
👉 Next Lab 13 : Understanding Tickets Using Spiceworks
