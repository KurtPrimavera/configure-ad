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

- Windows Server 2022: The server operating system deployed on the domain controller, providing essential features for managing network resources, user accounts, and Active Directory services. It offers improved security, scalability, and performance, making it ideal for enterprise environments.
- Windows 10 (21H2): Utilized on the Client-1 computer, this operating system allows users to authenticate with the Active Directory domain and access network resources. Its user-friendly interface and compatibility with a wide range of applications enhance productivity for end-users.
- macOS Sonoma (Host): The host operating system used to manage virtual machines and access the Azure environment. Its robust performance and seamless integration with development tools support effective management of the Active Directory setup.

<h2>High-Level Deployment and Configuration Steps</h2>

1.	Set Up Domain Controller (Server Manager): Installed and configured the Domain Controller using Server Manager, establishing the foundation for Active Directory services within the network.
	2.	Create a Network Environment in Azure Virtual Network Resources: Developed a virtual network in Azure to facilitate communication between the domain controller and client machines, ensuring proper segmentation and security.
	3.	Configure Network Interface Card (NIC): Set up the NIC on the Domain Controller to enable connectivity to the Azure virtual network and facilitate communication with clients.
	4.	Configure DHCP, DNS, and Servers: Implemented DHCP to automate IP address assignment, configured DNS for domain name resolution, and ensured that necessary server roles were established for optimal network performance.
	5.	Deploy Clients to Join the Domain: Provisioned client computers within the network, ensuring they were configured to join the Active Directory domain for centralized management and authentication.
	6.	Monitor ICMP: Utilized Internet Control Message Protocol (ICMP) to test connectivity and monitor the health of network devices, ensuring seamless communication across the infrastructure.
	7.	Implement Command Line Tools: Leveraged command line utilities for various administrative tasks, enhancing troubleshooting capabilities and system management efficiency.
	8.	Configure the Firewall: Set up firewall rules to control inbound and outbound traffic, ensuring network security while allowing necessary communications for domain operations.
	9.	Implement Proper Login for the Domain: Established secure login protocols for users to authenticate with the domain, enhancing security measures for accessing network resources.
	10.	Configure Active Directory: Set up Active Directory services to manage user accounts, security policies, and access to resources within the network.
	11.	Create Organizational Units (OUs): Organized users and resources into OUs within Active Directory for better management and application of group policies.
	12.	Configure Group Policy: Developed and applied Group Policy Objects (GPOs) to enforce security settings and configurations across user accounts and computers within the domain.
	13.	Run PowerShell ISE for Administrative Tasks: Utilized PowerShell Integrated Scripting Environment (ISE) to automate administrative tasks, streamline processes, and improve efficiency.
	14.	Troubleshoot User Problems: Conducted troubleshooting of user-related issues, resolving access problems and ensuring a smooth user experience within the domain.
	15.	Windows Settings: Configured relevant Windows settings on client machines to ensure compatibility with the domain environment and adherence to organizational policies.
	16.	Group Policy Object (GPO): Managed and applied GPOs to enforce specific configurations and security settings across the domain, ensuring compliance and consistency.
	17.	Security Groups: Created and managed security groups within Active Directory to control access to resources and implement permission settings effectively.

<h2>Deployment and Configuration Steps</h2>

<p>
<img src="https://github.com/user-attachments/assets/92f14c35-61f5-41df-a04a-cad3b2e85b0f"/>
</p>
<p>
1.	Create Virtual Machines in Azure: Deployed virtual machines (VMs) in Azure to establish a virtual network infrastructure for various resources.
	2.	Configure Network Interface Card (NIC): Set the NIC to a static configuration, ensuring that specific IP addresses were assigned within Azure for reliable connectivity.
	3.	Establish Domain Controller: Created the domain controller VM and assigned it a static IP address within Azure, enabling consistent access for managing network resources.
	4.	Attempt to Join Domain from Client 1: Used Microsoft Remote Desktop from my host computer (macOS) to configure Client 1 to join the domain through Windows settings; however, this attempt was unsuccessful.
	5.	Configure Client 1 for Domain Joining: Adjusted the settings on Client 1 to connect to the private IP address of the domain controller, utilizing Azure DNS settings to facilitate a successful domain join.
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
