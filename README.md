<p align="center">
<img src="https://i.imgur.com/PXfZigP.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />


<h2>Video Demonstration</h2>

[![Step 4: Turn Windows Features on or off](https://img.youtube.com/vi/EbS51IQ6leI/maxresdefault.jpg)](https://youtube.com/clip/UgkxkjSDttxJCalA07AthmPV2JlK1gUzzQea)


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>List of Prerequisites</h2>

- [Installation Files](https://drive.google.com/drive/folders/139sCXwDcbNJisxGkiU7XyU7HfNam8vrZ?usp=sharing)
- Microsoft Azure Account
- Remote Desktop 

<h2>Installation Steps</h2>

<p>

 <img src="https://imgur.com/F6dDyiN.png" height="100%" width="100%" alt="osStep1">
 
</p>
<p>
<h4>1. Create a Resource Group by searching Resource group in the search bar or by selecting the Resource Group Icon (ex. osTicket)</h4>

* Enter name for Resource Group (ex. osTicketRG)

* Select Review + Create

* Select Create once it finishes validating
</p>
<br />

<p>
<img src="https://imgur.com/zZLecVC.png" height="120%" width="120%" alt="Step2"/>
</p>
<p>
<h4>2. Navigate to the Virtual Machine section by searching Virtual Machine in the search bar or by selecting the Virtual Machine Icon</h4>

* Select create and choose Azure Virtual Machine

* In the Resource group field, select the Resource Group you previously created (in my case its osTicketRG)
* Enter a name for the virtual machine in the Virtual Machine Name field (ex. VM-osTicket)
* Select any region 
* Availability options can be set to “No structure redundancy required”
* Select Windows 10 Pro in the Image Field
* Select a machine with at least 4 CPUs (ex. 4vcpus, 16 GiB memory)
* Create a Username and Password for the VM (Don't forget what they are!)
* Leave the Inbound port rules unchanged
* Check the Licensing box
* Select Review + Create
* Select Create once validation is completed and wait for the VM to finish being deployed

</p>
<br />

<p>
<img src="https://imgur.com/ZnwEj5O.png" height="100%" width="100%" alt="Step3VM"/>
</p>
<p>
<h4>3. Select Go to resource or  navigate to Virtual Machines section and select your VM (ex. VM-osTicket)</h4>

* Copy the Public IP address (ex. Mine is 52.170.202.16)

* Open Remote Desktop Connection and paste the Public IP address of you VM

* Select connect, enter the Username and Password you created, and select yes

</p>
<br />

<p>
<img src="https://imgur.com/1HBOtBb.png" height="100%" width="100%" alt="Step4"/>
  
</p>
<p>
<h4>4. When the VM loads in, go to the search bar and type windows features until you see “Turn Windows features on or off” and select it</h4>

* Select Internet Information Services
 
* Click World Wide Web Services
 
* Click Application Development Features
 
* Check the CGI box, select OK and close when changes are finished

</p>
<br />

<p>
<img src="https://imgur.com/6d7uYWz.png" height="100%" width="100%" alt="Step5"/>
 
#### 5. Download the files from the [Installation Files](https://drive.google.com/drive/folders/139sCXwDcbNJisxGkiU7XyU7HfNam8vrZ?usp=sharing)

</p>
<p>

* Install PHP Manager for IIS ([PHPManagerForIIS_V1.5.0.msi](https://drive.google.com/drive/folders/139sCXwDcbNJisxGkiU7XyU7HfNam8vrZ))

* Install Rewrite Module ([rewrite_amd64_en-US.msi](https://drive.google.com/drive/folders/139sCXwDcbNJisxGkiU7XyU7HfNam8vrZ))

* Create a new folder within Windows(C:) drive called PHP

* Extract PHP 7.3.8 ([php-7.3.8-nts-Win32-VC15-x86.zip](https://drive.google.com/drive/folders/139sCXwDcbNJisxGkiU7XyU7HfNam8vrZ)) into the PHP folder created

* Install [VC_redist.x86.exe](https://drive.google.com/drive/folders/139sCXwDcbNJisxGkiU7XyU7HfNam8vrZ)

* Install MySQL 5.5.62 ([mysql-5.5.62-win32.msi](https://drive.google.com/drive/folders/139sCXwDcbNJisxGkiU7XyU7HfNam8vrZ))

* Select Typical Install

* Select Finish with the Launch the MySQL: Instance Configuration Wizard box checked

  * Select Standard Configuration

  *  Leave as Install As Windows Service

  * Create a password for root Username

  * Select Execute 

</p>
<br />

<p>
<img src="https://imgur.com/K2Wz8gG.png" height="100%" width="100%" alt="Step6"/>
</p>
<p>
<h4>6. Navigate to Windows search bar and enter IIS or Internet Information Services, open as administrator</h4> 

 * Select PHP Manager

 * Select Register new PHP version

 * Navigate to the PHP folder created previously and select php-cgi file

 * Select name of server and select Restart under manage server

</p>
<br />

<p>
<img src="https://imgur.com/XuYiOFF.png" height="100%" width="100%" alt="Step7"/>
  
 #### 7. Navigate to Osticket folder that was downloaded from the [Installation files](https://drive.google.com/drive/folders/139sCXwDcbNJisxGkiU7XyU7HfNam8vrZ) 
</p>
<p>

* Move the upload folder to \inetpub\wwwroot

* Rename the upload folder to osTicket within \inetpub\wwwroot

* Stop and start the server in IIS

</p>
<br />

<p>
<img src="https://imgur.com/GlZvaoh.png" height="100%" width="1000%" alt="Step8"/>
</p>
<p>
<h4>8. In IIS select the name of the server</h4>

* Select arrow next to Sites

* Select arrow next to Default Web Site

* Select osTicket

* Select Browse *.80(http), on the right

* Once the webpage for the installer opens successfully, open PHP Manager

* Select Enable or disable an extension
  * Enable php_imap.dll
  * Enable php_intl.dll
  * Enable php_opcache.dll

* Refresh installer webpage to confirm changes

</p>
<br />

<p>
<img src="https://imgur.com/Gej7Y6P.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>
</p>
<p>
<h4>9. Open file explorer</h4>

* Select inetpub folder

  * Select wwwroot folder

  * Select osTicket folder

  * Select include folder

  * Find file called ost-sampleconfig.php

  * Rename it to ost-config.php

* Right click on file and select properties

  * Select security and Advanced

  * Disable Inheritance and Remove all inherited permissions from this object

  * Select Add, Select principal, enter Everyone, and check names

  * Allow full control, select apply, and ok

</p>
<br />

<p>
<img src="https://imgur.com/pXuiz44.png" height="100%" width="100%" alt="Step10"/>
</p>
<p>
<h4>10. Select Continue on the osTicket installer webpage</h4>

 * Enter the name of your helpdesk (can be anything you want)

 * Create an email that will be receiving emails from customers

</p>
<br />

<p>
<img src="https://imgur.com/QSgcgcS.png" height="100%" width="100%" alt="Step11"/>
 
 #### 11. Download and install [HeidiSQL](https://drive.google.com/drive/folders/139sCXwDcbNJisxGkiU7XyU7HfNam8vrZ)
</p>
<p>
* Select create a new session

* Name the database osTicket
 
* Create a password for root username

</p>
<br />

<p>
<img src="https://imgur.com/uegnmiV.png" height="100%" width="100%" alt="Step12"/>
</p>
<p>
<h4>12. Continue setup process from the osTicket installer webpage</h4>

* Enter the Admin user details of your choosing (just don't forget your credentials)

* In Database settings enter the following
  
  * MySQL Database: osTicket
  
  * MySQL Username: root
  
  * MySQL Password:(the password you created in step 11)

* Select Install Now

</p>
<br />

<p>
<img src="https://imgur.com/a2xq1d6.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>
</p>
<p>
<h4>13. The page should now say congratulations</h4>

* Tickets can be submitted at http://localhost/osTicket/ 

* Agent/admin login at http://localhost/osTicket/scp/login.php
</p>
<br />

<p>
<img src="https://imgur.com/pdnAMhx.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>
</p>
<p>
<h4>14.Open File Explorer</h4>

* Select inetpub folder
 
 * Select wwwroot folder
 
 * Select osTicket folder
 
 * Delete the setup folder

* Select include folder

* Find ost-config.php and open properties

* Change permissions to read only

</p>
<br />
