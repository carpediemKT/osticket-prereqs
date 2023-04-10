<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />


<h2>Video Demonstration</h2>

<!-- - ### [YouTube: How To Install osTicket with Prerequisites](https://www.youtube.com) -->

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>List of Prerequisites</h2>

- Create a Resource Group in Azure 
- Create a VM in the resource group
- Item 3
- Item 4
- Item 5

<h2>Creating Resource Group and Virtual Machine in Azure </h2>
<p>
Create Resource Group
</p>

![Screen Shot 2023-03-31 at 8 18 52 PM](https://user-images.githubusercontent.com/88648101/229257003-f0efd402-35f5-48ec-b9ee-be3897a8f7ae.png)
<p>
Create a Resource Group; in this example I named mine RG-osticket.
</p>
<br />

<p>
Create a Virtual Machine Group
</p>

![Screen Shot 2023-03-31 at 8 46 16 PM](https://user-images.githubusercontent.com/88648101/229257681-625e1d59-2c24-4bf1-aba3-9486e11e8e0b.png)

![Screen Shot 2023-03-31 at 8 48 20 PM](https://user-images.githubusercontent.com/88648101/229257690-750ec14e-76f9-4b32-a251-b88d4fa98a72.png)

![Screen Shot 2023-03-31 at 8 51 04 PM](https://user-images.githubusercontent.com/88648101/229257699-45553362-2016-4194-8b35-44912b5919fd.png)


<p>
  Create a virtual machine and select the Resource Group we created earlier. Make sure the region is set to the same region we created our Resource Group and for the VM image choose window 10 Pro, version 21H2. Enter a username and password for the Administrator Account and make sure to rememeber it as we will use it to log into the VM. under the Networking allow Azure to create a virtual network, a subnet, and a public ip. Click on Review + Create to create the virtual machine.
</p>
<br />

<h2>Connecting to Microsoft Remote Desktop on a mac</h2>

<img width="939" alt="Screen Shot 2023-03-31 at 9 17 51 PM" src="https://user-images.githubusercontent.com/88648101/229258754-a442606d-5909-4251-b814-0aedb5d09aa9.png">
<p>
If you are using a macbook like I am in this example, you will have to download the Microsoft Remote Desktop from the app store.
</p>

<img width="913" alt="Screen Shot 2023-03-31 at 9 21 24 PM" src="https://user-images.githubusercontent.com/88648101/229258988-20e9cfaa-8c78-4140-bf6b-257a8e97fbc8.png">

![Screen Shot 2023-03-31 at 9 27 08 PM](https://user-images.githubusercontent.com/88648101/229259227-b559c183-6fb0-4fb2-8ce8-b4ef6809524c.png)
<p> 
After downloading Microsoft Remote Desktop, open the app and enter the Public IP address of the VM we created in the field of PC name. the IP address can be found in Azure by clicking on the virtual machine and looking in the overview. 
</p>

<img width="988" alt="Screen Shot 2023-03-31 at 9 30 14 PM" src="https://user-images.githubusercontent.com/88648101/229259524-4f019586-1755-40ea-94f6-c0a1b098d175.png">
<p> 
Enter the administrator information we provided while creating the VM. a message will appear click continue to log in to the VM.
</p>

<br />
