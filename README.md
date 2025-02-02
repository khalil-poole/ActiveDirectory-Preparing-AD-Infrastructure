![image](https://github.com/user-attachments/assets/e8da396e-164f-45d2-8c97-7492cf4599a5)


# ActiveDirectory-Preperaring-AD-Infrastructure

In this tutorial, we will be working with Active Directory (AD for short) to simulate user management on a large scale and Microsoft Azure to setup our Virtual Machines.

# Environments and Technologies Used
Microsoft Azure

Virtual Machines

Remote Desktop Connection

Windows Powershell

# Operating Systems Used
Windows Server

Windows 10

# Getting Started

Step 1: Create a Virtual Network
(This tutorial will assume that the reader understands how to setup a Resource Group, and thus the step for that will be skipped)
Setting up a Virtual Network is important to establish a private network, as a fundamental building block for Active Directory. Let's begin by searching for "Virtual Network" in Azure. Then clicking the "Create" button when the VN page is displayed.

![image](https://github.com/user-attachments/assets/d381a280-09a9-455a-bf95-c1836e3be695)

![image](https://github.com/user-attachments/assets/4a79055d-d94e-45f9-ac07-ca0513d57344)

From there, select the Resource Group (RG) that was previously created, followed by a unique name of the VN, and ensure that the region is the same as the RG. Finally, click "Review + Create" for validation, and then click "Create" once the new page is displayed.

![image](https://github.com/user-attachments/assets/d521f28e-8a70-4b1c-9975-0bba26ac771c)


Step 2: Create two Virtual Machines
Select the RG that was created for this tutorial and set the region the same as the RG. Create a unique name for the first VM. This part is important, for image select "Windows Server 2022 Datacenter: Azure Edition x64 Gen2" from the dropdown box. The size should be atleast 2vcpus and 8GiB of memory. Create a username and password for Remote Desktop and check the box for the licensing agreement. This VM will be for our Domain Controller, which manages the network and security. Afterward, we'll click "Next:Disks" and then go "Next: Networking". Followed by clicking "Review + Create" for validation and creation of the VM.

![image](https://github.com/user-attachments/assets/004fe066-7532-47b5-bc06-ddc1b0aed050)

![image](https://github.com/user-attachments/assets/19f3034c-f287-4a2c-901f-cf9de5541ee8)

![image](https://github.com/user-attachments/assets/a9a8a750-1a82-4f86-9687-19aa1245e850)




In the Networking  Tab, ensure that the settings below has the VNet selected that was just created, and that the Subnet is the default option. Afterwards, click "Review + Create" for validation and then click "Create" in the new page.

![image](https://github.com/user-attachments/assets/67455119-9698-4a40-86eb-010de0232088)


After the VM is created for the Domain Controller, we are going to change its Private IP to static, so it will never change. We start by clicking on the VM we created, dc-1. And then go into the Network Settings as shown below.

![image](https://github.com/user-attachments/assets/86b7d25c-e73b-42b1-ac11-f0901e98be5f)

Let's go into the "ipconfig1" settings by clicking on it. Change the Allocation to "Static" and then click "Save".

![image](https://github.com/user-attachments/assets/5bc68313-5e9b-4a61-8be5-585ea3b46de2)

