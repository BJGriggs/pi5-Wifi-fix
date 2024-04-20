# WIFI Firmware Fix for Raspberry Pi 5

This repository contains the instructions to fix wifi firmware issues for Raspberry Pi 5. Here are the steps to follow:

## Clone the WIFI Firmware Repository

First, clone the wifi firmware repository:

    git clone --depth=1 https://github.com/RPi-Distro/firmware-nonfree.git

## Create the /mnt/gentoo/lib/firmware/brcm directory if it doesn't already exist:

    mkdir -p /mnt/gentoo/lib/firmware/brcm

## The wifi mode for Raspberry Pi 5 is brcmfmc43455, so we only need to copy files for brcmfmc43455. Use the following commands to copy the necessary files:

    cp firmware-nonfree/debian/config/brcm80211/cypress/cyfmac43455-sdio-standard.bin /lib/firmware/brcm/brcmfmac43455-sdio.bin
    cp firmware-nonfree/debian/config/brcm80211/cypress/cyfmac43455-sdio.clm_blob /lib/firmware/brcm/brcmfmac43455-sdio.clm_blob
    cp firmware-nonfree/debian/config/brcm80211/brcm/brcmfmac43455-sdio.txt /lib/firmware/brcm/
    
# When the Raspberry Pi 5 boots, it looks for firmware names with model names like raspberry,5-model-b. Hence, we need to create symlinks for the firmware files. Ensure that you have the following symlinks:

    ls -l /lib/firmware/brcm/

# The output should look like this:
    -rw-r--r-- 1 root root 643651 Jan 21 12:20 brcmfmac43455-sdio.bin
    -rw-r--r-- 1 root root   2676 Jan 21 12:18 brcmfmac43455-sdio.clm_blob
    lrwxrwxrwx 1 root root     22 Jan 21 12:23 brcmfmac43455-sdio.raspberrypi,5-model-b.bin -> brcmfmac43455-sdio.bin
    lrwxrwxrwx 1 root root     27 Jan 21 12:23 brcmfmac43455-sdio.raspberrypi,5-model-b.clm_blob -> brcmfmac43455-sdio.clm_blob
    lrwxrwxrwx 1 root root     22 Jan 21 12:24 brcmfmac43455-sdio.raspberrypi,5-model-b.txt -> brcmfmac43455-sdio.txt
    -rw-r--r-- 1 root root   2074 Jan 21 12:19 brcmfmac43455-sdio.txt


# Orginal credit
    https://wiki.gentoo.org/wiki/Raspberry_Pi_Install_Guide#Raspberry_Pi_5_WiFi.2FBluetooth_Firmware
