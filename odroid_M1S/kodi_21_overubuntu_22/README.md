## homelabboardworks
Settings and howtos/whattos for my single board computers

## Odroid-M1S - Kodi 21 from https://ppa.linuxfactory.or.kr/images/raw/arm64/
ubuntu-22.04-kodi-areascout-gbm-odroidm1s-20231201.img

* **General comments**:
This one has the Mali-G52 driver no need to install it on my own.

## Install

* **Donwload**: Get the image from here: http://ppa.linuxfactory.or.kr/images/raw/arm64/jammy/ubuntu-22.04-kodi-areascout-gbm-odroidm1s-20231201.img.xz

Before flashing it, unxz it:

unxz ubuntu-22.04-kodi-areascout-gbm-odroidm1s-20231201.img.xz
burning it in .xz format leads to problems and Balena or Fedora media writer or dd wont stop you to burn it as it is. Then you can see the issues with dmesg (too late)

* **Flash**: flash it on SD card
# clear the SD card first
blkdiscard /dev/sda
# burn it
dd if=ubuntu-22.04-server-odroidm1s-20231114.img of=/dev/sda bs=1M status=progress

* **Move to SSD drive**: leave the link here from odroid forum or shell recipe how to do it

* **SSD location**:







