firewall<p align="center">
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

Step 18 Login as one of the random new users on the Client-VM

![image](https://github.com/KitchReeves/Active-Directory/assets/158783649/53a9ddd0-d0ed-4b54-bbb4-b62978ee2e25)

![image](https://github.com/KitchReeves/Active-Directory/assets/158783649/a726a5d5-9645-4ea2-a036-f8b0f53d159a)

 Now that the setup is done, I'm going to create Files on the Server-VM for clients to access.

![image](https://github.com/KitchReeves/Active-Directory/assets/158783649/b6eeee87-9121-473e-ac0f-7655fbf9c1e2)

Changing the permissions level

![image](https://github.com/KitchReeves/Active-Directory/assets/158783649/a0f3ad99-2877-427d-892f-dbbd02ceb797)


![image](https://github.com/KitchReeves/Active-Directory/assets/158783649/5401cdaf-907e-417d-8475-68ae2ede1392)

The Client can see and open certain files

![image](https://github.com/KitchReeves/Active-Directory/assets/158783649/a1e47c30-5d81-4b0a-ba41-714b4c3e5fb7)

Trying to Create a new Document with Read only permissions

![image](https://github.com/KitchReeves/Active-Directory/assets/158783649/f60946e4-c2f0-48c2-a232-bba882a56e86)

Creating a doc with Write permissions

![image](https://github.com/KitchReeves/Active-Directory/assets/158783649/2d533bd3-8c51-4753-adc1-f4fc2e81c651)

Creating a New Group to be able to access special files

![image](https://github.com/KitchReeves/Active-Directory/assets/158783649/ee99043b-7f81-4d99-86c4-aa34091477f0)


![image](https://github.com/KitchReeves/Active-Directory/assets/158783649/373a558a-7fd6-499f-a86d-255a98f7d59e)

The Client Can't Access the Folder due to not being apart of the security group

![image](https://github.com/KitchReeves/Active-Directory/assets/158783649/03afed5b-5609-4837-af6d-d65fe270271a)

Adding the Client to the Special access group. Once added, the Client will need to restart to receive the new permissions.

![image](https://github.com/KitchReeves/Active-Directory/assets/158783649/b5fb8c6c-3862-487a-9c24-bbd08f8d4091)

Client accessing the special folder.

![image](https://github.com/KitchReeves/Active-Directory/assets/158783649/df279fac-b6e2-4c60-8c89-e0d60fa8de95)

Showing DNS between the Client and the Domain.

Creating a A-record using the server-vm's private IP.

![image](https://github.com/KitchReeves/Active-Directory/assets/158783649/c5b14e41-9601-44fc-a25d-0de6eb8cadaa)

The Client-VM Pinging the new A-record mainframe

![image](https://github.com/KitchReeves/Active-Directory/assets/158783649/fbbb1109-f152-4fb0-a629-56a7e9fbdada)

Changing mainframe's IP. 

![image](https://github.com/KitchReeves/Active-Directory/assets/158783649/609f1817-30b5-4020-8342-76c850d012fc)

On the client ipconfig /displaydns still shows the old IP.

![image](https://github.com/KitchReeves/Active-Directory/assets/158783649/50e624ca-e638-4f63-a059-9cea235c32e3)

Flushing the DNS and ping mainframe again shows new IP.

![image](https://github.com/KitchReeves/Active-Directory/assets/158783649/5adf9427-b628-4285-bcdb-f57f9d601edb)

Creating a CNAME on the Server-VM.

![image](https://github.com/KitchReeves/Active-Directory/assets/158783649/4d91d8a2-e05a-4a8c-82bd-aec5fe3703ef)

Back on the Client-VM ping search shows one of google's IPs

![image](https://github.com/KitchReeves/Active-Directory/assets/158783649/4ea53e9a-d55e-485f-be4c-be843451e5b8)

![image](https://github.com/KitchReeves/Active-Directory/assets/158783649/b4e403fa-ebe4-42cb-9db9-3b901f518499)










