## VirtualBox Machine Setup

1. Click `New` near the top middle
   1. Name: `Win2k19AD`
   2. Type: `Microsoft Windows`
   3. Version: `Windows 2019 (64-bit)`
   4. Click Next
2. Continue through and accept defaults for:
   1. Memory Size (Click `Next`)
   2. Hard Disk (Click `Create`)
   3. Hard Disk File Type (Click `Next`)
   4. Storage on physical hard disk (`Click next`)
   5. File Location and Size (Click `Create`)
3. Find the newly created `Wind2k19AD` on the left, right-click it and select `Settings`
4. Select `Network` on the left
   1. Change `Attached to` to `Internal network`
   2. Change `Name` to `jp.net`
5. Select `Storage` on the left
   1. Select the CD-ROM image under `Storage Devices`
   2. Click the CD-ROM image on the far right under the `Attributes` section, and select `Choose a disk file`
   3. Select the `WindowsServer2019-xxxxx.iso` image from your thumb drive
   4. Click `OK` to accept changes and close the settings

## Server Installation

1. With `Win2k19AD` selected on the left, click the green `Start` arrow near the top middle.  
   - The installation CD will kick off automatically and bring you to a Windows Setup screen.
2. Accept the defaults on the initial setup screen and click `Next`
3. Click `Install Now`
4. Select `Windows Server 2019 Standard Evaluation (Desktop Experience)` from the list of choices and click `Next`
5. Select the checkbox for `I accept the license terms` and click `Next`
6. Choose `Custom: Install Windows only` 
7. Select `Next` to accept the defaults on the `Where do you want to install Windows` screen.  The installation will start and reboot itself several times over the next several minutes.
   - NOTE:  **<u>DO NOT</u>** press a key when it prompts you to `Press any key to boot from CD or DVD` or it will restart the setup process.
8. When presented with prompt to set the administrator password, enter the password `Jurassic2022` in both fields, then click `Finish`
9. This will bring you to the login screen.  I know the screen says press CTRL+ALT+Delete, but since this is a VM, we can't use that (the main machine will pick it up), so we use a VM shortcut and press the RIGHT-CTRL+Delete to do the same thing.

### Guest Additions VM Tool Setup

1. Login as the administrator with the password `Jurassic2022`
   - Notice how jerky the mouse is, we can fix that by installing the Guest Additions, which helps the VM behave normally.
2. At the top of the VM window, click `Devices` and then `Insert Guest additions CD image`
3. On the VM, click the `File Explorer` icon (yellow folder) at the bottom and then click `This PC` and then double-click `CD Drive`
4. Double-click the `VBoxWindowsAdditions-amd64` program
5. Click `Next` all the way through this, accepting all the defaults, and then click `Install` and finally `Finish`, accepting the choice to `Reboot Now`
6. After it reboots, log back in as the Administrator and notice how much smoother the mouse interacts with the VM.  
   - You can also resize the window and the VM will adjust the resolution.
7. At the top of the window, click `Devices`, `Drag and Drop`, then `Bidirectional` to enable dragging files to the VM.

### Configure Server Hostname

1. The Server Manager pops up after the machine reboots
2. In the little pop-up box, check `Don't show this message again` and click the `X` to close it.
3. Click on `Configure this local server` in the Server Manager Dashboard
4. Click on the name beside `Computer Name` near the top middle (this name will vary, but will start with `WIN-xxxxx`)
5. In the System Properties window, click `Change`
6. Change the Computer Name to `[ISLANDNAME]-DC` and click `OK`
7. Click `OK` on the restart warning pop-up, then click `Close` on the System Properties.
8. Click `Restart Now` to restart the server
9. Login to the server once it comes back up

### Configure Static IP

1. Right-click the Start menu at the bottom left
2. Click `Network Connections`
3. Click `Change adapter options`
4. Right-click `Ethernet` and click `Properties`
5. Double-click `Internet Protocol Version 4 (TCP/IPv4)`
6. Select the radio button beside `Use the following IP address` and put in the following values
   - IP Address:  `10.226.x.10`
   - Subnet mask:  `255.255.255.0`
   - Default Gateway:  `10.226.x.1`
7. Select the radio button beside `Use the following DNS server addresses` and put in the following value:
   - Preferred DNS server:  `10.226.x.1`
8. Click `OK` to accept the IP settings, then click `OK` again to close the Ethernet Properties window and apply the settings.

## Active Directory 

### Installation

1. Open the Server Manager (if it's not already displayed)
2. Click `Add roles and features` near the middle of the window
3. This will open the Add Roles and Features Wizard
   1. Click `Next` on the initial info screen
   2. On the Select Installation Type page, select Role-based or feature-based installation & click `Next`
   3. On the Server Selection page, select your server from the server pool (should be `YOURISLAND-DC`) and click `Next`
   4. On the Server Roles page, Select `Active Directory Domain Services` and click `Next`
   5. In the pop-up, leave the box checked and click `Add features`, then click `Next`
   6. On the Select Features page, accept the defaults and click `Next`
   7. On the Active Directory Domain Services page, click `Next`
   8. On the Confirm installation selections page, click `Install`
   9. Click `Close` when the installation is complete

### Active Directory Configuration

1. Click the Flag icon near the top right with the yellow exclamation mark beside it.
2. Click `Promote this server to a domain controller`
3. The AD Domain Services Config Wizard appears
   1. Deployment
      1. Select `add a new forest`
      2. Root domain name: `YOURISLAND.jp.lan`
      3. Click `Next`
   2. Domain Controller Options
      1. NOTE: This page may hang for a minute or two as it tries to resolve the domain name
      2. Enter password `JurassicDomainPass!`
      3. Leave other options at their default and click `Next`
   3. DNS Options
      1. Ignore DNS Delegation Error and click `Next`
   4. Additional options
      1. NOTE: This page may hang for a minute as it searches for other workgroups
      2. Use default NetBIOS domain name (should be your Island name)
      3. Click `Next`
   5. Paths
      1. Accept defaults and click `Next`
   6. Review Options
      1. Click `Next`
   7. Pre-requisites Check
      1. You will see a couple of errors but scroll to the end and it should say `All prerequisite checks passed successfully`
      2. Click `Install`
      3. Click `Close` , then the server will restart and apply the changes
4. Once it comes back, log in with `YOURDOMAIN/Administrator` and password `Jurassic2022`
