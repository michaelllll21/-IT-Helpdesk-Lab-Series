# Lab 7 – Lab 7 Security Groups, Mapped Drives, Personal Drives

## Overview
This section of my home lab documentation focuses on managing Security Groups, Mapped Drives, and Personal Drives in a domain environment. The project demonstrates how to create and configure security groups for managing permissions, set up mapped drives for network access, and configure personal drives for user-specific storage.

## Objectives
Create and configure Security Groups in Active Directory to manage access to resources and network drives.
Set up Mapped Drives to enable users to access shared resources across the network automatically.
Configure Personal Drives for individual users to store data securely in the domain environment.
Implement best practices for permission management using security groups and ensuring appropriate access control for mapped and personal drives.
---

## Documentation
In this home lab, we will focus on implementing Security Groups, Mapped Drives, Personal Drives, and Drive Letter Mapping. Let’s start by opening Server Manager on our Windows Server 2022. Then, select File and Storage Services on the left-hand side, followed by Shares. Right-click and select New Share.

![Rename Step 1](../images/lab7/step1-1.png)



Click Next until you reach the Specify Share Name screen. Name the share HR, then continue selecting Next until you reach the Create button. Click Create to finish setting up the shared folder.


![Rename Step 1](../images/lab7/step1-2.png)



Repeat the process, but this time name the share Personal. Select Next, then click Create to complete the setup for the second shared folder.


![Rename Step 1](../images/lab7/step1-3.png)


Now that we have our shared folders, open File Explorer → This PC → Local C Drive → Shares to access the shared folders.

![Rename Step 1](../images/lab7/step1-4.png)


Now, go to Active Directory Users and Computers → right-click on Users → select New → then click Group to create a new security group.


![Rename Step 1](../images/lab7/step1-5.png)

Name the group name “HR”.


![Rename Step 1](../images/lab7/step1-6.png)


We will create another group the same way and call it “Personal” and have it managed by Helpdesk as well.

![Rename Step 1](../images/lab7/step1-7.png)


Now, go back to the shared folders. Right-click on Personal → select Properties, then navigate to the Sharing tab. Highlight the path \SERVER2022\Personal, right-click, and select Copy. Then, paste this path into the Description field of the Personal properties in Active Directory Users and Computers.


![Rename Step 1](../images/lab7/step1-8.png)


![Rename Step 1](../images/lab7/step1-9.png)



Repeat the process for the HR share folder. Once that’s done, open the HR group in Active Directory Users and Computers and click on the Members tab. Select Add, then search for and add Bob to the group.


![Rename Step 1](../images/lab7/step1-10.png)


Repeat the process for the Personal share folder. Open the Personal group in Active Directory Users and Computers, click on the Members tab, select Add, and then add Bob to the group.

![Rename Step 1](../images/lab7/step1-11.png)



To verify, select the HR organizational unit in the domain, then double-click on Bob. Next, go to the Member Of tab to confirm that Bob is a member of the HR group.



![Rename Step 1](../images/lab7/step1-12.png)


Now, we will focus on configuring the correct permissions. To do this, navigate to the Personal share folder, right-click on it, and select Properties. In the Security tab, click on Advanced, then select Disable Inheritance.

Select the first option “Covert inherited permissions…”


![Rename Step 1](../images/lab7/step1-13.png)


Now remove both “Users”. This removes any users who do not have access to this personal folder.


![Rename Step 1](../images/lab7/step1-14.png)


Click Add, then select Select a principal. Add the Helpdesk group and assign the Modify permission under the basic permissions section.


![Rename Step 1](../images/lab7/step1-15.png)


Repeat the process and add the Personal group, ensuring the Modify permission is enabled under the basic permissions section.


![Rename Step 1](../images/lab7/step1-16.png)


Now, in the Personal folder properties, navigate to the Sharing tab → select Share... → right-click on Personal → choose Read/Write, then click Share.


![Rename Step 1](../images/lab7/step1-17.png)


Now, repeat the process on the HR folder:

Right-click on HR → select the Security tab → click Advanced.

Select Disable Inheritance → choose Convert inherited permissions....

Delete the two Users permissions.

Click Add, then Select a Principal, and add Helpdesk.

Enable Modify for basic permissions.

Click OK, then Apply.

![Rename Step 1](../images/lab7/step1-18.png)



Now, let's repeat the same process for the HR folder:

Right-click on HR → select the Security tab → click Advanced.
Click Add, then Select a Principal, and add HR.
Enable Modify for basic permissions.
Click OK, then Apply.
This will allow HR group members to access the HR shared folder with the proper permissions.



![Rename Step 1](../images/lab7/step1-19.png)



To ensure the HR group can "Read/Write" in the sharing properties, follow these steps:

Right-click on the HR folder.
Select Properties and go to the Sharing tab.
Click Share….
In the Network Access window, ensure HR is listed.
Right-click on HR and select Read/Write.
Click Share to confirm the settings.
This ensures that members of the HR group have the correct permissions to both read and write to the HR shared folder.


![Rename Step 1](../images/lab7/step1-20.png)



To check Bob's access to the HR folder on Desktop2:

Log in as Bob on the Desktop2 account.
Open File Explorer.
In the File Explorer search bar, paste the following network path:\\Server2022\HR
Press Enter to navigate to the HR shared folder.
Since Bob is part of the HR group, he should have access to this folder. You should be able to see the contents of the HR folder. If you followed the permissions setup correctly, Bob should have Read/Write access to this folder.



![Rename Step 1](../images/lab7/step1-21.png)


![Rename Step 1](../images/lab7/step1-22.png)


![Rename Step 1](../images/lab7/step1-23.png)




Another method to map a personal drive is by accessing your Windows Server 2022 account, copying the network path from the "Personal Properties" section in the shared folders.


![Rename Step 1](../images/lab7/step1-24.png)


Next, open Active Directory Users and Computers, search for "Bob," right-click on his name, and select "Properties." Then, go to the "Profile" tab and under "Home Folder," choose "Connect" and set the drive letter to P:. Paste the network path for the drive: \SERVER2022\Personal\%username% (make sure to include "%username%"). Finally, click "Apply." This will create a personal folder within Bob's directory.



![Rename Step 1](../images/lab7/step1-26.png)


Once we log into Desktop2 as Bob, we will see that both the Personal and HR drives are mapped.



![Rename Step 1](../images/lab7/step1-27.png)

---

Congratulations we have successfully configured on how to implement Security Groups, Map Drives, Personal Drives and Map Letter.

👉 Next Lab 8 : Windows 10 Remote Access: Remote Desktop, Remote Registry








