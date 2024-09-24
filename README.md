<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>Cloud-Hosted Active Directory: Deploying On-Premises Solutions in Azure, Joining Client-1 to the Domain, and Managing Users and Administrators </h1>
This tutorial provides a comprehensive guide to implementing on-premises Active Directory within Azure Virtual Machines. The Active Directory was configured on a domain controller to facilitate centralized management of network resources. To successfully join the domain, the Client-1 computer must reside within the same network as the domain controller. The primary administrator, designated as labuser, was responsible for managing user accounts on the domain controller. Utilizing a PowerShell script, labuser efficiently created thousands of client accounts, streamlining the onboarding process. Additionally, other administrators and clients were able to log in on the Client-1 computer, allowing for secure access to shared resources and services within the domain.

This implementation not only enhances organizational security but also simplifies user management and access control across the network. <br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute): A cloud computing platform utilized to host virtual machines, providing scalable resources for deploying and managing Active Directory and other services.
- Remote Desktop Protocol (RDP): A protocol that enables remote access to virtual machines, allowing administrators to manage and configure the domain controller and other components seamlessly.
- Active Directory Domain Services (AD DS): A critical service used for managing domain identities and providing authentication and authorization for users and computers within the network.
- PowerShell ISE: An integrated scripting environment that allows for efficient management and automation of tasks in Windows, including user account creation and system configuration.
- Domain Controller (Server Manager): The server that hosts Active Directory, responsible for managing user accounts, group policies, and security settings within the domain.
- Network Interface Card (NIC): Hardware that connects the server to the network, enabling communication between the domain controller and client machines.
- Dynamic Host Configuration Protocol (DHCP): A network management protocol used to automatically assign IP addresses to devices within the network, ensuring proper connectivity.
- Domain Name System (DNS): A critical service that translates domain names into IP addresses, facilitating network resource access and communication.
- Client (Computer): The end-user device configured to join the Active Directory domain, allowing users to authenticate and access network resources.
- Internet Control Message Protocol (ICMP): A network protocol used for diagnostic purposes, such as pinging devices to test connectivity and network health.
- Command Line Tools (CMD): A suite of command-line utilities used for system administration, troubleshooting, and network configuration tasks.
- Firewall: A security device or software that monitors and controls incoming and outgoing network traffic based on predetermined security rules, protecting the network from unauthorized access.

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
- Troubleshoot user problems
- Windows Settings
- Group Policy Object
- Security Groups

<h2>Deployment and Configuration Steps</h2>

<p>
<img src="https://github.com/user-attachments/assets/92f14c35-61f5-41df-a04a-cad3b2e85b0f"/>
</p>
<p>
Created VMs in Azure for virtual network resources. Configured NIC to static where IP addresses were assigned in Azure. The domain controller was created and set to static in Azure. Used Microsoft Remoted Desktop from my host computer (macOS) to set up Client 1 to join the domain in Windows settings, but did not work. Set up Client 1 to join the private IP address of the domain controller in Azure DNS settings. 
</p>
<br />

<p>
<img src="https://github.com/user-attachments/assets/0d43f16b-d577-440b-8ec1-1490e8af7eb5"/>
</p>
<p>
ICMP, monitored in Wireshark, was a protocol that Ping used from client-1 to connect to the domain controller. Ping -t connected domain controller's private IP address from Client 1 continuously. The connection did not work, so configured the firewall in wf.msc in the domain controller's Windows settings to open the port for Client 1. Logged in to the domain as website.com\username from Client-1 in Windows settings. Checked what VM computer was used by looking at the hostname, the name of the machines. 
</p>
<br />

<p>
<img src="https://github.com/user-attachments/assets/3a82db2e-7232-4776-933f-45ab38246ecb"/>
</p>
<p>
Configured Active Directory in the domain controller. Created organizational units such as "Employees". Checked ipconfig /all to inspect DNS settings for the domain controller and Client-1 in Powershell ISE. Checked the ping ipaddress to show the working connection for the domain controller and Client-1 in Powershell ISE. Created an administrator (Jane) and logged in on Client 1. Created clients from the (labuser) admin account in the domain controller. Edited group policy groups in the active directory. Any users (admin, client) in the domain were able to log in to Client 1 computer. Created a Powershell ISE script to create thousands of clients in the domain controller. Troubleshooted password resets, disabled/enabled accounts, and unlocked accounts in the domain controller's Active Directory group policy. Managed AD security groups and domain admins/users as "labuser" in the domain controller on what these groups can modify, control, read, write, enable and disable. 
</p>
<br />
