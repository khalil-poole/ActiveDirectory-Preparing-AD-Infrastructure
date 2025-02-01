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


Step 2: Create a Virtual Machine
Set the image and size as shown in the screenshots for the VM (Virtual Machine). Create a unique username and password, and check the box for the licensing agreement. This VM will be for our Domain Controller, which manages the network and security. Followed by clicking "Review + Create" for validation and creation of the VM.

![image](https://github.com/user-attachments/assets/004fe066-7532-47b5-bc06-ddc1b0aed050)

