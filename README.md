<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket: Installation

<h2>Description</h2>
This tutorial outlines the installation of the open-source helpdesk ticketing system osTicket. This will be my first three part series, the installation, post-installation, and configuring and working tickets in osTicket.
<br />


<h2>List of Prerequisites</h2>


<li>Microsoft Azure</li>
<li>Virtual Machine</li>
<li>osTicket Installation Files</li>

<h2>Environments and Technologies</h2>

<ul>
<li>Microsoft Azure (Virtual Machines/Compute)
<li>Remote Desktop
<li>Internet Information Services (IIS)
<li>Windows 10


<h2>Implementation/Program walk-through:</h2>
<p align="center">
1: First, create an Azure Virtual Machine Windows. We can name the resource group osTicket and virtual machine osTicket-vm:  <br/>
<img src="https://i.imgur.com/mmrbwiW.png" height="80%" width="80%" 
<br />
<br />
<br />
Image below shows the image and size we will using. For account you can use make your own account name and password or use ours: account: labuser password osTicketPassword1!:  <br/>
<img src="https://i.imgur.com/9cKG3hK.png" height="80%" width="80%" 
<br />
<br />
Log into Remote Desktop using the public IP address of virtual machine: <br/>
<img src="https://i.imgur.com/fUCRSBa.png" height="80%" width="80%" 
<br />
<br />
Within the VM (osticket-vm), download https://drive.google.com/uc?export=download&id=1b3RBkXTLNGXbibeMuAynkfzdBC1NnqaD and unzip it onto your desktop. The folder should be called “osTicket-Installation-Files” 
- We will use the files in this folder to install osTicket and some of the dependencies:  <br/>
<img src="https://i.imgur.com/yP9Qdp4.png" height="80%" width="80%" 
<br />
<br />
Drag file folder onto virtual machine desktop:  <br/>
<img src="https://i.imgur.com/7xlVnnh.png" height="80%" width="80%" 
<br />
<br />
Enable IIS, Start > Control Panel > Programs (uninstall programs) > On left click turn windows on or off > check Internet Information Services:  <br/>
<img src="https://i.imgur.com/tqXL9A2.png"80%" width="80%" 
<br />
<br />
We will need to download CGI, World Wide Web Services -> Application Development Features -> [X] CGI:  <br/> 
<img src="https://i.imgur.com/tL0NltI.png" width="80%" 
<br />
<br />
From the “osTicket-Installation-Files” folder, install PHP Manager for IIS (PHPManagerForIIS_V1.5.0.msi):  <br/>
<img src="https://i.imgur.com/jRQxOMe.png" width="80%" 
<br />
<br />
From the “osTicket-Installation-Files” folder install the Rewrite Module (rewrite_amd64_en-US.msi):  <br/>
<img src="https://i.imgur.com/negfMHT.png" height="80%" width="80%" 
<br />
<br />
Create the folder/directory C:\PHP in the (c:) drive:  <br/>
<img src="https://i.imgur.com/wMkgkE7.png" height="80%" width="80%" 
<br />
<br />
From the “osTicket-Installation-Files” folder, extract PHP 7.3.8 (php-7.3.8-nts-Win32-VC15-x86.zip) into the “C:\PHP” folder:  <br/>
<img src="https://i.imgur.com/YlIUBX1.png" height="80%" width="80%" 
<br />
<br />
From the “osTicket-Installation-Files” folder, install VC_redist.x86.exe:  <br/>
<img src="https://i.imgur.com/lGoSuIq.png" height="80%" width="80%" 
<br />
<br />
From the “osTicket-Installation-Files” folder, install MySQL 5.5.62 (mysql-5.5.62-win32.msi). We will select these options when upon installing Typical Setup > Standard Configuration > Next > Execute and we can use Username: root Password: root:  <br/>
<img src="https://i.imgur.com/zACAbd7.png" height="80%" width="80%" 
<br />
<br />
Open IIS as an Admin: <br/>
<img src="https://i.imgur.com/Fswkad8.png" height="80%" width="80%" 
<br />
<br />
Register PHP from within IIS (PHP Manager -> C:\PHP\php-cgi.exe):  <br/>
<img src="https://i.imgur.com/KaeqGW8.png" height="80%" width="80%" 
<br />
<br />
Reload IIS (Open IIS, Stop and Start the server) (right side):  <br/>
<img src="https://i.imgur.com/Y93nFoR.png" height="80%" width="80%" 
<br />
<br />
Install osTicket v1.15.8, From the “osTicket-Installation-Files” folder, extract “osTicket-v1.15.8.zip” into the same folder and copy the “upload” folder into “c:\inetpub\wwwroot” Within “c:\inetpub\wwwroot”, Rename “upload” to “osTicket”: <br/>
<img src="https://i.imgur.com/fTjNMdN.png"="80%" width="80%"
<br />
<img src="https://i.imgur.com/y6T4YbG.png" height="80%" width="80%"  
<br />
<br />
Reload IIS (Open IIS, Stop and Start the server) again:  <br/>
<img src="https://i.imgur.com/xIvalO2.png" height="80%" width="80%" 
<br />
<br />
Go to sites > Default > osTicket On the right, click “Browse *:80”:  <br/>
<img src="https://i.imgur.com/Oys5M8U.png" height="80%" width="80%" 
<br />
<br />
By now you should not have an error page, if you do you may have missed a step:  <br/>
<img src="https://i.imgur.com/qfqmHqt.png" height="80%" width="80%" 
<br />
<br />
Note that some extensions are not enabled Go back to IIS, sites > Default > osTicket > Double-click PHP Manager: <br/>
<img src="https://i.imgur.com/3hN5KRe.png" height="80%" width="80%" 
<br />
<br />
Click “Enable or disable an extension: <br/>
<img src="https://i.imgur.com/ecLrvHy.png" height="80%" width="80%" 
<br />
<br />
Find and enable: Enable: php_imap.dll, php_intl.dll, php_opcache.dll: <br/>
<img src="https://i.imgur.com/YKxEitM.png" height="80%" width="80%" 
<br />
<br />
Refresh the osTicket site in your browser, observe the changes (should have less x's):  <br/>
<img src="https://i.imgur.com/Wk2M9A5.png" height="80%" width="80%" 
<br />
<br />
We will be renaming file ost-sampleconfig.php to ost-config.php, go back to the (c:) drive, inetpub >wwwroot > osTicket > include > ost-sampleconfig.php:  <br/>
<img src="https://i.imgur.com/O3SM0ag.png" height="80%" width="80%" <br/>
<br/> 
<img src="https://i.imgur.com/kYInaIx.png" height="80%" width="80%" <br/>
<br /> 
<br /> 
Assign Permissions/Taking permission away ost-config.php, right click into properties > security > advanced > disabled inheritance > remove all:  <br/>
<img src="https://i.imgur.com/fLRGiJT.png" height="80%" width="80%" <br/>
<br />
<img src="https://i.imgur.com/eDZBpoy.png" height="80%" width="80%" <br/>
<br /> 
<br />   
Add New Permissions, add > select a principal > type everyone:  <br/>
<img src="https://i.imgur.com/rB5EvqK.png" height="80%" width="80%" <br/>
<br />
<br />
Continue Setting up osTicket in the browser, click Continue, make up your own name for help desk name *your name help desk* and Default email (random email will work, yourname@gmail.com, personal and work email must  be different) We are going to continue setting up the rest of osTicket: <br/>
<img src="https://i.imgur.com/XJV7SX5.png"="80%" width="80%" <br/>
<br />
 <br/>
<br />
We are not installing yet, we will need to install HeidlSQL from the “osTicket-Installation-Files” folder: Open Heidi SQL Create a new session, root/root Connect to the session,  Create a database called “osTicket” <br/>
<img src="https://i.imgur.com/tVZzrYq.png" height="80%" width="80%" <br/>
<br /> 
<img src="https://i.imgur.com/NuFsPyV.png" height="80%" width="80%"  <br/>
<br />  
<img src="https://i.imgur.com/jKp7jNr.png" height="80%" width="80%"  <br/>
<br />
<img src="https://i.imgur.com/l6v5DZY.png" height="80%" width="80%"  <br/>
<br />
Continue Setting up osTicket in the browser, MySQL Database: osTicket, MySQL Username: root, MySQL Password: root, Click “Install Now!”:  <br/>
<img src="https://i.imgur.com/J0SMm4A.png"80%" width="80%" 
<br />
<br />
Congratulations, hopefully it is installed with no errors! Browse to your help desk login page: http://localhost/osTicket/scp/login.php:  <br/>
<img src="https://i.imgur.com/hZ46UGh.png" height="80%" width="80%" 
<br />
<br />
<b>osTicket is now installed and ready for use! In the next project I will walk you through how to configure agents, their permissions and access, users, https://github.com/AnthonydcHo/post-install-config!
