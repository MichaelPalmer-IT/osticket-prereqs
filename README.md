
<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used</h2>

- Windows 10 (22H2)

<h2>List of Prerequisites</h2>

- Microsoft Azure account
- Basic knowledge of IIS
- Remote Desktop access
- osTicket installation files
- HeidiSQL

<h2>Installation Steps</h2>

<h3>1.) Creating a Virtual Machine</h3>

In Microsoft Azure we will create a VM and add it to a new Resource Group titled "osTicket"

- VM Name: osticket-vm  
- Image: Windows 10 Pro, version 22H2 - x64 Gen2  
- Size: 2 vCPUs, 16 GiB memory  

Navigate to the Virtual Machines page and select "Create". For this instance we will create an Azure Virtual Machine.

![osTicket 1](https://github.com/user-attachments/assets/ad5bb70f-419e-4f9e-b0e2-ba31751b9e2a)


Create a new resource group, name the virtual machine, select the region and the image/operating system.

![osTicket 2](https://github.com/user-attachments/assets/58b4e93e-5ffd-46fb-959b-0f916eba6550)


Select the preferred cpu size, enter adminstrative credentials, check the licensing box and review & create the VM. No changes are needed for management, disks, or networking sections.

![osTicket 3](https://github.com/user-attachments/assets/ba484532-0d86-4564-9e34-7bb338636110)


<h3>2.) Accessing the Virtual Machine</h3>
Retrieve the VM's Public's IP Address and log using "Remote Desktop" with the credentials created during the VM setup. 

![osTicket 4](https://github.com/user-attachments/assets/dcc12590-2fa9-445b-891d-cdde8bfe273b)


<h3>3.) Download and Prepare Installation Files</h3>

- Within the VM, download the osTicket-Installation-Files.zip and unzip it to your desktop. The folder should be named osTicket-Installation-Files.

![osTicket 5](https://github.com/user-attachments/assets/c1adcd0a-bf08-4ae2-8ea5-d4c77179375c)


<h3>4.) Install IIS and Enable Required Features</h3>

Open Control Panel > Programs > Turn Windows features on or off.
Install/enable IIS with the following features:
- World Wide Web Services > Application Development Features > [X] CGI

![osTicket 6](https://github.com/user-attachments/assets/6d509285-1072-4f2c-b762-46eb3771584c)


![osTicket 7](https://github.com/user-attachments/assets/ebdf5fd7-bed1-484f-af09-a3cd05a97a57)


<h3>5.) Install Required Components</h3>

From the osTicket-Installation-Files folder:
- Install PHP Manager for IIS: PHPManagerForIIS_V1.5.0.msi.
- Install Rewrite Module: rewrite_amd64_en-US.msi.
 
![osTicket 8](https://github.com/user-attachments/assets/7a07ce69-e896-4f69-b5b0-7a9053180568)


<h3>6.) Setup PHP</h3>

- Navigate to the C: drive and create the directory C:\PHP.
- Unzip PHP 7.3.8 (php-7.3.8-nts-Win32-VC15-x86.zip) into the C:\PHP folder.
- Install VC_redist.x86.exe.

![osTicket 9](https://github.com/user-attachments/assets/e413a41d-ddc7-4bc2-b2cf-ce733f245220)


![osTicket 10](https://github.com/user-attachments/assets/8f46e2f3-1c22-4794-9660-76510ba5c6d4)


![osTicket 11](https://github.com/user-attachments/assets/ec3345f6-50c7-47ba-8f9a-1eff00ddd285)

<h3>7.) Install MySQL</h3>

- From the osTicket-Installation-Files folder, install MySQL 5.5.62 (mysql-5.5.62-win32.msi).
  - Select Typical Setup.
  - Launch the Configuration Wizard:
    - Standard Configuration
    - Input a username and password

![osTicket 12](https://github.com/user-attachments/assets/33018a5c-b700-4ec4-976c-674973f088f1)

![osTicket 13](https://github.com/user-attachments/assets/8ca2bca2-cad1-4eb9-9f01-cb4b46d348d7)


![osTicket 14](https://github.com/user-attachments/assets/638c0b6a-2a17-4931-927f-7d10adcc337e)


![osTicket 15](https://github.com/user-attachments/assets/758e551e-d214-45ff-b78d-1da0c51ddac5)


<h3>8.) Configure IIS</h3>

- Open IIS as an administrator.
- Register PHP:
  - Go to PHP Manager > Register PHP path > C:\PHP\php-cgi.exe.
- Reload IIS (Stop and Start the server).

![osTicket 16](https://github.com/user-attachments/assets/3db6d454-d372-41b4-b575-f20350a8c3fa)


![osTicket 17](https://github.com/user-attachments/assets/892435fd-7162-4400-92db-b64bfdf0d851)


![osTicket 18 1](https://github.com/user-attachments/assets/c0fa6df3-0235-4b37-948b-1c6f6ec29f93)

![osTicket 18 2](https://github.com/user-attachments/assets/2a91b890-d50b-40e3-b1e4-b3b7232be44a)



<h3>9.) Install osTicket</h3>

- From the osTicket-Installation-Files folder:
  - Unzip osTicket-v1.15.8.zip.
  - Copy the upload folder into C:\inetpub\wwwroot
  - Rename the upload folder to osTicket don't mess up the spelling!
- Reload IIS (Stop and Start the server).

![osTicket 19](https://github.com/user-attachments/assets/3704f0e3-f2dc-431e-9b1c-4b31f075172f)


![osTicket 20 1](https://github.com/user-attachments/assets/6a930ef8-7376-450a-9e6b-a463c5c5fb6d)

![osTicket 20 2](https://github.com/user-attachments/assets/606ec859-9b53-47db-98a2-d6a65cfde6d2)



<h3>10.) Configure osTicket</h3>

- Open IIS:
  - Navigate to Sites > Default > osTicket
  - On the right click Browse :80

![osTicket 21](https://github.com/user-attachments/assets/3196d1ec-8a2b-4714-8f42-b4ce4263f6c0)


![osTicket 22](https://github.com/user-attachments/assets/fc7a2dfd-3b92-4864-9283-1a333c47cdac)


- Note extensions that are not enabled. Go back to IIS:
  - Navigate to Sites > Default > osTicket
  - Double-click PHP Manager > Click Enable or disable an extension
  - Enable the following extensions:
    - php_imap.dll
    - php_intl.dll
    - php_opcache.dll

![osTicket 23](https://github.com/user-attachments/assets/2655076d-cc37-4330-b8e0-9df767f10671)


![osTicket 24 1](https://github.com/user-attachments/assets/5b489249-f600-499b-b0b0-bce07effff91)

![osTicket 24 2](https://github.com/user-attachments/assets/b25a5d47-515f-4fbc-8b6a-cb3574a6c108)



<h3>11.) Update Configuration Files</h3>

- Rename ost-config.php:
  - From: C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php
  - To: C:\inetpub\wwwroot\osTicket\include\ost-config.php
- Assign Permissions:
  - Disable inheritance > Remove all permissions
  - Add new permissions > Everyone > Full control

![osTicket 25](https://github.com/user-attachments/assets/54119576-9ba0-473d-8c9c-52280f3b534f)


![osTicket 26](https://github.com/user-attachments/assets/3586ca7a-023a-4eb7-af83-abb1d8028763)



<h3>12.) Complete osTicket Setup</h3>

- In the browser, continue the osTicket setup:
  - Set Helpdesk Name
  - Set Default email
 
  ![osTicket 27](https://github.com/user-attachments/assets/12c811f8-ba2a-4d63-90a6-5a8b9349fb01)  



<h3>13.) Install HeidiSQL and Configure Database</h3>

- From the osTicket-Installation-Files folder install HeidiSQL
- Open HeidiSQL:
  - Create a new session: Username: root / Password: root
  - Connect to the session
  - Create a database named osTicket
 
![osTicket 28](https://github.com/user-attachments/assets/02549f6c-fd57-4a58-9333-76f98a256387)    

![osTicket 29](https://github.com/user-attachments/assets/f39d57e1-4263-445d-9fd1-15f6fbdbeeae)


![osTicket 30](https://github.com/user-attachments/assets/b1a6c443-cc53-4d2f-9c09-dd7a43b4deab)


![osTicket 31](https://github.com/user-attachments/assets/3a84e12e-611b-47f5-84cf-70c38cc0d3ec)


<h3>14.) Finalize osTicket Installation</h3>

- In the browser complete the setup:
  - MySQL Database: osTicket  
  - MySQL Username: root  
  - MySQL Password: root  
- Click Install Now!

![osTicket 32](https://github.com/user-attachments/assets/c9ac8c86-b1f0-47d5-ad35-3d1bf4744ab5)


<h3>15.) Verify Installation</h3>

- Access your help desk login page: http://localhost/osTicket/scp/login.php

![osTicket 33](https://github.com/user-attachments/assets/ed688412-3ae5-45b3-8ce4-e7655a748450)


<h2>Conclusion</h2>

Congratulations! You have successfully installed and configured osTicket on your virtual machine. Your help desk system is now ready to use!
