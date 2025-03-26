<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This project outlines the prerequisites and installation process of the open-source help desk ticketing system osTicket. While focusing on the small details that make the ticketing system run effectively. <br />



<h2>Key Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>List of Prerequisites</h2>

- Create and set up an Azure VM 
- Log into Remote Desktop and unzip osTicket-Installation-Files.zip
- Install/enable IIS and other files within osTicket-Installation-Files.zip
- Install the osTicket file, then enable certain extensions on the ticketing system 
- Assign permissions and finish setting up osTicket

<h2>Installation Steps</h2>


<h4>Create and setup Azure VM:</h4>
<p>
<img src="https://i.imgur.com/55yXxky.jpeg" height="80%" width="80%" alt="Creating VM"/>
<img src="https://i.imgur.com/FwfWYAY.jpeg" height="80%" width="80%" alt="VM completed"/>
<p>
Creating an Azure VM is the first thing to complete in this installation process. Log in to the Azure portal and go to create a virtual machine. Make sure to get all of the details correct in this section. From naming your virtual machine to setting the correct zone, region, number of CPUs, and operating system. We want to use Windows 10 Pro. Also, save your username/password for later use as well. Once you get done with entering the details, check the box at the bottom of the page before continuing. After that, the validation process will occur, and when finished, review and create. Watch the deployment progress happen, it might take a couple of minutes, but when don, go to your VM to look at things such as public/private IP addresses and the settings.  
</p>
<br />

<h4>Log into Remote Desktop and unzip osTicket-Installation-Files.zip:</h4>
<p>
<img src="https://i.imgur.com/7rC4pln.png" height="40%" width="40%" alt="Remote Desktop Log in"/>
</p>
<p>
The next step is where we get into the actual virtual machine. Pull up Remote Desktop by going to your search bar on the desktop. When you get to it, take the public IP address from the VM that was created and copy/paste it into the remote desktop. It should take you to the login screen in Windows as it's loading. Use the same username/password that was saved when creating the virtual machine. Once on the homepage in the virtual machine, we are going to copy the osTicket-Installation-Files.zip into the web browser. Download it next and unzip the file on your desktop. Whenever you unzip this file, you're going to see multiple things that need to be installed so that osTicket can be run properly.  
</p>
<br />

<h4>Install/enable IIS and other files within osTicket-Installation-Files.zip:</h4>
<p>
<img src="https://i.imgur.com/XcJ5zCk.png" height="40%" width="40%" alt="Windows features"/>           <img src="https://i.imgur.com/v3oP5lQ.jpeg" height="40%" width="40%" alt="IIS and CGI"/>
</p>
<p>
In this section, we will be enabling IIS, known as Internet Information Services ahd installing files that we need for osTicket. To get IIS enabled, go to your control panel. Once there, look under program and features, you should see the Windows features turn on or off, press that, and it will take you to a list of features. These features can be turned on or off by simply checking a box. Go to IIS, then select World Wide Web Services. After that, we will go to Application Development Features to be able to enable CGI. Next, we need to install PHP Manager, Rewrite Module while creating a C:\PHP directory. This needs to take place so we can unzip the PHP 7.3.8 (php-7.3.8-nts-Win32-VC15-x86.zip) into the directory. Shortly after, we will install two more files, VC_redist.x86.exe and MySQL 5.5.62 (mysql-5.5.62-win32.msi). To install these files, just right-click them and press Extract All. It is important that when installing MySQL 5.5.62, to select the standard option as well as launch the wizard configuration and make sure your username/password are correct.  
</p>
<br />

<p>
<img src="https://i.imgur.com/mcgu1Ry.jpeg" height="60%" width="60%" alt="Register PHP from within IIS"/>
<img src="https://i.imgur.com/j8uGLa1.jpeg" height="55%" width="55%" alt="Rename “upload” to “osTicket"/>
<img src="https://i.imgur.com/0luOrQg.jpeg" height="60%" width="60%" alt="Getting to osTicket"/>         
</p>
<p>
When registering the PHP Manager, we have to move it to the C:\PHP\php-cgi.exe file so it has a pathway to go to. How you do this is by going to IIS/PHP Manager, then click on it, when it opens up, there will be a line where it says register PHP. Click on that so it can pull up a browser to select which path you want it to go. Select C:\PHP\php-cgi.exe Then press Finish. Now that's finished, let's unzip osTicket-v1.15.8.zip and move the upload folder into the C:\inetpub\wwwroot. We're going to extract the osTicket-v1.15.8.zip file, which will bring up c:\inetpub\wwwroot. Double-click on that and drag the upload file into that folder. Next, you will rename it to osTicket. Make sure to spell exactly how it looks. Head back to IIS so we can open up osTicket to the actual ticketing system. Start by pressing osTicket-vm, after that you will press sites, default web sites, and lastly osTicket. On the right, click “Browse *:80;” this should open up the osTicket ticketing system to the homepage.  
</p>
<br />

<h4>Install osTicket file, then enable certain extensions on the ticketing system:</h4>
<p>
<img src="https://i.imgur.com/5McRDGC.jpeg" height="60%" width="60%" alt="Enabling extensions"/> 
</p>
<p>
For the installation of osTicket, we need to enable a couple of extensions. Go back to IIS, sites, Default, osTicket. We want to double-click click PHP Manager and click enable or disable an extension. The three extensions we are going to enable are  php_imap.dll, php_intl.dll, and php_opcache.dll. Refresh the osTicket site in your browser, and observe the changes. Now we need to rename the  ost-config.php by going to the C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php renaming it to ost-config.php. Right click on ost-config.php, go to properties the advanced. 
<br />

<h4>Assign permissions and finish setting up osTicket:</h4>
<p>
  <img src="https://i.imgur.com/JOrpDl1.png" height="60%" width="60%" alt="continuing help desk"/>
  <img src="https://i.imgur.com/5ktEQ1S.png" height="60%" width="60%" alt="Enabling extensions"/>
</p>
<p>
 Disable inheritance and remove all. After that, we will assign the New permissions to everyone. Continue setting up osTicket in the browser by filling out the helpdesk name as well as setting a default email. Head back to the osTicket-Installation-Files folder and install HeidiSQL. Open Heidi SQL to create a session; the username/password will both be root. You should be able to connect to the session. Once finished, we will create an empty database called osTicket. Continue setting up osTicket by scrolling down the osTicket browser and filling out the MySQL Database by naming it osTicket, MySQL Username/Password with root. The last thing to do is click install, and osTicket should be running with no errors.    
</p>
<br />

