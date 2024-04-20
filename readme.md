To use WIFI /lib/firmware folder.

WIFI

1. Clone wifi firmware repository
root #git clone --depth=1 https://github.com/RPi-Distro/firmware-nonfree.git

2. Create /mnt/gentoo/lib/firmware/brcm if it doesn't exist
root #mkdir -p /mnt/gentoo/lib/firmware/brcm

3. The wifi mode for raspberry pi 5 is brcmfmc43455, so we only need to copy files for brcmfmc43455.
root # cp firmware-nonfree/debian/config/brcm80211/cypress/cyfmac43455-sdio-standard.bin /lib/firmware/brcm/brcmfmac43455-sdio.bin
root # cp firmware-nonfree/debian/config/brcm80211/cypress/cyfmac43455-sdio.clm_blob /lib/firmware/brcm/brcmfmac43455-sdio.clm_blob
root # cp firmware-nonfree/debian/config/brcm80211/brcm/brcmfmac43455-sdio.txt /lib/firmware/brcm/

4. When raspberry pi 5 boots, it looks for firmware names with model name, like raspberry,5-model-b, so we need to create symlinks for the firmware files, make sure you have following symlinks.
root #ls -l /lib/firmware/brcm/

  -rw-r--r-- 1 root root 643651 Jan 21 12:20 brcmfmac43455-sdio.bin
  -rw-r--r-- 1 root root   2676 Jan 21 12:18 brcmfmac43455-sdio.clm_blob
  lrwxrwxrwx 1 root root     22 Jan 21 12:23 brcmfmac43455-sdio.raspberrypi,5-model-b.bin -> brcmfmac43455-sdio.bin
  lrwxrwxrwx 1 root root     27 Jan 21 12:23 brcmfmac43455-sdio.raspberrypi,5-model-b.clm_blob -> brcmfmac43455-sdio.clm_blob
  lrwxrwxrwx 1 root root     22 Jan 21 12:24 brcmfmac43455-sdio.raspberrypi,5-model-b.txt -> brcmfmac43455-sdio.txt
  -rw-r--r-- 1 root root   2074 Jan 21 12:19 brcmfmac43455-sdio.txt

