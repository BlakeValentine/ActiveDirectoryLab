<h1>Running Active Directory | Adding Bulk Users with Powershell</h1>

<h2>Description</h2>
Hey there! In today's lab, we're going to dive into creating your very own Active Directory home lab using Oracle VirtualBox. It's like building your own little digital playground! This hands-on experience will give you a better grasp of how Active Directory works in Windows. I recommend going through this a couple of times to really get the workflow. Don't hesitate to reach out if you've got any questions – I'm here to help!
<br />


<h2>Platforms Used Used</h2>

- <b>Oracle VirtualBox</b>
- <b>Server2019</b> 
- <b>Powershell</b>

<h2>Environments Used </h2>

- <b>Windows 10</b> 

<h2>Creating a Virtual Machine</h2>

<p align="center">
Download and install Oracle Virtual Box.</a> <br/>
<img src="https://i.imgur.com/xZXI8at.png" height="80%" width="80%" alt="Download Virtual Box"/>
<br />
Tip - Don't forget to install the extension pack.
<br />
<br />
Download Server 2019 ISO.
<br/>
<img src="https://i.imgur.com/QphdPUo.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Download Windows 10 ISO.
<br/>
<img src="https://i.imgur.com/wA22Vsn.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
We'll now establish our Domain Controller. Open VirtualBox, select "New," name the VM, and for Version, select "Windows Other (64-Bit)." 
<br/>
<img src="https://i.imgur.com/rlThy4y.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Configure VM System Settings. Values like RAM will depend on your individual system's capabilities.
<br/>
<img src="https://i.imgur.com/2aex0VI.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Configure VM Network Settings. We are setting up two NICs for this lab. One is going to be used to connect to the internet, and the other will be our client's internal private network.
<br/>
<img src="https://i.imgur.com/SGmY2qG.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://i.imgur.com/VbbZHX6.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Launch the VM. When prompted, open the ISO file for Server 2019.  
<br/>
<img src="https://i.imgur.com/6LiaH7V.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Install Windows Server 2019.  <br/>
<img src="https://i.imgur.com/PZW8YQT.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<h2>Guest Additions and TCP/IP Addressing</h2>

<p align="center">
Congratulations! You've installed Windows Server 2019. Navigate to Devices and select Insert Guest Additions CD image. This will add many quality of life improvements to the functionality of the VM.
<img src="https://i.imgur.com/iE5Jtpq.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
In File Explorer, you can access the CD Drive to launch the Guest Additions installer.
<img src="https://i.imgur.com/dpi2U6T.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Select VBoxWindowsAdditions-amd64.exe.
<img src="https://i.imgur.com/9CPydl6.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Now it's time to assign our IP Addressing. Remember our Domain Controller will have two NICs. The external one that is dedicated to the internet will receive an IP address through your home router. The internal NIC will need to be manually configured.
<br />
<img src="https://i.imgur.com/czCwcHS.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Select change adapter options. 
<img src="https://i.imgur.com/YCWdzz2.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Confirm your external and internal NICs by checking their IP addresses. Remember, the internal NIC did not receive an IP address from DHCP, so it will have 169.254 in the address.
 <br />
<img src="https://i.imgur.com/7388oV4.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Update the IP Addressing on our internal NIC to match the config sheet.
<img src="https://i.imgur.com/HTfb3BU.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
 
<h2>Installing Active Directory </h2>

<p align="center">
We will now install Active Directory Domain Services.
<img src="https://i.imgur.com/Hoh5SxT.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
This installation wizard will be used often as we add roles to the Domain Controller. 
<img src="https://i.imgur.com/vloZoCQ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Select Active Directory Domain Services and proceed through the wizard. Close the installer when finished.
<img src="https://i.imgur.com/iYC6soa.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Select the yellow status notification button to continue to the post-deployment configuration.
<br />
<img src="https://i.imgur.com/J7M9P8p.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Add a new forest, specify the domain name, and complete the configuration.
<img src="https://i.imgur.com/6j3VMeq.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
The computer will now restart. 
<img src="https://i.imgur.com/RWlLQsa.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Now we’ll create our own dedicated admin account. Open Active Directory Users and Groups.
<br />
<img src="https://i.imgur.com/4OIej2b.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Select our newly created domain. 
<img src="https://i.imgur.com/4OIej2b.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
We’ll create a new Organizational Unit for our dedicated admin account.
<img src="https://i.imgur.com/4OIej2b.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Name the Organizational Unit _ADMINS.
<img src="https://i.imgur.com/4OIej2b.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Start -> Windows Administrative Tools -> Active Directory Users and Computers.
<img src="https://i.imgur.com/4OIej2b.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Create a new user account. 
 <br />
<img src="https://i.imgur.com/4OIej2b.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Select the new user account -> Properties -> Member of -> Add.
<img src="https://i.imgur.com/4OIej2b.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Add to “Domain Admins” group.
<img src="https://i.imgur.com/4OIej2b.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Test your new admin account by signing out and trying to sign in with the credentials you’ve created.
 <br />
<img src="https://i.imgur.com/4OIej2b.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<h2>Next, we’ll be installing RAS / NAT.</h2>

<p align="center">
When we create our Windows 10 client, this will allow us to connect to the internet through the domain controller. Select "Add Roles and Features". 
 <br />
<img src="https://i.imgur.com/4OIej2b.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Install remote access and routing.
 <img src="https://i.imgur.com/4OIej2b.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Close the installation wizard when finished.<img src="https://i.imgur.com/4OIej2b.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Go to tools in the top right corner.
<img src="https://i.imgur.com/4OIej2b.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Scroll down to routing and remote access.
<img src="https://i.imgur.com/4OIej2b.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
We’ll now configure the Domain Controller.
<img src="https://i.imgur.com/4OIej2b.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
 Select the external NIC as the public interface to connect to the internet.
 <img src="https://i.imgur.com/4OIej2b.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
 
<h2>Now it’s time to set up a DHCP Server</h2>

<p align="center">
Go back to Add Roles and Features.
<br />
<img src="https://i.imgur.com/4OIej2b.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Install DHCP.
 <br />
<img src="https://i.imgur.com/4OIej2b.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Go to tools in the top right corner.
<img src="https://i.imgur.com/4OIej2b.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Select DHCP.
<br />
<img src="https://i.imgur.com/4OIej2b.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
In DHCP Control Panel select the Domain Controller.
<img src="https://i.imgur.com/4OIej2b.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
In the drop-down menu, right-click IPV4 and select New Scope.
<img src="https://i.imgur.com/4OIej2b.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Use the details from the configuration chart and proceed through the wizard.
<img src="https://i.imgur.com/4OIej2b.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Authorize
<br />
<img src="https://i.imgur.com/4OIej2b.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<h2>Running our Powershell Script</h2>

<p align="center">
A quick configuration change will let us browse the internet from the domain controller. NOTE - Never do this in a production environment. It’s okay for this lab.
<br />
<img src="https://i.imgur.com/4OIej2b.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Click configure this local server.
<img src="https://i.imgur.com/4OIej2b.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Disable internet explorer enhanced security.
<img src="https://i.imgur.com/4OIej2b.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Paste link for PowerShell user generator script.
<img src="https://i.imgur.com/4OIej2b.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Extract the script to the desktop.
<img src="https://i.imgur.com/4OIej2b.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
In the folder, you will see a plain txt file and the PowerShell script.
<img src="https://i.imgur.com/4OIej2b.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
You can add your name to the list. Then save and close.
<img src="https://i.imgur.com/4OIej2b.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Click on start and then go to Windows PowerShell, select Windows PowerShell ISE, more, and run as administrator.
<br />
<img src="https://i.imgur.com/4OIej2b.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Go to Open.
<br />
<img src="https://i.imgur.com/4OIej2b.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Open the Powershell script on the desktop
<img src="https://i.imgur.com/4OIej2b.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
By default, there is a security feature you must get around to complete this lab.
<img src="https://i.imgur.com/4OIej2b.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Enter set-execution policy unrestricted.
<img src="https://i.imgur.com/4OIej2b.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Change the directory to the folder that the script is actually housed in.
<img src="https://i.imgur.com/4OIej2b.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Hit Run.
<br />
<img src="https://i.imgur.com/4OIej2b.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Check Active Directory, and you should notice a ton of new users.
<img src="https://i.imgur.com/4OIej2b.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<h2>Creating our Client VM</h2>

<p align="center"
Go to VirtualBox.
<img src="https://i.imgur.com/4OIej2b.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Create a new VM.
<br>
<img src="https://i.imgur.com/4OIej2b.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Name it Client1.
<br />
<img src="https://i.imgur.com/4OIej2b.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
For the network - Instead of using NAT, we’re going to click internal. This machine will receive a DHCP address from the domain controller.
<img src="https://i.imgur.com/4OIej2b.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Start the virtual machine loading the Windows 10 ISO.
<img src="https://i.imgur.com/4OIej2b.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Complete the installation of Windows 10.
<img src="https://i.imgur.com/4OIej2b.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Open command prompt.
<br />
<img src="https://i.imgur.com/4OIej2b.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Ipconfig - Check for default gateway.
<img src="https://i.imgur.com/4OIej2b.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Ping to the internet.
<br />
<img src="https://i.imgur.com/4OIej2b.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Rename the PC Client1.
<br />
<img src="https://i.imgur.com/4OIej2b.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Join the PC to the domain.
<br />
<img src="https://i.imgur.com/4OIej2b.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Log in with one of the newly created user accounts.
<img src="https://i.imgur.com/4OIej2b.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
You have officially completed the lab! Great job.
<img src="https://i.imgur.com/4OIej2b.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />

<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
