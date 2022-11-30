<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>
This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Setup Resources in Azure
- Ensure Connectivity between the client and Domain Controller
- Install Active Directory
- Create an Admin and Normal User Account in AD
- Join Client-1 to your domain (mydomain.com)
- Setup Remote Desktop for non-administrative users on Client-1


<h2>Deployment and Configuration Steps</h2>

<p>
<img src="https://i.imgur.com/6mueYE6.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
1a- Create the Domain Controller VM (Windows Server 2022) named “DC-1” (username created: labuser) (you can create any username/password // 
1b- Take note of the Resource Group and Virtual Network (Vnet) that get created at this time // 
2- Set Domain Controller’s NIC Private IP address to be static // 
3- Create the Client VM (Windows 10) named “Client-1”. Use the same Resource Group and Vnet that was created in Step 1.a //
4- Ensure that both VMs are in the same Vnet (you can check the topology with Network Watcher)

</p>
<br />

<p>
<img src="https://i.imgur.com/m9mB0Po.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
5- Login to the Domain Controller and enable ICMPv4 in on the local windows Firewall //
6- Login to Client-1 with Remote Desktop and ping DC-1’s private IP address with ping -t <ip address> (If successful ping should result in a reply)
</p>
<br />

<p>
<img src="https://i.imgur.com/Jch4j4G.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
7- Login to DC-1 > Service Manage > Add Roles and Features > install Active Directory Domain Services
8- Promote as a DC: Setup a new forest as mydomain.com (can be anything, just remember what it is)
9- Restart and then log back into DC-1 as user: mydomain.com\labuser
</p>
<br />
