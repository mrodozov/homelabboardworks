## homelabboardworks
Settings and howtos/whattos for my single board computers

## Odroid-M1S - Ubuntu 20 from hardkernel

## Prep

* **Donwloaded**: Get the image from here:

https://dn.odroid.com/RK3566/ODROID-M1S/Ubuntu/ubuntu-20.04-gnome-desktop-odroidm1s-20240326.img.xz

# current version works fine and no more NIC problems.

## Install

unxz ubuntu-20.04-gnome-desktop-odroidm1s-20240326.img.xz
sudo dd if=ubuntu-20.04-gnome-desktop-odroidm1s-20240326.img of=/dev/mmcblk0 bs=4096 status=progress

## Post-install

Use this: https://forum.odroid.com/viewtopic.php?t=47615

dd the image once on the builtin emmc, keeping only the /boot partition on it
burn the image also on the nvme, keeping the OS on it. erase the non-boot partition from the builtin emmc
and mount it as readonly. create the rest of the emmc writable to use it

to do this use sdcard with the image to write over the emmc and the nvme, then remove it and keep only the boot part on the builtin mmc

sudo dd if=/dev/zero of=/dev/mmcblk0p2 bs=4096 status=progress
sudo mkfs.ext4 /dev/mmcblk0p2

Swap space, 8GB is enough # https://gist.github.com/namgivu/1d07ea0484af3e9defd680cd215b34f8
sudo su -; dd if=/dev/zero of=/swapfile bs=1M count=8192 ; chmod 600 /swapfile ; mkswap /swapfile ; swapon /swapfile ; exit

## Wifi drivers
this image doesn't have builtin wifi drivers, get them from here:
https://github.com/aircrack-ng/rtl8188eus/issues/31
https://github.com/kimocoder/realtek_rtwifi
for the small dongle

Build:

Load the drivers:

## NPU

The NPU SDK is not built for this image, make use of it starting here:
https://github.com/rockchip-linux/rknpu2

## Saved image on local disks


