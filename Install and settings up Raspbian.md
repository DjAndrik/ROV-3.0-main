# StereoPiSettings
This is the guide to settings up raspbian

# First of all 
Download raspbian lite - [Raspbian images](https://downloads.raspberrypi.org/raspbian_lite_latest)
, and balena etcher - [Balena](https://www.balena.io/etcher/)

If you use non-Lite version of raspberry CM, you must download and install RPIboot -[RPIboot guide](https://www.raspberrypi.org/documentation/hardware/computemodule/cm-emmc-flashing.md)

After flashing your Raspberry CM you'll need to download dt-blob.bin and add it into BOOT partition. This file configures GPIO Raspberry for two cameras.
Download it from this: [First url](http://wiki.stereopi.com/files/dt-blob.bin.zip),
or this: [Second url](http://stereopi.com/sites/default/files/dt-blob.dts.zip)

# First setting up
Keybord, monitor and... power up! When the system turns on, enter the default user. Login is *pi* and password is *raspbian*

Enable ssh-server, just

    sudo raspi-config
Go to interfacing -> ssh -> enable.
After this do this command and remember ip addres

    ip a
or go to /etc/network/interfaces and settings up eth0:

    sudo nano /etc/network/interfaces
Config for me:  

    auto eth0
    iface eth0 inet static
        address 192.168.0.50
        netmask 255.255.255.0
        gateway 192.168.0.1
CTRL+O, enter,CTRL+X

Reboot

    sudo apt update && sudo apt upgrade
