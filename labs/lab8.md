# Lab 8 –Lab 8 Windows 10 Remote Access: Remote Desktop, Remote Registry

## Overview
This section of my home lab documentation focuses on setting up and using Remote Desktop and Remote Registry for remote access to a Windows 10 machine in a VirtualBox environment. The project covers the steps for enabling, configuring, and troubleshooting remote access services to allow users and administrators to connect to and manage a Windows 10 PC remotely.

## Objectives
Windows 10 Remote Management: Configuring and managing remote access to Windows 10 systems.
Remote Registry: Exploring the Remote Registry feature to manage registry settings from another computer.
Remote Desktop: Setting up and utilizing Remote Desktop for secure remote control of Windows 10 systems.
C$ Administrative Share: Understanding and using the hidden C$ administrative share for file and system access.

---

## Documentation
In this home lab, we will focus on using Windows 10 Remote Management, Remote Registry, Remote Desktop, and accessing C$. Let's begin by enabling Windows 10 Remote Desktop Services on Desktop2 for Bob. On Desktop2, open File Explorer, right-click on "This PC," and select "Advanced System Settings." Next, use your Helpdesk administrative permissions to enable "Allow Remote Connections" and click on "Select Users" to add the necessary users.



![Rename Step 1](../images/lab7/step1-1.png)



Select “Add” then add Helpdesk then select “OK” then “Apply”.


![Rename Step 1](../images/lab7/step1-1.png)



Now that Remote Desktop is enabled, let's switch to the Helpdesk account. Search for "Remote Desktop Connection" in the Windows search bar and open the application. In the "Computer" field, type "Desktop2" and log in using your Helpdesk credentials. Once the remote session is active, you can select "Yes" to disconnect Bob's session, allowing you to log in to Desktop2 under the Helpdesk account.


![Rename Step 1](../images/lab7/step1-1.png)


Now that we're remotely accessing Bob's computer from the Helpdesk account, we can perform various tasks. For example, we can create a new folder for Bob by navigating to his folder, then opening the "Desktop" directory and creating a folder there.


![Rename Step 1](../images/lab7/step1-1.png)


We can also delete things in Bob’s download’s folder if Bob wants to.
We can also access Bob’s AppData folder by navigating to User → Bob and typing \appdata in the File Explorer search bar. This will allow us to view and manage the contents of Bob’s AppData directory.

![Rename Step 1](../images/lab7/step1-1.png)



Let's disconnect from the Remote Desktop Connection and log back in as Bob on Desktop2. Once logged in, we should see the "Test" folder on Bob's desktop.

![Rename Step 1](../images/lab7/step1-1.png)



Next, let's show how to determine shared drives. On Desktop2, open Command Prompt (CMD) and type net use. This will display a list of all the network drives currently mapped to the system.

![Rename Step 1](../images/lab7/step1-1.png)



Another way to determine shared drives is to search for "Services" in the Windows search bar and run it as Administrator. Use Helpdesk credentials to bypass. In the Services window, search for "Remote Registry," right-click on it, and select "Properties." Change the "Startup type" from "Disabled" to "Automatic," then click "Apply" and "OK." After that, click "Start" to enable the Remote Registry service. This will allow access to registry information, including shared drives.


![Rename Step 1](../images/lab7/step1-1.png)


![Rename Step 1](../images/lab7/step1-1.png)


Now lets go to our Helpdesk account, search up “Registry Editor”


![Rename Step 1](../images/lab7/step1-1.png)



Select File on the top left → Connect Network Registry → then search “Desktop2” then “OK”.


![Rename Step 1](../images/lab7/step1-1.png)


![Rename Step 1](../images/lab7/step1-1.png)


Under HKEY_USERS, we need to browse through the folders to find the one associated with the "Z" drive under the "Network" section. This will show the shared drives that are mapped to the system. The drive letter "Z" will be listed within the registry key associated with the network shares, which helps to identify the shared drives connected to the machine.


![Rename Step 1](../images/lab7/step1-1.png)




Now, let's use the C$ command with our Helpdesk account, which allows administrators to remotely access the root of the C: drive on the local user account. To do this, open File Explorer on Helpdesk and type \Desktop2\c$ in the search bar, then press Enter. This will grant access to the C: drive of Desktop2 remotely.


![Rename Step 1](../images/lab7/step1-1.png)



From here, we can delete the "Test" folder we created remotely. Navigate to Users → Bob → Desktop, and then locate the "Test" folder. Once found, simply delete the folder to remove it from Bob's desktop.

![Rename Step 1](../images/lab7/step1-1.png)




Now if we check back on Bob’s computer we see that the “Test” folder is no longer in Bob’s desktop.

![Rename Step 1](../images/lab7/step1-1.png)



Another way to remote into a users is using Windows Remote Assistance by typing “Windows Remote Assistance” in the Windows search on Desktop2 → then select “Invite someone you trust to help you”.


![Rename Step 1](../images/lab7/step1-1.png)


Another way to remote into a users is using Windows Remote Assistance by typing “Windows Remote Assistance” in the Windows search on Desktop2 → then select “Invite someone you trust to help you”.
If you dont have that, Windows + R TYPE "msra" 

![Rename Step 1](../images/lab7/step1-1.png)


Select “Save this invitation as file” on desktop.


![Rename Step 1](../images/lab7/step1-1.png)



Now, back on the Helpdesk account, open Windows Remote Assistance and select Help Someone Who Has Invited You. In the prompt, type \Desktop2\C$ to access the invitation file. Once connected, navigate to Users → Bob → Desktop and locate the invitation file there. Afterward, you can enter the password provided in the invitation to establish the remote session.

A prompt will ask if we want to allow Helpdesk to remote access, select “Yes”.

Now we have remote control of Bob’s computer on Helpdesk.

![Rename Step 1](../images/lab7/step1-1.png)



Now we can send chats to Bob, request control access on the top left.



![Rename Step 1](../images/lab7/step1-1.png)


---

Congratulations! we have successfully access Windows 10 Remote Management exploring the Remote Registry feature, setting up and utilizing Remote Desktop for secure remote control of Windows 10 system and using C$.

👉 Next Lab 9 : RSOP, Group Policy, Task Manager, Disable Logoff
























