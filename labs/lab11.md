# Lab 11 – Lab 11 PDQ Inventory: Hardware and Software Reporting

## Overview
This repository documents my home lab focused on PDQ Inventory: Hardware and Software Reporting using VirtualBox. The lab aims to explore PDQ Inventory's capabilities for gathering detailed reports on hardware and software configurations across a network of virtual machines. The project will include setting up PDQ Inventory, creating custom reports, and automating hardware/software data collection for system management and network monitoring.

## Objectives
Learn PDQ Inventory: Explore how to set up PDQ Inventory and configure it for comprehensive hardware and software reporting.
Create Custom Reports: Learn how to build and customize reports to track hardware specifications, software installations, and system configurations.


---

## Documentation
In this home lab, I will showcase the installation and uses of PDQ Inventory. To start, open File Explorer and navigate to the SimoTech folder. Inside, you should find the PDQ Inventory application.


![Rename Step 1](../images/lab11/step1-1.png)



We can double click on the application to start the installation then continue it to install to finish. Launch the application once finish.


![Rename Step 1](../images/lab11/step1-2.png)


Lets add Desktop2 to PDQ Inventory, to do that select “Computers” on top → “Add computers” then “Active Directory - Browse by Name” then select “Desktop2.SimoTech.com” as the target to add then select “OK”.


![Rename Step 1](../images/lab11/step1-3.png)



PDQ Inventory is a powerful IT asset management tool that helps track and manage hardware and software across a network. It provides real-time insights, automates reporting, and integrates seamlessly with tools like PDQ Deploy for efficient software updates and policy compliance.

Here are some of the features we can use in PDQ Inventory: Right-click on Desktop2, then select Run Report → Share Folders to generate a report on the shared folders available on that machine.



![Rename Step 1](../images/lab11/step1-4.png)


This show us all the folders that are mapped on it. Lets double click on “ADMIN$”



![Rename Step 1](../images/lab11/step1-5.png)



It will give us all the details and specifications that are on that computer, such as who is logged in currently, what the domain controller is, the host name, what operating system it is, and what version of Windows it is using.


![Rename Step 1](../images/lab11/step1-6.png)






On the left-hand side, we can see all the items we can explore on Desktop2. Let's take a look at the Applications by clicking on it. This is a great way to check what applications are installed on the computer. If something is missing, we can use this feature to identify the missing software and download it accordingly.



![Rename Step 1](../images/lab11/step1-7.png)


To verify if we have these applications downloaded, let's go to our Desktop2 VM and open Control Panel → Uninstall a Program. This will display the list of applications installed on Desktop2 under Bob's account.


![Rename Step 1](../images/lab11/step1-8.png)



We can also navigate to the CPU section on the left to see how many CPU cores are available on Desktop2. It will also provide information about the processors being used on the system.


![Rename Step 1](../images/lab11/step1-9.png)



The Environment tab on the left shows us the path directories configured on Desktop2 as well.


![Rename Step 1](../images/lab11/step1-10.png)


We can look into Printers and see which printer machines are installed on Desktop2 as well.



![Rename Step 1](../images/lab11/step1-11.png)



On the Shares tab, we can see our shared drives.


![Rename Step 1](../images/lab11/step1-12.png)


If we wanted to remote admin into Desktop2 then double click on “ADMIIN$”, here we can see things on a system level.



![Rename Step 1](../images/lab11/step1-13.png)



If we wanted to add a specific file to Desktop2, we can double click on “C$” then add anything in there.


![Rename Step 1](../images/lab11/step1-14.png)



Lets copy the text document “results” then go into “Users” → into “Bob” → then “Desktop”.




![Rename Step 1](../images/lab11/step1-15.png)




Paste the copied "results" file onto the Desktop, and we can see that the file was successfully transferred to our Desktop2 VM from our Windows Server 2022 VM using PDQ Inventory.



![Rename Step 1](../images/lab11/step1-16png)



Some additional features in PDQ Inventory include Manage with MMC, which allows us to manage Computer Management on the Desktop2 VM directly from PDQ Inventory. To use this, select Tools at the top, then choose Manage with MMC.



![Rename Step 1](../images/lab11/step1-17.png)




We can create a new user on Desktop2 if we wanted to by using this feature.


![Rename Step 1](../images/lab11/step1-18.png)




Another tool we can use is “Remote Desktop” if we want to remote into Desktop2 from PDQ Inventory.


![Rename Step 1](../images/lab11/step1-19.png)



![Rename Step 1](../images/lab11/step1-20.png)




Another powerful feature we can use is remotely rebooting Desktop2. To do this, select Tools, then choose Reboot/Shutdown.



![Rename Step 1](../images/lab11/step1-21.png)





![Rename Step 1](../images/lab11/step1-22.png)



Now, let's print a report on Desktop2. Return to the home page in All Computers, right-click on Desktop2, and select Print Preview. This feature is useful if, for example, a manager requests a report on a specific user's computer.



![Rename Step 1](../images/lab11/step1-23.png)




Now, let's print a report on the hardware devices on Desktop2. Right-click on Desktop2, then select Run Report → Hardware Devices. This will generate a report of all the hardware devices installed on Desktop2.



![Rename Step 1](../images/lab11/step1-24.png)



Select the printer icon on the top left to preview the report. This will display a list of all the hardware devices associated with Desktop2.


![Rename Step 1](../images/lab11/step1-25.png)




Lastly, we can launch PDQ Deploy for Desktop2 through PDQ Inventory. In All Computers, right-click on Desktop2, select Tools, and then choose Run PDQ Deploy.



![Rename Step 1](../images/lab11/step1-26.png)



From here, we can deploy applications or software packages onto Desktop2 using this feature. Let's select the Mozilla Firefox package that we previously installed on our Windows Server 2022 VM, then click OK to deploy it onto the Desktop2 VM.



![Rename Step 1](../images/lab11/step1-27.png)



Notice on the left that Desktop2.SimoTech.com is the target for the Firefox application deployment. Now, select Deploy Now to begin the deployment process.



![Rename Step 1](../images/lab11/step1-28.png)



Now, we can see that Firefox has been successfully installed on our Desktop2 VM through the PDQ Deploy deployment process.



![Rename Step 1](../images/lab11/step1-29.png)



---



Congratulations! We have successfully completed Home Lab 10 on PDQ Deploy and Inventory!

This project focused on using PDQ Inventory within a VirtualBox environment to track and manage hardware and software across virtual machines. We explored creating and analyzing reports, gaining insights into user resources, and generating reports for managers or supervisors.

👉 Next Lab 12 : Printer Setup on Server 2022, NTFS Permissions



























