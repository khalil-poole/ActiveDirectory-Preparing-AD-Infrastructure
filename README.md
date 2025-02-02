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

The last step is to create a second VM, but this time it's similar to how we created them in the previous tutorials. Create a unique name, username, and password while also making sure that the RG selected is the one we created in this tutorial, as well as setting the correct region and image to Windows 10 Pro, with 2 vcpus and 8GiBs. Confirm the licensing, and then let's go to the Networking Tab.

![image](https://github.com/user-attachments/assets/df718a59-9f9f-4e00-9f26-e8c6faa4c503)

![image](https://github.com/user-attachments/assets/eca76468-1d6e-4445-910b-1c6b03f63716)

![image](https://github.com/user-attachments/assets/67620360-2e44-4ac5-b0f7-b20520e31fed)

Check to make sure that the VN selected is the one created during this tutorial, and that the Subnet is the default setting. Once down, click "Review + Create" and then "Create" when the new page is displayed.

![image](https://github.com/user-attachments/assets/ec4c3f82-5ded-48ec-bbdd-cccf093ee440)

Once created, let's set the second VM's DNS settings to the first VM's Private IP Address. This is achieved by going into the DC's settings by clicking on its name, and copy / pasting the private ip address to the client VM. Save after pasting the ip address in the client VM.

![image](https://github.com/user-attachments/assets/3f8e58ef-318a-4978-85c4-95140372723b)

![image](https://github.com/user-attachments/assets/33a04b82-fbf1-467e-bffc-d86df74dd1b3)

Step 3: Firewalls and Pings

Let's go to the Domain Controller VM using Remote Desktop with the login credentials, and turn off Windows Firewall. This is for testing purposes and is not recommended to do in a professional work setting.

Open up "Run" and type "wf.msc" and then enter

![image](https://github.com/user-attachments/assets/e30e1091-7e35-47c9-a81a-5174f00a3b1c)

Next, we go to Properties and turn off the firewall in the following tabs: Domain Profile, Private Profile, and Public Profile. Once configured, click "Apply" and then click "OK".

![image](https://github.com/user-attachments/assets/3261ab98-d563-4820-a7fc-75633ded6fbc)

![image](https://github.com/user-attachments/assets/0a3a2d01-2290-4396-9307-95e69883705b)

Finally for this particular tutorial, we're going to login to the second VM with the Remote Desktop and ping the first VM's private IP Address.

In the search bar, type "Windows Powershell" and click on the first option that appears.

![image](https://github.com/user-attachments/assets/1c9d0adc-1f92-4c62-8d3b-67bb58829fee)

Once Powershell opens up, type "ping <private ip address>" and press enter. If properly setup, the client VM will have successfully pinged the domain VM. Lastly, type in "ipconfig /all" and if everything is properly setup, you can see the DNS that the domain controller is using.
![image](https://github.com/user-attachments/assets/10d81c57-d3d2-40e8-86a9-f3fa6a361514)


With all that said, this concludes part 1 of Active Directory. Remember to stop the VMs in Azure to avoid any unnecessary costs if you're taking a break.

When you're ready, let's proceed to Part 2. 



