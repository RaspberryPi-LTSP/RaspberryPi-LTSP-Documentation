[Home](../README.md)    | [Getting started](../installation/getting-started.md)     | [Managing users](../manage-users/README.md) | [Collecting work](../collect-work.md) | [Shared folders](../shared-folders/README.md) | [Backups](../backups/README.md) | [Advanced options](../advanced/README.md) 
| :-----------: |:-------------:| :-----:| :-----:| :-----:| :-----:| :-----:| 


Editing the operating system outside of Raspi-LTSP
--------------------------------------------------

Although Raspi-LTSP allows you to perform most actions a standard user
would need to the Raspbian operating system from within Raspi-LTSP, it
is understandable if advanced users may want to directly modify
configuration files or install programs on the Raspbian operating system
manually.

The key things you need to know are

-   The Raspbian operating system is stored at
    ```/opt/ltsp/armhf```

-   To “chroot” into it (basically allows you to interact with it like a
    normal Raspberry Pi
    ```sudo ltsp-chroot --arch armhf```
    To exit when you are finished, just type exit and hit enter.

-   The lts.conf file (LTSP armhf configuration file) is stored at ```/opt/ltsp/armhf/etc/lts.conf```

-   To manually compress the operating system for use after a change
    ```ltsp-update-image /opt/ltsp/armhf```

-   The raw boot files before configuration changes have been made can
    be found at
    <https://github.com/gbaman/RaspberryPi-LTSP/tree/master/boot>
