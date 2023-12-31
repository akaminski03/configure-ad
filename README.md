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

<h2>List of Prerequisites</h2>

- Have an active Microsoft Azure subscription
- Create a Windows 10 Virtual Machine (the user), and a Windows server Virtual Machine (the domain controller) on Azure
- Set the domain controller's NIC private IP address to be static
- Remote desktop connect to both virtual machines that you created


<h2>Deployment and Configuration Steps</h2>

<p>
<img src="https://github.com/akaminski03/configure-ad/assets/65532146/97fdfb3f-dbe7-4858-9cf7-92436ffeba2e" height="80%" width="80%" alt="Pings"/>
</p>
<p>
From the user, perpetually ping the domain controller using ping -t.
</p>
<br />


<p>
<img src="https://github.com/akaminski03/configure-ad/assets/65532146/fc444cf4-026d-48e8-9d3b-e994ef59b4d7" height="80%" width="80%" alt="ICMPv4"/>
</p>
<p>
From the domain controller, open Windows Defender Firewall with Advanced Security, select Inbound Rules, sort by protocol, and enable both "Core Networking Diagnositcs - ICMP Echo Request (ICMPv4-In)" rules.
</p>
<br />

<p>
<img src="https://github.com/akaminski03/configure-ad/assets/65532146/7e21c6a3-0d83-4dd1-aea8-aa34cf38b855" height="80%" width="80%" alt="Pings2"/>
</p>
<p>
The user should now be getting replies from their pings. If not, the virtual machines are likely not on the same network.
</p>
<br />

<p>
<img src="https://github.com/akaminski03/configure-ad/assets/65532146/21c59a0a-f65b-465f-a414-3ec3aad0f2ca" height="80%" width="80%" alt="Domain Services"/>
</p>
<p>
From the Domain Controller, open Server Manager, click Add roles and Features, and enable Active Directory Domain Services.
<br />

<p>
<img src="https://github.com/akaminski03/configure-ad/assets/65532146/6ba836f1-f652-4ea7-979b-09dd842c35a3" height="80%" width="80%" alt="forest"/>
</p>
<p>
From the Domain Controller, open Server Manager, click on the flag in the top right, click on "Promote this server to an active directory," make sure in the first step that you select "Add a new forest," and proceed with installation.
<br />
  
<p>
<img src="https://github.com/akaminski03/configure-ad/assets/65532146/40643d1a-c64c-4229-9812-d067dbe87681" height="80%" width="80%" alt="restart"/>
</p>
<p>
The domain controller will reset. When logging back in, login with the context of the domain.
<br />

<p>
<img src="https://github.com/akaminski03/configure-ad/assets/65532146/7a3c889c-fd59-4ebb-8063-a40fd82f2bc2" height="80%" width="80%" alt="active directory"/>
</p>
<p>
You can now have access to active directory!
<br />



