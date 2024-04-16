firewall<p align="center">
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

Step 5 Connect to both VMs using Remote Desktop.

Step 6 Change the inbound rules for IVMPv4 on the Server-VM and ping the Server from the Client-vm to verify everything is on the same network.


![image](https://github.com/KitchReeves/Active-Directory/assets/158783649/3666d467-a50f-4051-8b7f-a469478caff7)

Step 7 Install Active Directory on the Server-VM using default settings

![image](https://github.com/KitchReeves/Active-Directory/assets/158783649/59248dfc-c79b-444f-aaeb-dc42f9d1a4c1)

Step 8  Promote server to domain.


![image](https://github.com/KitchReeves/Active-Directory/assets/158783649/8b255418-4986-4b2d-af79-a6832327fda4)


![image](https://github.com/KitchReeves/Active-Directory/assets/158783649/ca537910-c407-4ff3-ac08-db7f0f587348)

Once promoted this will force restart the Server-VM and you'll need to Reconnect with Diffrent information.

Step 9 Reconnect to the Server-VM using new credentials.

![image](https://github.com/KitchReeves/Active-Directory/assets/158783649/8b1e969f-2dcd-48ff-9550-5917b72e0910)

Step 10 Open "Active Directory Users and Computers" and Create two new Organizational Units and name them "_EMPLOYEES" and "_ADMINS"

![image](https://github.com/KitchReeves/Active-Directory/assets/158783649/7a93fbf9-3bab-4b5f-aad9-de9f79137e81)

Step 11 Creating an Admin user

![image](https://github.com/KitchReeves/Active-Directory/assets/158783649/955b4ec7-313b-4dae-8d84-ac86e45ec3ab)

![image](https://github.com/KitchReeves/Active-Directory/assets/158783649/0ab4fcc3-eea1-40bc-8f62-49fca2cf3a36)

Step 12 log back in as the new Admin

![image](https://github.com/KitchReeves/Active-Directory/assets/158783649/657854fa-1945-4fed-8505-f4afce166497)

Step 13 Set Client-VM's DNS to Server-VM's private Ip Address.

![image](https://github.com/KitchReeves/Active-Directory/assets/158783649/93802d07-f364-4892-a242-a4d258909694)

Step 14 Restart the Client-VM and log back in

Step 15 Add Client-VM to the Domain

![image](https://github.com/KitchReeves/Active-Directory/assets/158783649/48e0cbb8-6d3f-4cc9-a86d-3bf31622ea88)

![image](https://github.com/KitchReeves/Active-Directory/assets/158783649/79290139-0704-4f24-864f-86b97a268aa3)

You should be able to see the Client-VM on the Server-VM now.

Step 16 Log back into the Client-VM as a Domain admin to allow remote access.

![image](https://github.com/KitchReeves/Active-Directory/assets/158783649/5ddfca27-d3a5-490f-9a12-8f441eb57ebe)

Step 17 Creating 10,000 Users using Powershell ISE as Admin.

 Use this link https://github.com/joshmadakor1/AD_PS/blob/master/Generate-Names-Create-Users.ps1 
 and copy the code into Powershell and run it.

![image](https://github.com/KitchReeves/Active-Directory/assets/158783649/69ffa3e3-fafd-455c-beab-f15be61293ac)



