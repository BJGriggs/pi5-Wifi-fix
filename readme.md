# WIFI Firmware Fix for Raspberry Pi 5 on Parot OS X 6.0

This repository contains the instructions to fix wifi firmware issues for Raspberry Pi 5. Here are the steps to follow:

## Clone the WIFI Firmware Repository

First, clone the wifi firmware repository:

    git clone https://github.com/BJGriggs/pi5-Wifi-fix.git

## Create the /lib/firmware/brcm directory if it doesn't already exist:

    mkdir -p /lib/firmware/brcm

## The wifi mode for Raspberry Pi 5 is brcmfmc43455, but we can just trasfer all the files or only the BCM4355C0 ones:

    sudo mv -f * /lib/firmware/brcm/
    
# When the Raspberry Pi 5 boots, it looks for firmware names with model names like raspberry,5-model-b. Check the following.

    reboot, check to see if wlan0 is up as whell as check for any brcm errors in dmesg

# Orginal credit
    https://wiki.gentoo.org/wiki/Raspberry_Pi_Install_Guide#Raspberry_Pi_5_WiFi.2FBluetooth_Firmware
