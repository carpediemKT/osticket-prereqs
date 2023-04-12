<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />


<!-- <h2>Video Demonstration</h2> -->

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
- Enable / install IIS in windows
- Download PHP Manager for IIS (PHPManagerForIIS_V1.5.0.msi) from Microsoft
- Rewrite Module (rewrite_amd64_en-US.msi)
- PHP 7.3.8 (php-7.3.8-nts-Win32-VC15-x86.zip)
- Microsoft Visual C++ Redistributable(2015-2022)
- Heidi SQL

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

<h2 align="center"> Installation </h2>
<p>
Installing / Enabling IIS in widows
</p>
<img width="1120" alt="Screen Shot 2023-04-01 at 3 29 10 PM" src="https://user-images.githubusercontent.com/88648101/230892706-81acbca4-43ab-4e0c-8c58-cfb4901a2271.png">

<img width="1729" alt="Screen Shot 2023-04-10 at 7 38 52 AM" src="https://user-images.githubusercontent.com/88648101/230895097-84314540-682f-4a06-bcd5-790a75700da5.png">
<p> 
 In the windows VM, search control panel and clicke on programs. In "Programs and Features" clicke on "Turn Windows Features on or off". A windows features box will appear check internet information services(IIS). Expand IIS by clicking on the plus sign next to it. Expand World Wide Web Services and expand Application Development Features. in Application Development Feautes check CGI. click ok. To check if we did it right, open a web browser and type in the loopback address 127.0.0.1 the default IIS web page should load up as seen in the second image.
</p>
<br />

- Download PHP Manager for IIS (PHPManagerForIIS_V1.5.0.msi) from Microsoft
- Download Rewrite Module (rewrite_amd64_en-US.msi) and create a directory called PHP in the root of the c: drive
- Download PHP Version 7.3.8 and unzip the contents into the PHP Folder we just created.
- Download Microsoft Visual C++ Redistributable(2015-2022)

Download MySQL Server 5.5. in the setup choose typical for type of setup and finish downloading. a new window will pop up asking to configure instance. select the "standard configuration".  click next and leave the check on "Install As Window Service". click next and enter the a password in "New root password". Make sure to rememeber this password as it will be used to log in to your MySQL instance. click next and execute to finish installing. 
<br />
<p>
 Configuration in IIS
</p>
<img width="1331" alt="Screen Shot 2023-04-10 at 10 45 41 AM" src="https://user-images.githubusercontent.com/88648101/230924896-a4343550-ddae-4c50-a28c-8a7cdf1e82c7.png">
<p>
 Click on start type in IIS and run as an administrator. In IIS,you should see the PHP Manager we downloaded earlier. double click it and click on the Register new PHP version. Select the path of the new PHP by browsing to the PHP folder we created and selecting php-cgi. click ok and restart the  server by clicking on the vm and clicking restart under the Manage Server.
</p>
<br />
<h3>Download osTicket</h3>
<p>Download osTicket v1.15.8 from link</p>

<img width="1361" alt="Screen Shot 2023-04-10 at 10 33 35 PM" src="https://user-images.githubusercontent.com/88648101/231044251-55c1602a-9ee0-44f0-8156-9f23301eb334.png">

<img width="1171" alt="Screen Shot 2023-04-10 at 10 37 47 PM" src="https://user-images.githubusercontent.com/88648101/231044376-02adcfc9-663f-4184-b155-e232a7dda58f.png">

<img width="1149" alt="Screen Shot 2023-04-10 at 10 39 55 PM" src="https://user-images.githubusercontent.com/88648101/231044479-2ee04646-f4e7-4e4c-a2fc-ea4ea83da3b8.png">
<p>Open two file explorer tabs. Extract and copy the “upload” folder into c:\inetpub\wwwroot. In the wwwroot, rename the upload folder to "osTicket. Return to the IIS manager.</p>
<br />

<p>Launching osTicket</p>
<img width="1169" alt="Screen Shot 2023-04-10 at 10 51 45 PM" src="https://user-images.githubusercontent.com/88648101/231044584-e591c7c6-11fe-4c18-8354-8fbc9397619a.png">
<img width="1126" alt="Screen Shot 2023-04-10 at 10 53 02 PM" src="https://user-images.githubusercontent.com/88648101/231044666-dceac4d0-b096-4790-a2ef-e8f9495d0e9c.png">
<p>In the IIS manager restart the server by clicking on the server and clicking on restart under Manage Server. Expand "Sites", "Default Web Site". Click on osTicket and click on Browse *:80 (http) under Manage Folder. If everything was set right, you should see osTicket open your web browser.</p>

<img width="1150" alt="Screen Shot 2023-04-10 at 11 19 51 PM" src="https://user-images.githubusercontent.com/88648101/231047705-2c584d25-5d77-4781-9e38-3e42982a6613.png">

<img width="1151" alt="Screen Shot 2023-04-10 at 11 22 10 PM" src="https://user-images.githubusercontent.com/88648101/231048022-47b7a23b-d311-4ca6-bd3d-40ecb98ef561.png">

<p>In IIS, click on osTicket and open PHP Manager. Click on enable or disable an extension, and enable the following:</p>

- Enable php_imap.dll
- Enable php_intl.dll
- Enable php_opcache.dll

<p>Refresh the osTicket web page and observe the changes</p>

<h3>Rename ost-sampleconfig.php to ost-config.php</h3>
<img width="545" alt="Screen Shot 2023-04-10 at 11 40 42 PM" src="https://user-images.githubusercontent.com/88648101/231212531-df270fe6-59cc-454b-81ca-5b9aade65b77.png">
<p>open file exploer and browse to C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php. Change ost-sampleconfig.php to ost-config.php.
</p>
<br />

<h3>Setting Permissions</h3>
** we allow everyone to have access this file becuase it a lab and we will be using random users. 

<img width="560" alt="Screen Shot 2023-04-11 at 11 32 34 AM" src="https://user-images.githubusercontent.com/88648101/231214563-2bbc874d-6b0f-4433-a3d7-ee3d1a463d1e.png">

<img width="840" alt="Screen Shot 2023-04-11 at 11 33 45 AM" src="https://user-images.githubusercontent.com/88648101/231214609-6dddbb47-2a74-4a6b-a43c-c9e94ee7ed0f.png">

<img width="934" alt="Screen Shot 2023-04-11 at 11 36 17 AM" src="https://user-images.githubusercontent.com/88648101/231214856-208ed121-6236-41c7-9d80-be20be4800fa.png">

<img width="978" alt="Screen Shot 2023-04-11 at 11 37 46 AM" src="https://user-images.githubusercontent.com/88648101/231215232-ed793715-4512-4b9d-ba6f-9c422627ed69.png">

<img width="799" alt="Screen Shot 2023-04-11 at 11 38 55 AM" src="https://user-images.githubusercontent.com/88648101/231215637-e989f434-9862-4051-b492-890b0a4c0784.png">
<p>
  Right-click ost-config.php, click properties and go to security. Click Advance and disable inheritance. click on "Remove all inherited permisiions from this object". Click Add and then Select a principel. Type in "everyone" and then check Names in the box "Enter the object name to select", and click ok. check full control to allow everyone permision to the file and click ok. click apply then ok to exit.
</p>

<p>osTicket continuation</p>
<img width="1092" alt="Screen Shot 2023-04-11 at 5 26 17 PM" src="https://user-images.githubusercontent.com/88648101/231433890-7599dbbc-552c-4a23-823d-0094543788c5.png">
<p>Return to the osTicket in the browser and fill out the basic information about your instance. Think of it as you are an administrator in a company and you are signing up for osTicket to be used by your organization. Make sure the information used are documented somewhere as it will be used to sign in to osTicket later.</p>
<br />

<h3>Download Heidi</h3>
<p>Heidi SQL allows us to connect to the SQL server and create a database for osTicket to use.</p>

<img width="633" alt="Screen Shot 2023-04-12 at 7 28 20 AM" src="https://user-images.githubusercontent.com/88648101/231444764-a24d41fc-a766-40a7-9e82-133bd59017a0.png">

<img width="703" alt="Screen Shot 2023-04-12 at 7 30 23 AM" src="https://user-images.githubusercontent.com/88648101/231444788-76d3515b-4405-4440-92a1-4543741bbb72.png">

<img width="957" alt="Screen Shot 2023-04-12 at 7 31 32 AM" src="https://user-images.githubusercontent.com/88648101/231444825-6d983c6d-8801-4104-8dee-6fef206a1ea5.png">
<p>Install Heidi SQL version 12.3.0. After installing click New to create a new connection to the database. The default user name will be root, and enter the password you entered while creating the MySQL server. Click open to connect to the SQL server.</p>

<p>Create a new database in Heidi by right-clicking on Unnamed and hovering on Create New. Name the database osTicket or something you will remember</p>
<img width="953" alt="Screen Shot 2023-04-12 at 7 40 42 AM" src="https://user-images.githubusercontent.com/88648101/231446481-ddd4bc59-b514-474c-a2ca-1ebdd2532f93.png">


<p>osTicket continuation</p>

<img width="964" alt="Screen Shot 2023-04-12 at 7 45 38 AM" src="https://user-images.githubusercontent.com/88648101/231447643-c7420c9f-4ce1-45b2-8462-9a307bb29806.png">

In the osTicket browser, finish setting up "Database Settings" and click install now. In my example I recieved an error stating "conflicts with system email above". This is because I used the same email for the Help Desk setting and administrator settings. If you did the same change one of the email and then proceed to install. you should get a page success page.

<img width="856" alt="Screen Shot 2023-04-12 at 7 52 01 AM" src="https://user-images.githubusercontent.com/88648101/231448753-afca4d7c-becc-4625-95d6-24dcf121f07e.png">
<br />

<h3>Clean Up</h3>

- Delete: C:\inetpub\wwwroot\osTicket\setup
<img width="1011" alt="Screen Shot 2023-04-12 at 7 58 19 AM" src="https://user-images.githubusercontent.com/88648101/231450206-726cac21-071e-4351-abbf-4a0779a04366.png">
<p>Navigate to the setup folder in osTicket and delete it</p>

- Set Permissions to “Read” only: C:\inetpub\wwwroot\osTicket\include\ost-config.php
<img width="996" alt="Screen Shot 2023-04-12 at 8 02 23 AM" src="https://user-images.githubusercontent.com/88648101/231451098-57dfe794-1065-4f2b-8fee-da7d5c20f9a5.png">
<img width="764" alt="Screen Shot 2023-04-12 at 8 03 38 AM" src="https://user-images.githubusercontent.com/88648101/231451693-05a73d20-5637-43a4-b90f-2c801d58a89e.png">
<img width="928" alt="Screen Shot 2023-04-12 at 8 04 25 AM" src="https://user-images.githubusercontent.com/88648101/231451718-e80035bc-da4b-4453-9566-61af634dfdd8.png">






