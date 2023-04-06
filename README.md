<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>
The brief explanation here shows the implementation of on-premises Active Directory within Azure Virtual Machines.<br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Set up all resources in Azure
- Install Active Directory on our Domain Controller
- Ensure both VMs are in the same private network by observing ICMP traffic
- Create Admin users and regular users
- Setup Remote Desktop for non-administrative users on Client Virtual Machine

<h2>Deployment and Configuration Steps</h2>

<p>
<img src="https://i.imgur.com/d8my3Ai.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Set up two Virtual Machines(VM) in Azure, one being a Windows Server 2022 which will be our Domain Controller(DC) where we install Active Directory and another VM using Windows 10 which will act as our Client PC. Ensure they are in the same resource group and Vnet in Azure. Remote control the Client pc(Client) and ping the private ip of DC to look for a connection. If there is no connection, enable ICMPv4 in the local firewall of DC. 
</p>
<br />

<p>
<img src="https://i.imgur.com/2g8rp7m.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Install Active Directory Domain Services on the DC and promote it as a DC setting up a new forest. This is when you will name a Domain for your Active Directory.This alters the remote control login to now read the login as a directory. Example sign in would be mydomain.com\Jane.Doe instead of just Jane Doe. In Active Directory Users and Computers, create Organizational units for Employees and Computers. Create multiple users of Admin level and regular level. Creating Admin level users requires changing the security group the user belongs in.
</p>
<br />

<p>
<img src="https://i.imgur.com/GhR0lIQ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
From Client, open system properties and click remote desktop. Allow domain users access to remote desktop. With this, all users in the domain mydomain.com can now access remote control of any computer that is also connected to the private network that the Domain Controller has been given.
</p>
<br />
