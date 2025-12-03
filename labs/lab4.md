### Lab 4 — Installing Windows 10, Joining a PC to the Domain, Installing RSAT, and Using Server Manager

## Overview
In this lab, we will install **Windows 10**, join it to our **SimoTech.com** domain using the **Helpdesk account**, install **RSAT (Remote Server Administration Tools)**, and verify domain management using **Server Manager**.  
This simulates real-world helpdesk responsibilities and domain onboarding tasks.

---

## Objectives
- Install and set up Windows 10 in VirtualBox
 Windows 10 Installation Media Tool.

![Rename Step 1](../images/lab4/properties.png)

Next, open your VirtualBox application and create a new virtual machine. Click Machine in the top-left corner, then select New.

![Rename Step 1](../images/lab4/properties.png)

Name the virtual machine "Windows 10 Project." For the ISO image, navigate to the Downloads folder, click the dropdown icon, select "Other," and choose the "Windows" ISO file. Then, select "Skip unattended installation.”

![Rename Step 1](../images/lab4/properties.png)

Select Hardware, and by default, the base memory is set to 2048 MB. Increase it to 6081 MB. Finally, click Finish and start the machine by pressing Start. On the Windows Setup screen, click Next, then Install Now.

![Rename Step 1](../images/lab4/properties.png)


![Rename Step 1](../images/lab4/properties.png)


Select “I don’t have a product key”.

![Rename Step 1](../images/lab4/properties.png)

Make sure to select "Windows 10 Pro," check the box to accept the license terms, and click Next.

![Rename Step 1](../images/lab4/properties.png)

Select "Custom: Install Windows only," then click Next to begin the installation of Windows 10.

![Rename Step 1](../images/lab4/properties.png)

✅ SOLVE: PAANO ITIGIL ANG PAG-LOOP SA INSTALLATION
STEP 1 — I-shutdown ang VM
Kung nasa installer ka:
Click X sa top ng VM window
Piliin Power off the machine
OK

STEP 2 — REMOVE the ISO from the VM
Sa VirtualBox main screen, i-select ang Windows 10 VM
Click Settings
Go to Storage
Sa Controller: IDE / SATA, i-click ang ISO file (Windows10.iso)
Click the CD icon sa right
Piliin Remove disk from virtual drive
Dapat mawala yung .iso sa list.

STEP 3 — Check Boot Order
Still inside Settings → System → Motherboard
Make sure:

✔ Hard Disk
✖ Optical (CD/DVD)
✖ Floppy
I-move Hard Disk sa taas.

STEP 4 — Start the VM
Pag-start mo, dapat ganito lalabas:

✔ Windows logo
✔ “Getting devices ready…”
✔ Your Windows 10 login screen


Select “Personal use”.

![Rename Step 1](../images/lab4/properties.png)

On the bottom left, select “Offline account”.

![Rename Step 1](../images/lab4/properties.png)

Enter "User" as the name, skip the password creation, and click Next.

![Rename Step 1](../images/lab4/properties.png)



---


For best practice in a lab environment, we’ll configure static IP addresses for both virtual machines. This ensures consistent network communication and allows us to successfully connect the Windows 10 machine to the domain, enabling seamless interaction between the two virtual machines. Next, switch to the Windows Server 2022 virtual machine. Open the Control Panel and go to View network status and tasks → Change adapter settings. Right-click the network connection (Ethernet) and select Properties to begin configuring the network settings.

![Rename Step 1](../images/lab4/properties.png)

![Rename Step 1](../images/lab4/properties.png)

Double-click on Internet Protocol Version 4 (TCP/IPv4).

![Rename Step 1](../images/lab4/properties.png)

Select Use the following IP address, then configure the static IP address as follows:

IP Address: 12.1.10.2
Subnet Mask: 255.0.0.0
Default Gateway: 12.1.10.1
Preferred DNS: 12.1.10.2
Alternate DNS: 12.1.10.1
Click OK to save the settings.

![Rename Step 1](../images/lab4/properties.png)


Next, modify the network settings on the virtual machine by selecting Devices at the top, then choose Network and go to Network Settings.

![Rename Step 1](../images/lab4/properties.png)

Now, switch back to the Windows 10 Project machine and enable the administrator account. Open File Explorer, right-click This PC, and select Manage. This will open Computer Management.

![Rename Step 1](../images/lab4/properties.png)

Expand Local Users and Groups, then select Users. Right-click on Administrator and click Properties.

![Rename Step 1](../images/lab4/properties.png)

The Account is disabled option is checked by default. Uncheck it, then select Apply and click OK.

![Rename Step 1](../images/lab4/properties.png)

Next, click on Administrator again and select Set Password → Proceed. Create a password, then click OK. A prompt will appear confirming that your password has been set.

![Rename Step 1](../images/lab4/properties.png)


Now that the Administrator account is enabled and the password is set, log into that account by first signing out of your Windows 10 Project machine. Right-click the bottom-left Windows icon, select Shut down or sign out, and then choose Sign out.

Now that the Administrator account is available, we will log into it instead.

![Rename Step 1](../images/lab4/properties.png)

![Rename Step 1](../images/lab4/properties.png)


Since the default 'User' account can be accessed without a password, we will remove it to enhance security and prevent unauthorized access. Open File Explorer, right-click This PC, and choose Manage. Navigate to Local Users and Groups and select Users. To delete the 'User' account, right-click on it and select Delete.

![Rename Step 1](../images/lab4/properties.png)

To confirm that the 'User' account has been successfully removed, log out and ensure that the only password-protected account remaining is the 'Administrator' account. We have now successfully set up our local Help Desk account. This procedure removes weak default accounts, enhancing the security of Windows 10.


![Rename Step 1](../images/lab4/properties.png)


---

Next, we will download the RSAT tools to enable access to Active Directory on a local level. Type "Optional" in the search bar at the bottom left and click on Add an optional feature, then select Add a feature.

![Rename Step 1](../images/lab4/properties.png)

![Rename Step 1](../images/lab4/properties.png)

Type "RSAT" in the search bar for a quicker search, then install the following 7 features:

RSAT: Active Directory Certificate Services Tools
RSAT: Active Directory Domain Services and Lightweight Directory Services Tools
RSAT: DHCP Server Tools
RSAT: DNS Server Tools
RSAT: Group Policy Management Tools
RSAT: Remote Desktop Services Tools
RSAT: Server Manager
Click Install (7). Once the installation is complete, restart the virtual machine.

![Rename Step 1](../images/lab4/properties.png)

![Rename Step 1](../images/lab4/properties.png)

Now that all of our administrative tools are installed, we can verify this by clicking the Windows icon at the bottom left and looking for Windows Administrative Tools.

![Rename Step 1](../images/lab4/properties.png)

Now, let's add our PC to the domain SimoTech.com. Before doing that, let's rename our PC to Desktop1. To do this, open File Explorer, right-click on This PC, and select Properties. Then, click on Rename this PC (advanced), followed by Change. In the Computer name field, enter Desktop1, click OK, and then select Restart now.

![Rename Step 1](../images/lab4/properties.png)

After the restart, open Internet Explorer and download Google Chrome from the web. Once Chrome is installed, download the TeamViewer Full Client 64-bit. We will be using TeamViewer in our upcoming homelabs.

![Rename Step 1](../images/lab4/properties.png)

![Rename Step 1](../images/lab4/properties.png)



---

Next, we will set a static IP on our Windows 10 machine, just as we did with the Windows Server 2022 machine, and join it to the domain SimoTech.com. As before, open Control Panel on your Windows 10 Project machine, select View network status and tasks, then Change adapter settings. Right-click on the Ethernet connection and select Properties, then double-click Internet Protocol Version 4 (TCP/IPv4). Select Use the following IP address and enter the following:

IP Address: 12.1.10.3
Subnet Mask: 255.0.0.0
Default Gateway: 12.1.10.1
Preferred DNS: 12.1.10.2
Alternate DNS: 12.1.10.1
Next, update the network settings on your virtual machine as we did earlier by selecting Devices → Network → Network Settings, and change NAT to Host-only Adapter.

![Rename Step 1](../images/lab4/properties.png)


Now that our networks and static IPs are set up, let's test the connection by pinging our Windows 10 machine from the Windows Server 2022 machine. On the Windows 10 Project machine, open Command Prompt and type: ping 12.1.10.2

This is the static IP we set up for the Windows Server 2022 machine.


![Rename Step 1](../images/lab4/properties.png)

Now that we can ping the Windows Server 2022 machine, we can finally join our Windows 10 machine to the SimoTech.com domain. First, open File Explorer, right-click on This PC, and select Properties. Then, click on Rename this PC (advanced), followed by Change. Under Domain, type SimoTech.com.

![Rename Step 1](../images/lab4/properties.png)

Next, we will use our Administrator account and password to join the domain. Afterward, a prompt will appear asking us to restart the virtual machine to apply the changes.

![Rename Step 1](../images/lab4/properties.png)

To verify that Desktop1 has been successfully added to the SimoTech.com domain, open Active Directory Users and Computers on the Windows Server 2022 machine. Select Computers, and you should see DESKTOP1 listed as part of the domain. Desktop1 will serve as our Helpdesk account.

![Rename Step 1](../images/lab4/properties.png)

Next, on the Windows Server 2022 machine, still in Active Directory Users and Computers, select Users, right-click on Helpdesk, and choose Reset Password. Create a new password for the Helpdesk account. Afterward, use this new password to log into the Windows 10 virtual machine.

![Rename Step 1](../images/lab4/properties.png)

Now, we can sign in to the Helpdesk account on our Windows 10 machine. On the login screen, make sure to select Other Users, and then log in using the Helpdesk account credentials.

![Rename Step 1](../images/lab4/properties.png)


Congratulations! We have successfully set up Windows 10, joined the PC to the domain, and installed the RSAT tools, google and TeamViewer. You can now search for applications like 'Server Manager' and 'Active Directory Users and Computers,' then pin them to the task bar for quick access by right-clicking and selecting 'Pin to taskbar.

![Rename Step 1](../images/lab4/properties.png)


👉 Next Lab 5 : Join Windows 10 to Domain (Local User), Group Policy, RSOP Reports



