<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools
- Various Network Protocols (SSH, RDH, DNS, HTTP/S, ICMP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Ubuntu Server 20.04

<h2>High-Level Steps</h2>

- Download and install Wireshark
- Observe ICMP Traffic
- Observe SSH Traffic
- Observe DHCP Traffic
- Observe DNS Traffic

<h2>Prerequisites</h2>

- Resource Group with 2 VM's ( 1 x Windows 10 and 1 x Linux[Ubuntu])

<h2>Actions and Observations</h2>

<h3>Download and install Wireshark</h3>

<p>
Copy public IP for Windows VM (VM 1) and log in via Remote Desktop
</p>
<p>
<img src="https://i.imgur.com/WGLapO0.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<br />

<p>
Go to https://www.wireshark.org/download.html and download Wireshark
</p>
<p>
<img src="https://i.imgur.com/x0I7e8c.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<br />

<p>
Install Wireshark on VM using defaults
</p>
<p>
<img src="https://i.imgur.com/BQEsYNL.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<br />

<p>
Select 'Ethernet' then 'Start capturing packets' (blue fin)
</p>
<p>
<img src="https://i.imgur.com/bF7Z4Zu.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<br />

<h3>Observe ICMP Traffic</h3>

<p>
In the filter bar type 'icmp' and press enter
</p>
<p>
<img src="https://i.imgur.com/xemoEhU.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<br />

<p>
Get privte IP for the Linux VM (VM 2)
</p>
<p>
<img src="https://i.imgur.com/rewRwHB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<br />

<p>
Open Powershell on VM 1 and ping the private IP on VM 2
</p>
<p>
<img src="https://i.imgur.com/rrrX2lg.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<br />

<p>
In Azure Portal go to VM 2's Network security group
</p>
<p>
<img src="https://i.imgur.com/tAbzHMd.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<br />

<p>
Go to Inbound security rules
</p>
<p>
<img src="https://i.imgur.com/KWA4P78.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<br />

<p>
Add new rule to deny any ICMP traffic from VM 1
</p>
<ul><li>Protocol: ICMP</li><li>Priority: 200</li></ul>
<p>
<img src="https://i.imgur.com/xuoG4re.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<br />

<p>
Go back to VM 1 and observe ping timing out
</p>
<p>
<img src="https://i.imgur.com/1NKK7lp.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<br />

<p>
Go back to VM 2's Network security rules and allow ICMP traffic then refresh
</p>
<p>
<img src="https://i.imgur.com/kkwr0E9.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<br />

<p>
Observe ICMP request and reply in Wireshark (ping no longer timing out)
</p>
<p>
<img src="https://i.imgur.com/6TJQrM5.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<br />

<h3>Observe SSH Traffic</h3>

<p>
Change filter to ssh
</p>
<p>
<img src="https://i.imgur.com/EagW7ME.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<br />

<p>
In Powershell type 'ssh {VM 2 username}@[VM 2 private IP]', type yes, enter VM 2 password
</p>
<p>
<img src="https://i.imgur.com/1wDyMjd.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<br />

<p>
Enter any Linux commands in Powershell ad observe the traffic, type 'exit' to close ssh connection
</p>
<p>
<img src="https://i.imgur.com/GUhI5T1.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<br />

<h3>Observe DHCP Traffic</h3>

<p>

</p>
<p>
<img src="https://i.imgur.com/vvGJNec.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<br />

<p>

</p>
<p>
<img src="" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<br />

<p>

</p>
<p>
<img src="" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
