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

<h2>Creating our Virtual Machines:</h2>

<p align="center">
Download and install Oracle Virtual Box</a> <br/>
<img src="https://i.imgur.com/xZXI8at.png" height="80%" width="80%" alt="Download Virtual Box"/>
<br />
Tip - Don't forget to install the extension pack: 
<br />
<br />
Download Server 2019 iso:  <br/>
<img src="https://i.imgur.com/QphdPUo.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Download Windows 10 iso: <br/>
<img src="https://i.imgur.com/wA22Vsn.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
We'll now establish our Domain Controller. Open VirtualBox, select "New", name the VM, and for Version select "Windows Other (64-Bit)":  <br/>
<img src="https://i.imgur.com/rlThy4y.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Configure VM System Settings. Values like RAM will depend on your individual system's capabilities:  <br/>
<img src="https://i.imgur.com/2aex0VI.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Configure VM Network Settings. We are setting up two NICs for this lab. One is going to be used to connect to the internet and the other will be our clients internal private network :  <br/>
<img src="https://i.imgur.com/SGmY2qG.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://i.imgur.com/VbbZHX6.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Launch the VM. When prompted open the iso file for Server 2019:  <br/>
<img src="https://i.imgur.com/6LiaH7V.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Install Windows Server 2019:  <br/>
<img src="https://i.imgur.com/PZW8YQT.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<h2>Guest Additions and TCP/IP Addressing:</h2>
<br />
<br />
<p align="center">
Congratulations! You've installed Windows Server 2019. Navigate to Devices and select Insert Guest Additions CD image. This will add many quality of life improvements to the functionality of the VM.
<img src="https://i.imgur.com/iE5Jtpq.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
In File Explorer you can access the CD Drive to launch the Guest Additions installer
<img src="https://i.imgur.com/dpi2U6T.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Select VBoxWindowsAdditions-amd64.exe
<img src="https://i.imgur.com/9CPydl6.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Now it's time to assign our IP Addressing. Remember our Domain Controller will have two NICs. The external one that is dedicated to the internet will receive an IP address through your home router. The internal NIC will need to be manually configured.
<br />
<img src="https://i.imgur.com/czCwcHS.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Select change adapter options 
<img src="https://i.imgur.com/YCWdzz2.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Confirm your external and internal NICs by checking their IP addresses. Remember, the internal NIC did not receive an IP address from DHCP so it will have 169.254 in the address.
<img src="https://i.imgur.com/7388oV4.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Update the IP Addressing on our internal NIC to match the config sheet 
<img src="https://i.imgur.com/HTfb3BU.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
We will now install Active Directory Domain Services
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
Select the yellow status indicator button to continue to the post deployment configuration 
 <br />
<img src="https://i.imgur.com/J7M9P8p.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Add a new forest and complete the configuration.
<img src="https://i.imgur.com/6j3VMeq.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
The computer will now restart. 
<img src="https://i.imgur.com/RWlLQsa.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. 
<img src="https://i.imgur.com/4OIej2b.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. 
<img src="https://i.imgur.com/4OIej2b.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. 
<img src="https://i.imgur.com/4OIej2b.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
