<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>List of Prerequisites</h2>
- [OS Ticket Installation Files](https://drive.google.com/uc?export=download&id=1b3RBkXTLNGXbibeMuAynkfzdBC1NnqaD)

<h2>Installation Steps</h2>
Download the installation zip folder and extract the files to your desktop

Install/Enable IIS (Internet Information Services) WITH CGI
-Open the Control Panel > Programs > Turn Windows Features on or off
![image](https://github.com/user-attachments/assets/ddb04b99-f4b3-4683-a525-17241cb3f731)

-Scroll down to Internet Information Services and click the box
![image](https://github.com/user-attachments/assets/030f2470-a098-429d-a408-539ddcdec030)

-Open the dropdown for World Wide Web Services > Application Development Features > CGI
![image](https://github.com/user-attachments/assets/3c6b9801-232d-4b96-ba05-ad3a7178fa40)

Install PHP Manager for IIS from the "osTicket-Installation-Files" folder (PHPManagerForIIS_V1.5.0.msi)
-Click Next > "I agree" > Next > Finish

Install the Rewrite Module from the "osTicket-Installation-Files" folder (rewrite_amd64_en-US.msi)
-Agree to the terms > Install > Yes > Finish

Create a "PHP" directory on the C: drive
![image](https://github.com/user-attachments/assets/f46a83ff-0d82-4dad-a32e-30a3c092be86)

Unzip PHP 7.3.8 (php-7.3.8-nts-Win32-VC15-x86.zip) from the "osTicket-Installation-Files" folder into the "C:\PHP" folder
![image](https://github.com/user-attachments/assets/e5deee6e-1995-4e19-9705-e241e51da96c)

Install VC_redist.x86.exe from the "osTicket-Installation-Files" folder
-Agree to the terms > Install > Yes > Close

Install MySQL 5.5.62 (mysql-5.5.62-win32.msi) from the "osTicket-Installation-Files" folder
-Next > Accept the terms > Next > "Typical" > Install > Yes > "Launch the Instance Configuration Wizard" > Finish
-Yes > Next > Next > "Standard Configuration" > Next > Next > Make the password "root" for this demonstration > Next > Execute > Finish

Open IIS as an Admin
![image](https://github.com/user-attachments/assets/2ce3fbda-1d71-4c4f-b182-868f7296bc8f)

Register PHP from within IIS
-Click PHP Manager > Register new PHP version > Navigate to the php-cgi.exe file in C:\PHP
![image](https://github.com/user-attachments/assets/fa8b7ea5-4548-471e-8ef9-d7da472ee6f3)
![image](https://github.com/user-attachments/assets/d0b075b4-d7f5-40b9-b538-01b8d6f46151)
![image](https://github.com/user-attachments/assets/273a34d8-0b2b-417f-9c87-d835069ef6c8)

Reload IIS (Stop and Start the server) MAKE SURE TO CLICK "STOP" AND THEN "START", NOT "RESTART" NOR "REFRESH"
![image](https://github.com/user-attachments/assets/46f0de69-a471-4287-a00d-fa1c39aeb0e2)

Install osTicket v1.15.8
-From the “osTicket-Installation-Files” folder, unzip “osTicket-v1.15.8.zip”; defualt destination is fine
![image](https://github.com/user-attachments/assets/32ad9d77-9cca-4d51-8dfe-ca96a9333409)

-Copy the "upload" folder into “c:\inetpub\wwwroot”
![image](https://github.com/user-attachments/assets/2cb79c51-a11a-4729-8c9a-c204164c1cc8)
![image](https://github.com/user-attachments/assets/f05728ee-c7b7-4cb1-b2aa-d9b6f33543a2)
![image](https://github.com/user-attachments/assets/a2b09b2b-cb1e-4e12-9382-03d0676f59f6)
![image](https://github.com/user-attachments/assets/740f4b23-43f5-4e14-baa5-26025450135f)

-Within "c:\inetpub\wwwroot", Rename "upload" to "osTicket"
![image](https://github.com/user-attachments/assets/7518f8e8-12ac-4246-9bbd-cc6285313735)

Reload IIS once again (Stop and Start the server)

In IIS, go to Sites > Default > osTicket > Click "Browse *:80"
![image](https://github.com/user-attachments/assets/a1f05759-79bd-4a9e-8880-ee0ab66b6cf2)
![image](https://github.com/user-attachments/assets/e3bb8c74-e081-486d-bb19-e6360eee47ea)

Some extensions are disabled; to enable them, in IIS, go to Sites > Default > osTicket and double-click PHP Manager
![image](https://github.com/user-attachments/assets/185090c7-2440-4e9c-93d8-656566e6f012)

-Click "Enable or disable an extension" > right-click and enable the following: php_imap.dll, php_intl.dll, php_opcache.dll
![image](https://github.com/user-attachments/assets/c752d851-b098-47cc-89e2-a69882251c3c)

In C:\inetpub\wwwroot\osTicket\include folder, rename "ost-sampleconfig.php" to "ost-config.php"
*Before*
![image](https://github.com/user-attachments/assets/d521e246-e68c-425c-ae4a-c3e1a69cb699)
*After*
![image](https://github.com/user-attachments/assets/12a9eb90-b9a1-4d4f-88ba-6f8394dc61ce)

Assign Permissions to ost-config.php
-Right-click > Properties > Security > Advanced > Click "Change permissions" if needed > Disable Inheritance > Remove all inherited permissions
![image](https://github.com/user-attachments/assets/ee0e1de3-5f9b-4426-90b3-3d01bd6d590d)
![image](https://github.com/user-attachments/assets/37c6e52b-80c9-44c8-9dd2-0c24637287fc)

-Add > Select a principal > "everyone" ONLY FOR THE PURPOSE OF THIS DEMONSTRATION > click Ok > check Full Control > click Ok > click Apply
![image](https://github.com/user-attachments/assets/3c3741d6-e258-48c1-9915-e44a7e9f9052)
![image](https://github.com/user-attachments/assets/c29e2165-c48e-421b-86a0-31ff72c72010)

Continue osTicket setup in the browser
-set a Helpdesk Name, Default Email (the one that will receive emails from customers), Admin Username and Password
![image](https://github.com/user-attachments/assets/2dab75cd-46bc-4013-97cd-c0328c75bcb6)

BEFORE CLICKING INSTALL NOW: install HeidiSQL from the "osTicket-Installation-Files" folder
-Accept the agreement > Next x4 > Install > "Launch HeidiSQL" > Finish
![image](https://github.com/user-attachments/assets/16206f79-a746-404a-9655-2368d0c19c11)

-Skip > click New > user: root, password: root > Open
![image](https://github.com/user-attachments/assets/df463071-1a0e-4337-ad16-706a487e7c78)

-Create a database called "osTicket" by right-clicking "Unnamed" > Create new > Database
![image](https://github.com/user-attachments/assets/c10dc281-20bb-491c-ba2d-6fcce80c9ccc)
![image](https://github.com/user-attachments/assets/af50c6ff-a48d-4473-9959-27f23af28e04)

Back in the browser, set the following:
MySQL Database: osTicket
MySQL Username: root
MySQL Password: root
Install Now
![image](https://github.com/user-attachments/assets/2325ceaf-5af0-4586-8a94-1c820216e657)
![image](https://github.com/user-attachments/assets/4609402a-4631-425c-a508-29ecc62af447)


osTicket is now installed!
Browse to the help desk login page: http://localhost/osTicket/scp/login.php

End User osTicket URL: http://localhost/osTicket/

































