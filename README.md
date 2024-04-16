<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>
This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />


<h2>Video Demonstration</h2>


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>

Step 1 Creating a Server-VM.

![image](https://github.com/KitchReeves/Active-Directory/assets/158783649/73c69125-8f1c-4c91-941c-2415574d3a37)

Step 2 Set the Server-VM's private ip to static, as we will be using it as the DNS for our Client-VM

![image](https://github.com/KitchReeves/Active-Directory/assets/158783649/db988e10-54a2-4a4f-b955-5f488568e5ed)


Step 3 Creat the Client-VM and be sure to put it on the same V-net as the Server-VM

![image](https://github.com/KitchReeves/Active-Directory/assets/158783649/f948c404-f7d1-4fca-85ae-82882d172638)


![image](https://github.com/KitchReeves/Active-Directory/assets/158783649/204d8bf3-bbe6-4ded-a0a9-279600799570)

Step 5 Connect to both VMs using Remote Desktop
