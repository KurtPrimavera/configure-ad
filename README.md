<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>
This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />


<h2>Video Demonstration</h2>

- ### [YouTube: How to Deploy on-premises Active Directory within Azure Compute](https://www.youtube.com)

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Set up Domain Controller 
- Create a Network environment in Azure Virtual Network Resources 
- Configure Network Interface Card
- Configure DHCP, DNS, and Servers
- Deploy clients to join the domain
- Monitor ICMP
- Implement cmd line tools
- Configure the firewall
- Implement proper login for the domain
- Configure Active Directory
- Created organizational units
- Configure group policy
- Run PowerShell ISE for administrative tasks
- Troubleshooted user problems 

<h2>Deployment and Configuration Steps</h2>

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Created VMs in Azure for virtual network resources. Configured NIC to static where IP addresses are assigned. The domain controller is created and set to static. Set up Client 1 to join the domain. Set Client 1 to join the private IP address of the domain controller. 
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
ICMP is a protocol that Ping uses. Ping -t ping domain controller's private IP address from Client 1. Configured firewall in wf.msc to open the port of domain controller for Client 1. Logged in to the domain as website.com\username. 
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Configured Active Directory in Domain Controller. Created organizational units. Checked ipconfig /all to inspect DNS settings. Checked ping ipaddress to show working connection. Created an administrator and logged in on Client 1. Created users from the admin account. Edited group policy groups. Users were able to login to Client 1. Created a Powershell ISE script to have thousands of users. Troubleshooted password resets, disable/enable accounts, unlock accounts. Managed AD security groups and domain admins. 
</p>
<br />
