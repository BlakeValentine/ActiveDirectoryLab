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
<img src="https://i.imgur.com/AeZkvFQ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
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
