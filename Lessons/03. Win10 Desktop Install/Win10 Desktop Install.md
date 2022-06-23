## Installation

###  Computer Setup

1. Insert your solid-state drive firmly into the SATA cable coming out of the back of the PC
2. Insert the USB drive into one of the front USB ports

### Starting Windows Setup

1. Press the power button on the PC, then quickly hit F12 to access the boot menu. You may have to hit it several times, but you should see briefly see 'Entering the boot menu' at the top right of the screen’

2. Choose 'USB Storage Device' under 'Legacy Boot' and hit 'Enter'.

3. You should see the Windows Logo as the installer is loading. This may take a few minutes.

### Initial Setup

![image-20220521175905385](.Win10%20Install%20Lab.assets/image-20220521175905385.png)

1.  
    At the initial Windows Setup Screen, keep the default settings of English (US) and hit 'Next'.

2.  Click 'Install Now' on the next screen.

3.  Click the checkbox at the bottom left to accept the License Agreement and click 'Next'.

4.  Choose 'Custom: Install Windows only (advanced)' on the next screen.

5.  Windows 10 doesn't recognize our storage drive, so we need to give it a driver.  Click `Load Driver`, then `Browse` and select the `Win10` drive, then `IT-225-Storage` and click `OK`

6.  Click `Next` to use the `Intel Chipset SATA/PCIe RST Premium Controller`

7.  ![image-20220521175914255](.Win10%20Install%20Lab.assets/image-20220521175914255.png)![image-20220521175919580](.Win10%20Install%20Lab.assets/image-20220521175919580.png)

8.  This brings you to the drive partition screen. If there is only one line that says, 'Unallocated Space' (right pic above), click Next. Otherwise, click each line that doesn't say 'Unallocated Space' and once it's highlighted, click 'Delete'. Do this until there is only one line that says, 'Unallocated Space', then click Next.

9.  Windows will begin the installation process. This will take several minutes but the progress is shown on the screen. If there is no change for over a minute, notify the instructor.

**7.**  Once installation is complete, the installer will automatically reboot the computer.
 **NOTE: It's possible the computer will try to boot from the USB drive again. If you see the Windows Setup initial screen again, turn off the computer, remove the USB drive, and then turn it back on.**

8. As Windows reboots, it will take several minutes to finish installation. You should see a message displayed on screen along with the spinning circles to show activity. If the circles are frozen for more than a few seconds, notify the instructor.

### Setup Finalization

1. Once the installation is finished, Windows will ask a series of customization questions. Answer as follows and click 'Yes' or 'Next' to proceed:
    *Region: **United States**
    Keyboard Layout: **US**
    Second Keyboard Layout: **Skip***

2. When prompted to Sign in with Microsoft, click 'Domain Join Instead' at the bottom left.

3. On the next screen, fill in these details:
    *Who's Going to Use this PC: **UBMS**
    Super Memorable Password: **password
      ** Confirm Password: **password***

4. At the security question screen, it will make you pick 3 security questions. Just pick 3 questions at random and answer them all with '**CNM**'.

5. Answer '**No**' at 'Do more across devices with activity history'

6. At the privacy settings page, click all the blue dials to disable them (you need to scroll down for some dials), then click Accept.

7. Windows will finalize the changes, which will take several minutes, and eventually bring you to the desktop environment.

8. At this point, you have successfully installed Windows 10 OS. Good job, champ.

9. Fix the Timezone on the clock

###    Searching in Windows

The search menu allows you to quickly find anything on the Windows 10 OS. You can access it two ways:

·  Click the magnifying glass button near the bottom left.

 OR


·  Press and hold the Windows key (the key with the Windows Logo) and press the 'S' key.

 ![image-20220521180808025](.Win10%20Install%20Lab.assets/image-20220521180808025.png)

### Device Manager

![image-20220521180825890](.Win10%20Install%20Lab.assets/image-20220521180825890.png)![image-20220521180830268](.Win10%20Install%20Lab.assets/image-20220521180830268.png)

1. Open the search menu and type in 'Device Manager' (shown left)

2. You should see 'Device Manager' show up in the 'Best Match' list. Click it to open Device Manager.

3. Once the Device Manager opens (shown right), look at the hierarchy of devices. At the 'root' of this hierarchy (the top of the list) is the computer name. 

4. Let's fix the Network Card first - open USB drive, run installer from the Win10 drive, IT225-Network folder.

5. Uncheck the `Download Killer Control Center` box and click `Finish`

6. When it prompts what to do while connected to the network, say `No`

7. Click `Yes` to restart

## Driver Setup

NOTE:  Drivers will install in the background, including display drivers, which may mess up monitors.  To fix, you need to goto Display Settings.  Show them how to identify the displays and move them around.

1. Install Chrome/Firefox
2. Google `Dell Support` then click the `Drivers &D ownloads` link
3. Show them how to find service tag on top of PC and put it in and hit `Search`
4. Click `Check for Updates`
5. Click `Download` for Dell SupportAssist
6. Run the SupportAssist installer
7. After the page refreshes, click `Download And Install`
8. Wait for driver installation to finish, then re-check device manager for missing drivers
9. Reboot and wait for any BIOS updates to finish (it will shut off and turn itself back on)
10. Check device manager for any other missing things (there'll be like 4)
11. Go back to Dell Support Site and download `Intel Chipset Device Software` and then install it.  The screen will go crazy for a while, but wait until it prompts to reboot, then reboot.

Install other stuff