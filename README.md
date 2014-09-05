Raspberry Pi LTSP Documentation
===============================


![](images/image1.png)


##Warning this documentation is still pre-alpha and is not finished.




Introduction
============

Pi-LTSP is a BASH script for installing setting up and managing an LTSP
(Linux Terminal Server Project) fat client network for Raspberry Pis.

The system is designed to be run on an Ubuntu 14.04 Linux server with at
least 20gb of hard drive space and minimum of 10/100mb Ethernet card.
10/100/1000mb Ethernet card is highly recommended if using any more than
4 clients.

Its main features are

-   Centralised operating system – The operating system for the
    Raspberry Pis is stored centrally on the server. This master image
    is read-only for the Raspberry Pi clients. This means that if the
    administrator wishes to add new software or configuration changes to
    every Raspberry Pi, he just modifies the master image.

-   Network login – There is no user accounts stored locally on the
    Raspberry Pis. They are stored on the Server. This allows a student
    to sit down and log into any Raspberry Pi in the classroom (or even
    the school) and have access to all their files.

-   Network files – As the user accounts are stored on the server, so
    are the student’s files and folder. This means if a teacher needs to
    collect a piece of work off a student, they can just grab it from
    the student’s home folder. It also means backing up is much simpler,
    just back up the entire /home folder on the server onto an external
    drive. This means coursework/controlled assessments can be easily
    and safely backed up in case of an unexpected hardware failure.

<span id="_Toc261449862" class="anchor"><span id="_Toc263869736" class="anchor"></span></span>Required hardware
---------------------------------------------------------------------------------------------------------------

The system requires some specific hardware

-   A server machine. This can be an old desktop machine. It is highly
    recommended it has a 10/100/1000mb Ethernet port and at least 30GB
    of available hard drive space.

-   A network switch. At least 10/100mb switch. For any more than 4-6
    clients, it is highly recommended a 10/100/1000mb switch or you may
    run into major bottlenecks in the network dramatically slowing down
    the clients.

-   Ethernet cabling between the server and switch.

-   Ethernet cabling between the switch and all the clients (Wi-Fi is
    not currently supported)

-   Clients. The clients must be armhf based. The system was
    specifically designed for Raspberry Pi model Bs, revision 2 but may
    work with other armhf based clients.

Ubuntu
------

Linux itself is actually a family of different distributions, all their
own Operating Systems but based on the Linux Kernel. Ubuntu is one of
these distributions. It was specifically designed to be really simple
and easy to use for new users of Linux and is the single most popular
Linux distribution. The current LTS (Long Term Support) version of
Ubuntu is 14.04 (with the previous being 12.04). 14.04 has guaranteed
software and security updates till April 2019.

The codename for 14.04 is Trusty Tahr.

Installation
============

Creating Ubuntu Installation Disk
---------------------------------

### Windows

### Mac

### Ubuntu Linux

Installing Ubuntu 14.04
-----------------------

Please make sure your server machine has no important information left
on it, as we will be ***deleting everything***. You have been warned!
You also need a working (if possible unfiltered) Internet connection.
Wired Ethernet is preferable for installation.

1.  Insert your Ubuntu 14.04 installation disk into the computer you
    intend to use as a server

2.  Shutdown the computer

3.  Hold the “Boot from CD” key or “Boot menu” key. This is commonly F3.
    If in doubt, refer to your computer’s manual.

4.  Ubuntu installer screen should load up as below. Select “Install
    Ubuntu”![](images/image2.png)

5.  Select English and hit continue![](images/image3.png)

6.  Check both the “Download updates while installing” and
    “Install-third party software” and click
    continue.![](images/image4.png)

7.  Select to “Erase disk and install Ubuntu”. This will completely wipe
    your hard drive! No information currently stored on this computer
    will remain. It will all be deleted ![](images/image5.png)

8.  Select your location and time zone. For the UK, select London and
    hit continue ![](images/image6.png)

9.  Select your keyboard. The default is likely correct. If living in
    the UK, select “English (UK)” and select
    continue.![](images/image7.png)

10. Now enter your login details. These will be the administer login
    details on the server. It is recommended you leave the computer name
    at default.![](images/image8.png)

11. Now wait for Ubuntu to install. This normally takes roughly 10-20
    minutes, depending on internet speed and computer processing power.
    ![](images/image9.png)

12. Once it finishes it will ask to reboot. Remove your installation CD
    from the drive and select “Restart now”.
    ![](images/image10.png)

Installing Raspi-LTSP
---------------------

1.  Once the machine reboots, login with your credentials you set up
    earlier. ![](images/image11.png)

2.  Select the search button in the top left corner.
    ![](images/image12.png)

3.  Search for and select “Terminal”. You can also just hit Ctrl + Alt +
    T. ![](images/image13.png)

4.  You will then be presented with a terminal. Raspi-LTSP runs inside a
    terminal window. You may find it useful to resize the terminal
    window to make it larger or put it in full screen.
    ![](images/image14.png)

5.  Enter “wget
    http://raw.github.com/gbaman/RaspberryPi-LTSP/master/Pi\_ltsp”
    (Without quites) and hit enter. ![](images/image15.png)

6.  Once that completes, enter “sudo bash Pi\_ltsp” which will launch
    Raspi-LTSP. You must repeat this command every time you want to
    launch Raspi-LTSP. ![](images/image16.png)

7.  Enter your password as the application must be run as administrator.
    ![](images/image17.png)

8.  Raspi-LTSP will prompt you if you would like to run a full install.
    Select yes. ![](images/image18.png)

9.  The install will take roughly 1-2 hours depending on processor speed
    and internet speed. Select ok and it will start the installation.
    You can now leave it to work. ![](images/image19.png)

10. Around 1-2 hours later, the extra software dialog will be displayed.
    Here you can select any additional software you with to install.
    Libreoffice can be useful for a classroom; it is a free full office
    suit, similar to Microsoft Office. You can also install a custom
    package from the software repositories if you know its full name.
    Once you have finished, select cancel (or finished) to move on.
    ![](images/image20.png)

11. Select yes when asked if you are finished installing software.
    ![](images/image21.png)

12. The operating system will now be compressed. After every change made
    to the operating system, it must be recompressed which takes roughly
    5 minutes normally. Select ok. ![](images/image22.png)

13. If using 2 network interface cards then check the IP address is
    correct. If you are only using 1 (most people), then the default
    will likely be correct. Select yes. ![](images/image23.png)

14. Finally, you must decide if you need students to have Sudo access on
    the Raspberry Pi. If you intend to work with the GPIO pins on the
    Raspberry Pi they will need it. You can really easily later enable
    or disable Sudo use in the Manage-Users submenu in the main software
    options. If in doubt, is recommended to just select yes.
    ![](images/image24.png)

15. Raspi-LTSP installation is now complete. The server has generated an
    SD card image which is located in /home/YourUser/piboot\
    You need to copy these files onto a blank formatted SD card and
    connect the Raspberry Pi to the network.
    ![](images/image25.png)

16. You are recommended to check the Backup section of this manual on
    setting up an automatic backup of your students work to an external
    hard drive in case of hard drive failure.


Copying boot files to SD card on Ubuntu
---------------------------------------

1.  Insert SD card into SD card reader on Ubuntu server. If the computer
    has an internal SD card reader, use it. If not, a USB reader is
    recommended.

2.  Open “Files” near top left. ![](images/image26.png)

3.  Piboot folder with the required boot files is stored in this
    folder.![](images/image27.png)

4.  Open search again and search for “Disks”, Ubuntu’s disk manager.
    ![](images/image28.png)

5.  Select your SD card from the menu at the side. Be very careful to
    pick the correct device here! A good check is check the size, for
    example my SD card in the screenshot is an 8 gigabit SD card.
    ![](images/image29.png)

6.  Select the cog in the top right and select format.
    ![](images/image30.png)

7.  The default options should be correct in the format settings window.
    Select “Format…”. ![](images/image31.png)

8.  Check the device is correct and select format.
    ![](images/image32.png)

9.  Open the piBoot folder and select all the files by dragging while
    holding left mouse button down. ![](images/image33.png)

10. Right click any file in the selection and select “Copy to”.
    ![](images/image34.png)

11. Select the SD card from the side bar. It is usually called BOOT but
    may be named anything. It should be completely empty. Then hit
    select. ![](images/image35.png)

12. Finally hit the eject icon beside the SD card and remove it from the
    computer. Now insert it into a Raspberry Pi, plug the network cable
    in along with keyboard and mouse and plug in the power. The
    Raspberry Pi should then boot successfully.
    ![](images/image36.png)

Additional features
===================

Although Raspi-LTSP is now configured and ready to be used, there are a
number of other features included. These include adding additional
software, managing users (including adding new users), configuring
backups of the system, collecting student’s work and a number of other
items. These are explained in detail in this section

Installing additional programs
------------------------------

Adding additional software is very simple. Be warned though, a number of
developers have taken a lazy approach to software with the Raspberry Pi
and hardcode the user to be Pi. This means this software may not work
with other usernames. If you come across any software with this issue,
try emailing the developer, as most are very happy to fix this issue.

Raspi-LTSP comes with a number of preconfigured options for installing
software or you can select “Install-Custom-package” and enter the name
of the software. This is exactly the same as doing “apt-get install
SoftwareName”.

1.  Select “Install-Program” and hit enter. ![](images/image37.png)

2.  Select the package you wish to install. If it isn’t in the list
    select “Install-Custom-Package” and enter the name of the package.
    ![](images/image38.png)

3.  Once finished, select “Finished” ![](images/image39.png)

4.  When asked if you are finished, select yes.
    ![](images/image40.png)

5.  If any changes were made, it will recompress the operating system to
    prepare it for the Raspberry Pis.

Managing user accounts
----------------------

Although there are a number of graphical tools for managing users, when
adding many users at a time, it is much easier to use the “Add-user”
tool inside Raspi-LTSP. There is also the option to launch a graphical
user management utility with “Launch-graphical”.

To manage user accounts open the Manage-Users submenu.

### Adding new users

1.  From the main menu, select Manage-Users.
    ![](images/image41.png)

2.  Then select add user. ![](images/image42.png)

3.  Next enter the username for the new user. For example, Bob.
    ![](images/image43.png)

4.  Then enter the new users password. Please note this is displayed in
    plain text (as opposed to \*\*\*\*\*) but encrypted when saved.
    ![](images/image44.png)

5.  You will then be prompted if you want to add another user. If you
    are finished, select no. ![](images/image45.png)

### Removing Users

1.  From the main menu, select Manage-Users.
    ![](images/image41.png)

2.  Select Remove-user from the menu. ![](images/image46.png)

3.  Note the full username of the user you want to delete from the list
    displayed and hit enter. ![](images/image47.png)

4.  Enter the username of the user you want to remove. In my case, bob.
    ![](images/image48.png)

5.  Confirm the correct user is displayed and select ok.
    ![](images/image49.png)

6.  You will then be informed the user has been removed along with all
    their files. ![](images/image50.png)

### Change a users password

1.  From the main menu, select Manage-Users.
    ![](images/image41.png)

2.  Select Change-password. ![](images/image51.png)

3.  Note the user you wish to change the password of from the displayed
    list and hit enter. ![](images/image52.png)

4.  Enter the username you wish to change the password of.
    ![](images/image53.png)

5.  Enter the new password you wish to use with the user. For example,
    password and select ok. ![](images/image54.png)

6.  You will then be informed the password change has been successful.
    Select ok. ![](images/image55.png)

7.  If you wish to change more users passwords, select yes, if not
    select no. ![](images/image56.png)

Configuring automatic backups
-----------------------------

Raspi-LTSP includes an automated backup system. This separate piece of
software runs in the background at set times. Overall the system is
still in Alpha currently so it is recommended you also consider running
a full system backup regularly on top of these backups.

Note that these backups only back up the /home folder, aka all the users
files. The operating system is not backed up, nor is the Rasberry Pi
operating system backed up (this can easily be recreated later).

You should not save backups onto the same hard drive as you installed
Ubuntu and Raspi-LTSP onto. Backups should be saved onto an external
hard drive for example.

To configure the backups:

1.  Select backup-Menu. ![](images/image57.png)

2.  Note the warning and select ok. ![](images/image58.png)

3.  Select “Configure-backup” to launch the backup configuration wizard.
    ![](images/image59.png)

4.  Read the information box and select ok. ![](images/image60.png)

5.  Navigate to the folder you wish to save your backups in. External
    drives are mounted to /media/Username so you start in /media. To
    move up one level, select ../. To select this folder, select ./.
    ![](images/image61.png)

6.  Next decide how often you want the backup to run. Twice weekly is a
    good middle ground if you are unsure. ![](images/image62.png)

7.  Next select how long backups should be kept. The old backup checker
    only runs every time a new backup is made, so backups may sit a
    little longer than the chosen time. A good middle ground if you are
    unsure is Thirty days. ![](images/image63.png)

8.  The backup is now configured. It is very important you check
    Display-Logs in the Backup-submenu to check the backup has been
    successfully configured. You should check this regularly as any
    failed backups and their corresponding reasons will be displayed.
    ![](images/image64.png)

9.  To check the log file, select Display-Logs from the Backup-Submenu.
    ![](images/image65.png)

10. The log will be displayed in chronological order. Check the backup
    has been configured and the folder selected is correct. It is
    important to check this every week or 2.
    ![](images/image66.png)

Collecting students work
------------------------

Collecting work from students is simple with Raspi-LTSP. Instead of
printing, they can submit work digitally to you! When Raspi-LTSP is
installed, this is automatically configured and ready to go.

### How to use

Every student has a folder called “handin” in their user files
(/home/UserName/handin).

When they are ready to submit a piece of work, they can copy and paste a
copy of the work into their handin folder.

1.  To collect the work, first select Collect-work from the main menu in
    Raspi-LTSP. ![](images/image67.png)

2.  Verify the username in the box is your own. If you wish to collect
    the work and place it in another users home folder, enter their
    username here instead. Then select ok. ![](images/image68.png)

3.  If the user entered already has a folder in their home folder called
    “submitted”, it will be deleted and replace with the new folder.
    Select yes. ![](images/image69.png)

4.  The students work is now stored in /home/YourUser/submitted/ under
    all the students usernames. You can navigate to this folder and
    check their work. ![](images/image70.png)

Rebuilding the operating system
-------------------------------

Epoptes and Pi-control
----------------------

Advanced options
================

Network technologies
--------------------

Editing the operating system outside of Raspi-LTSP
--------------------------------------------------

Although Raspi-LTSP allows you to perform most actions a standard user
would need to the Raspbian operating system from within Raspi-LTSP, it
is understandable if advanced users may want to directly modify
configuration files or install programs on the Raspbian operating system
manually.

The key things you need to know are

-   The Raspbian operating system is stored at\
    /opt/ltsp/armhf

-   To “chroot” into it (basically allows you to interact with it like a
    normal Raspberry Pi.\
    sudo ltsp-chroot --arch armhf\
    To exit when you are finished, just enter exit

-   The lts.conf file (LTSP armhf configuration file) is stored at\
    /opt/ltsp/armhf/etc/lts.conf

-   To manually compress the operating system for use after a change\
    ltsp-update-image /opt/ltsp/armhf

-   The raw boot files before configuration changes have been made can
    be found at\
    <https://github.com/gbaman/RaspberryPi-LTSP/tree/master/boot>

Understanding the boot folder files
-----------------------------------

The autogenerated boot folder (stored in /home/YourUser/piboot) is made
up of a number of configuration files and boot files.

-   System.map-KERNEL – A debug file for kernel panics.

-   Bootcode.bin – Untouched Raspberry pi bootloader.

-   Cmdline.txt – Default kernel config file, contains NBD server IP
    address, by default this is 1.1.1.1.

-   Cmdline2.txt – cmdline.txt’s twin, only here for maintaining legacy
    setups

-   CmdlineLocalSD – The cmdline.txt file with the kernel settings for a
    standard Raspbian OS.

-   CmdlineNBD.txt – The cmdline.txt file with the kernel settings for
    Raspi-LTSP NBD booting.

-   CmdlineNFS.txt – The cmdline.txt file with the kernel settings for
    Raspi-LTSP NFS booting (legacy).

-   Config-LTSP – The main Raspberry Pi config.txt file for Raspi-LTSP.

-   ConfigLocal.txt – The main Raspberry Pi config.txt for local
    Raspbian booting.

-   Config.txt – The current in use config.txt file, by default boots
    Raspi-LTSP.

-   Config\_standard – The main raspberry Pi config.txt for Raspi-LTSP
    with overclocking disabled.

-   Fixup.dat, fixup\_cd.dat, fixup\_x.dat – Untouched Raspbian boot
    files

-   Initrd.img-KERNEL – The initrd used by Raspi-LTSP. An initrd is a
    mini Linux operating system used to kickstart the main operating
    system. It contains the bootmenu script.

-   Initrd.img-KERNEL-NoMenu – The old initrd used by Raspi-LTSP. It
    does not contain the bootmenu script.

-   Kernel\_emergency.img – An untouched Raspbian recovery kernel.

-   Start.elf, start\_cd.elf, start\_x.elf – Untouched Raspbian boot
    files.

-   Vmlinuz-KERNEL – The main Raspi-LTSP kernel.

Additional files you may have

-   Kernel.img – An untouched Raspbian kernel.

-   Initrd.img – An untouched Raspbian Initrd (very rarely used)

Troubleshooting
===============

“Giving up” errors on boot
--------------------------

“Connection timed out” errors on boot
-------------------------------------
