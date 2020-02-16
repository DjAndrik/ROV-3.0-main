# StereoPiSettings
This is the guide to settings up raspbian

# First of all 
download raspbian <https://downloads.raspberrypi.org/raspbian_lite_latest>

and balena etcher <https://www.balena.io/etcher/>

If you use non-Lite version of raspberry CM, you must download and install RPIboot <https://www.raspberrypi.org/documentation/hardware/computemodule/cm-emmc-flashing.md>

After flashing your Raspberry CM you'll need to download dt-blob.bin and add it into BOOT partition. This file configures GPIO Raspberry for two cameras
Download from this <http://wiki.stereopi.com/files/dt-blob.bin.zip>
or this <http://stereopi.com/sites/default/files/dt-blob.dts.zip>

# First setting up
Keybord, monitor and... power up! When the system turns on, enter the default user. Login - *pi*, password is *raspbian*

    sudo apt update && sudo apt upgrade
