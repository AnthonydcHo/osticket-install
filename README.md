<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source helpdesk ticketing system osTicket.<br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>List of Prerequisites</h2>

<ul>
<li>Microsoft Azure</li>
<li>Virtual Machine</li>
<li>osTicket Installation Files</li>
</ul>

<h2>Installation Steps</h2>

<p>
<h3>Step 1: Connect to Your Virtual Machine with Remote Desktop</h3>



<h3>Step 2: Within the VM (osticket-vm), download the osTicket-Installation-Files.zip [this is a file] and unzip it onto your desktop. The folder should be called “osTicket-Installation-Files” </h3>

- Go to downloads folder
- Move file onto desktop 
- Right click Extract all, select extract 



![image](https://github.com/user-attachments/assets/b125669c-6fc1-4a58-a914-ed0a517ed948)



<h3>Step 3: Install / Enable IIS in Windows WITH CGI </h3>
 
- World Wide Web Services -> Application Development Features -> [X] CGI      
- From the “osTicket-Installation-Files” folder FROM DOWNLOAD, install PHP Manager for IIS (PHPManagerForIIS_V1.5.0.msi)
- From the “osTicket-Installation-Files” folder install the Rewrite Module (rewrite_amd64_en-US.msi)
- Create the directory C:\PHP
  - file explorer - windows c (c drive) - make new folder php
- From the “osTicket-Installation-Files” folder, unzip PHP 7.3.8 (php-7.3.8-nts-Win32-VC15-x86.zip) into the “C:\PHP” folder
	-unzip-go into osticket folder - php - extract all - browse to php folder - select 
- From the “osTicket-Installation-Files” folder, install VC_redist.x86.exe.
- From the “osTicket-Installation-Files” folder, install MySQL 5.5.62 (mysql-5.5.62-win32.msi)

   -  Typical Setup 
   -  Launch Configuration Wizard (after install) 
   -  Username: root
   -  Password: root

- Open IIS as an Admin
- Register PHP from within IIS (PHP Manager -> C:\PHP\php-cgi.exe)




<h3>Step 4: Install osTicket v1.15.8</h3>
     
- From the “osTicket-Installation-Files” folder, unzip[extract] “osTicket-v1.15.8.zip” and copy the “upload” folder into “c:\inetpub\wwwroot”
- Within “c:\inetpub\wwwroot”, Rename “upload” to “osTicket”


    

<h3>Step 5: Restart the IIS Server
</h3>

- Search for Internet Information Services (IIS) and select Open
	- Select Restart on the right-hand side 
- On the left side of the screen, select Virtualmachine > Sites > Default Website > osTicket
- On the right side of the screen, click “Browse *:80”
	- This should open osTicket in your web browser
- Before continuing, head back to IIS
- Open IIS


<p align="center">
<img src="https://i.imgur.com/OpBkwwj.png" height="80%" width="80%" alt="Azure Free Account"/> <img src="https://i.imgur.com/XNVSNia.png" height="80%" width="80%" alt="Azure Free Services"/>
</p>

<h3>Step 6: Enable Extensions in IIS
</h3>

- Go back to IIS > Sites > Default Web Site > osTicket
- Double-click PHP Manager
- Click “Enable or Disable an Extension” at the bottom of the screen under PHP Extensions
- Right-click and enable the following
    - php_imap.dll (Might be already enabled)
    - php_intl.dll
    - php_opcache.dll

 
     
 <p align="center">
<img src="https://i.imgur.com/GQfPOU8.png" height="80%" width="80%" alt="Azure Free Account"/> <img src="https://i.imgur.com/iCK6vst.png" height="80%" width="80%" alt="Azure Free Services"/>
</p>

<h3>Step 7: Refresh the osTicket Site in Your Browser
</h3>

- Refresh the osTicket site adn observe the change
	- Intl Extension should now have a green checkmark next to it


<p align="center">
<img src="https://i.imgur.com/ByfN2Fd.png" height="80%" width="80%" alt="Azure Free Account"/>



<h3>Step 8: Rename</h3>
 
- Open Windows Explorer and select C: > inetpub > wwwroot > osTicket > include
	- Rename the following file:
		- From: ost-SAMPLEconfig.php
		- To: ost-config.php


<p align="center">
<img src="https://i.imgur.com/DDTR8CD.png" height="80%" width="80%" alt="Azure Free Account"/>

<h3>Step 9: Assign Permissions to ost-config.php</h3>

- Right-click ost-config.php 
- Open Properties > Security > Advanced > Permissions 
- Select Disable Inheritance > Remove all inherited permissions from this object 

<p align="center">
<img src="https://i.imgur.com/pcFvK9d.png" height="80%" width="80%" alt="Azure Free Account"/>

- Afterwards, select Add > select Principal > type in "everyone" > select Check Names > select OK
	- Allow everyone full control (check all boxes) > Select apply > OK

<p align="center">
<img src="https://i.imgur.com/vUlpzTb.png" height="70%" width=70%" alt="Azure Free Account"/> <img src="https://i.imgur.com/WZrk1F7.png" height="80%" width="80%" alt="Azure Free Services"/>
</p>

  
<h3>Step 10: Continue Setting Up osTicket in Browser</h3>

- Go back to the browser and click Continue
  - Name: Helpdesk
  - Email: whichever email you want
  - First Name: your first name
  - Last Name: your last name
  - Email Address: whichever email you want (needs to be different from the Helpdesk's default email)
  - Username: user_admin 
  - Password: Password1 
  
<p align="center">
<img src="https://i.imgur.com/1GfpPLs.png" height="80%" width="80%" alt="Azure Free Account"/>

<h3>Step 11: Download and Install HeidiSQL</h3>

- Head to osTicket Installation Files [link](https://drive.google.com/drive/u/0/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6)
	- Download and install HeidiSQL
- Open HeidiSQL > Select "New" at the bottom-left corner of the screen
   - User: root
   - Password: Password
- Select Open
- On the left side, right-click Unnamed > select Create New > Database
- Name it “osTicket” and select OK

 <p align="center">
<img src="https://i.imgur.com/mDBWQ5k.png" height="70%" width="70%" alt="Azure Free Account"/> <img src="https://i.imgur.com/ADJYQyB.png" height="70%" width="70%" alt="Azure Free Services"/>
</p>

<h3>Step 12: Continue Setting Up osTicket by Filling Out the Fields</h3>

- Go back to the browser
	- MySQL Database: osTicket (the one you just created in HeidiSQL)
	- MySQL Username: root
	- MySQL Password: Password1
	- Finally, click Install Now

<p align="center">
<img src="https://i.imgur.com/Npqj9Us.png" height="80%" width="80%" alt="Azure Free Account"/>



<p align="center">
<img src="https://i.imgur.com/F52ypHn.png" height="80%" width="80%" alt="Azure Free Account"/>

<h3>Tips!</h3>

- To create tickets as a user: http://localhost/osTicket/
- To log in as an Admin or helpdesk professional: http://localhost/osTicket/scp

<h3>Step 13: Post-Intallation Cleanup</h3>

- Go to C: > inetpub > wwwroot > osTicket > Setup
    - Delete the contents in the Setup folder
    - Afterwards, delete the Setup folder
- Go to C: > Inetpub > wwwroot > osTicket > Include
    - Right-click on ost-config.php 
    - Select Securities > Advanced > Click on "everyone" > edit to change permissions
	- Allow everyone to only have "Read and execute" permission, then select OK > Apply > OK
	
 <p align="center">
<img src="https://i.imgur.com/wucT3UN.png" height="70%" width="70%" alt="Azure Free Account"/> <img src="https://i.imgur.com/cPSx6VL.png" height="70%" width="70%" alt="Azure Free Services"/>
</p>	

