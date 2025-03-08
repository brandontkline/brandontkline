
<b>[PREV]:</b> ( [Home Page](https://github.com/brandontkline/brandontkline/blob/main/README.md) ) <br>
<b>[NEXT]:</b> (Post-Installation Configuration) - (Coming Soon)
<br />
<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
<p>This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket for learning purposes.</p>
<br />


<h2>Operating Systems Used </h2>

- <b>Windows 11</b>

<h2>Prerequisites</h2>

- osTicket Bundle (including PHP, MySQL, and necessary extensions)
- Administrator privileges

<h2>Installation Steps</h2>

### Step 1: Download and Extract osTicket Bundle
1. Download the **osTicket Bundle**.
2. Extract the bundle to a convenient location on your system.
<br />
<br />

### Step 2: Install and Enable IIS with CGI
1. Open the **Start menu** and search for `Control Panel`.
2. Set **View By** to `Category` and click on **Uninstall a Program** under **Programs**.
3. Click on **Turn Windows features on or off**.
4. Scroll down to **Internet Information Services (IIS)** and check the box to enable it.
5. Expand **World Wide Web Services > Application Development Features**.
6. Check **CGI** and click **OK**.

<p>
<img src="https://github.com/brandontkline/brandontkline/blob/main/img/osticket/OsTicketSetupStep1.png" height="80%" width="80%" alt="Screenshot showing Internet Information Services and CGI enabled in Turn Windows features on or off window."/>
</p>
<br />
<br />

### Step 3: Install Required Components

#### Install PHP Manager for IIS
- Run `PHPManagerForIIS_V1.5.0.msi` from the osTicket bundle.

#### Install IIS Rewrite Module
- Run `rewrite_amd64_en-US.msi` from the osTicket bundle.

#### Install Visual C++ Redistributable
- Run `VC_redist.x86.exe` from the osTicket bundle.

#### Configure PHP
- Create a new folder `C:\PHP`.
- Extract `php-7.3.8-nts-Win32-VC15-x86.zip` into `C:\PHP`.
<p>
<img src="https://github.com/brandontkline/brandontkline/blob/main/img/osticket/OsTicketSetupStep3a.png" height="80%" width="80%" alt="Screenshot showing the PHP folder created in the C directory."/>
</p>
<br />
<br />

### Step 4: Install and Configure MySQL
1. Run `MySQL 5.5.62` installer.
2. Select **Typical** setup.
3. Ensure **Launch the MySQL Instance Configuration Wizard** is checked, then click **Finish**.
4. Choose **Standard Configuration**.
5. Set a **root password** and store it securely.
<br />
<br />

### Step 5: Configure IIS for PHP
1. Open IIS as Administrator:
   - Search for `IIS` in the Start Menu.
   - Right-click **Internet Information Services (IIS) Manager** and select **Run as Administrator**.
2. Register PHP:
   - In IIS, double-click **PHP Manager**.
   - Under **PHP Setup**, click **Register new PHP version**.
   - Browse to `C:\PHP` and select `php-cgi.exe`.
   - Click **OK**.
3. Restart IIS:
   - Click **Restart** under **Manage Server** in IIS.
   <br />
   <p><img src="https://github.com/brandontkline/brandontkline/blob/main/img/osticket/OsTicketSetupStep4a.png" height="80%" width="80%" alt="Screenshot showing the right click menu of the Internet Information Services Manager menu entry in the start menu."/></p>
   <p><img src="https://github.com/brandontkline/brandontkline/blob/main/img/osticket/OsTicketSetupStep4b.png" height="80%" width="80%" alt="Screenshot showing PHP Manager highlighted in the Internet Information Services Manager."/></p>
   <p><img src="https://github.com/brandontkline/brandontkline/blob/main/img/osticket/OsTicketSetupStep4c.png" height="80%" width="80%" alt="Screenshot showing where Register new PHP version is at."/></p>
   <p><img src="https://github.com/brandontkline/brandontkline/blob/main/img/osticket/OsTicketSetupStep4d.png" height="80%" width="80%" alt="Screenshot showing php-cgi."/></p>
   <p><img src="https://github.com/brandontkline/brandontkline/blob/main/img/osticket/OsTicketSetupStep4e.png" height="80%" width="80%" alt="Screenshot showing Home button to get back to main area in the IIS Manager"/></p>
   <p><img src="https://github.com/brandontkline/brandontkline/blob/main/img/osticket/OsTicketSetupStep4f.png" height="80%" width="80%" alt="Screenshot showing where to restart IIS."/></p>
   <br />
   <br />

### Step 6: Install osTicket
1. Extract `osTicket-v1.15.8.zip` from the osTicket bundle.
2. Copy the `upload` folder to `C:\inetpub\wwwroot`.
3. Rename `upload` to `osTicket`.
4. Restart IIS.
<p><img src="https://github.com/brandontkline/brandontkline/blob/main/img/osticket/OsTicketSetupStep6.png" height="80%" width="80%" alt="Screenshot showing osTicket folder in the wwwroot folder."/></p>

#### Verify osTicket Installation
1. Open IIS.
2. Navigate to **Sites > Default Web Site > osTicket**.
3. Click **Browse *:80 (http)**.
4. If the osTicket installer page appears, proceed to the next steps. Otherwise, troubleshoot the setup.
<br />
<br />

### Step 7: Enable PHP Extensions
1. Open IIS and navigate to **Sites > Default Web Site > osTicket**.
2. Double-click **PHP Manager**.
3. Click **Enable or disable an extension**.
4. Enable the following extensions:
   - `php_imap.dll`
   - `php_intl.dll`
   - `php_opcache.dll`
<p><img src="https://github.com/brandontkline/brandontkline/blob/main/img/osticket/OsTicketSetupStep7a.png" height="80%" width="80%" alt="Screenshot showing where Enable or disable an extension is."/></p>
<p><img src="https://github.com/brandontkline/brandontkline/blob/main/img/osticket/OsTicketSetupStep7b.png" height="80%" width="80%" alt="Screenshot showing how to enable PHP extension."/></p>
<br />
<br />

### Step 8: Configure osTicket Files
1. Navigate to `C:\inetpub\wwwroot\osTicket\include`.
2. Rename `ost-sampleconfig.php` to `ost-config.php`.
3. Set permissions:
   - Right-click `ost-config.php` > **Properties** > **Security**.
   - Click **Advanced**.
   - Click **Disable inheritance** > **Remove all inherited permissions**.
   - Click **Add** > **Select a Principal**.
   - Enter `Everyone`, check **Full Control**, and apply changes.
<p><img src="https://github.com/brandontkline/brandontkline/blob/main/img/osticket/OsTicketSetupStep9a.png" height="80%" width="80%" alt="Screenshot showing Advanced Security Setting for ost-config with Change permissions highlighted."/></p>
<p><img src="https://github.com/brandontkline/brandontkline/blob/main/img/osticket/OsTicketSetupStep9b.png" height="80%" width="80%" alt="Screenshot showing Advanced Security Setting for ost-config with Disable inheritance highlighted."/></p>
<p><img src="https://github.com/brandontkline/brandontkline/blob/main/img/osticket/OsTicketSetupStep9c.png" height="80%" width="80%" alt="Screenshot showing Advanced Security Setting for ost-config with Add button highlighted."/></p>
<p><img src="https://github.com/brandontkline/brandontkline/blob/main/img/osticket/OsTicketSetupStep9d.png" height="80%" width="80%" alt="Screenshot showing the Permission entry window with Everyone typed in and checked."/></p>
<br />
<br />

### Step 9: Install HeidiSQL and Set Up Database
#### Install HeidiSQL
- Run the installer with default settings.

#### Create osTicket Database
1. Open **HeidiSQL**.
2. Click **New**.
3. Enter the MySQL credentials (username: `root`, password: `your_root_password`).
4. Click **Open**.
5. Right-click `Unnamed` > **Create New > Database**.
6. Name the database `osTicket` and click **OK**.
<p><img src="https://github.com/brandontkline/brandontkline/blob/main/img/osticket/OsTicketSetupStep5a.png" height="80%" width="80%" alt="Screenshot showing HeidiSQL with the New button highlighted."/></p>
<p><img src="https://github.com/brandontkline/brandontkline/blob/main/img/osticket/OsTicketSetupStep5b.png" height="80%" width="80%" alt="Screenshot showing HeidiSQL with create new -> database highlighted."/></p>
<br />
<br />

### Step 10: Complete osTicket Setup
1. Open a browser and go to `http://localhost/osTicket/setup/`.
2. Click **Continue**.
3. Fill out the information you want for Helpdesk name, default email etc in System Settings section.
4. Fill out the information for your initial admin user (Note: admin email and default email cannot be the same).
5. Enter the following database details:
   - **MySQL Database**: `osTicket`
   - **MySQL Username**: `root`
   - **MySQL Password**: `your_root_password`
6. Click **Install**.
<p><img src="https://github.com/brandontkline/brandontkline/blob/main/img/osticket/OsTicketSetupStep10a.png" height="80%" width="80%" alt="Screenshot showing osTicket installer intial page in a web brower."/></p>
<p><img src="https://github.com/brandontkline/brandontkline/blob/main/img/osticket/OsTicketSetupStep10b.png" height="80%" width="80%" alt="Screenshot showing osTicket installer's first half of the Basic Installation page."/></p>
<p><img src="https://github.com/brandontkline/brandontkline/blob/main/img/osticket/OsTicketSetupStep10c.png" height="80%" width="80%" alt="Screenshot showing osTicket installer's second half of the Basic Installation page."/></p>
<p><img src="https://github.com/brandontkline/brandontkline/blob/main/img/osticket/OsTicketSetupStep10d.png" height="80%" width="80%" alt="Screenshot showing osTicket installer's finished page."/></p>
<br />
<br />

<b>[NEXT]:</b> [Post-Installation Configuration] (Coming Soon) <br>
<b>[PREV]:</b> ( [Home Page](https://github.com/brandontkline/brandontkline/blob/main/README.md) )
