<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>
This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop Protocol
- Active Directory Domain Services
- PowerShell ISE
- Domain Controller (Server Manager)
- NIC
- DHCP, DNS, and Servers
- Client (Computer)
- ICMP
- CMD Line Tools
- Firewall

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)
- macOS Sonoma (Host)

<h2>High-Level Deployment and Configuration Steps</h2>

- Set up Domain Controller (Server Manager)
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
<img src="https://github.com/user-attachments/assets/92f14c35-61f5-41df-a04a-cad3b2e85b0f"/>
</p>
<p>
Created VMs in Azure for virtual network resources. Configured NIC to static where IP addresses are assigned. The domain controller is created and set to static. Set up Client 1 to join the domain. Set Client 1 to join the private IP address of the domain controller. 
</p>
<br />

<p>
<img src="https://github.com/user-attachments/assets/0d43f16b-d577-440b-8ec1-1490e8af7eb5"/>
</p>
<p>
ICMP is a protocol that Ping uses. Ping -t ping domain controller's private IP address from Client 1. Configured firewall in wf.msc to open the port of domain controller for Client 1. Logged in to the domain as website.com\username. 
</p>
<br />

<p>
<img src="https://github.com/user-attachments/assets/3a82db2e-7232-4776-933f-45ab38246ecb"/>
</p>
<p>
Configured Active Directory in Domain Controller. Created organizational units. Checked ipconfig /all to inspect DNS settings. Checked ping ipaddress to show working connection. Created an administrator and logged in on Client 1. Created users from the admin account. Edited group policy groups. Users were able to login to Client 1. Created a Powershell ISE script to have thousands of users. Troubleshooted password resets, disable/enable accounts, unlock accounts. Managed AD security groups and domain admins. 
</p>
<br />
