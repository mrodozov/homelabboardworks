## homelabboardworks
Settings and howtos/whattos for my single board computers

## Odroid-M1S - Ubuntu 20 from hardkernel

## Prep

* **Donwloaded**: Get the image from here:

https://dn.odroid.com/RK3566/ODROID-M1S/Ubuntu/ubuntu-20.04-gnome-desktop-odroidm1s-20240326.img.xz

# current version works fine and no more NIC problems.

## Install
# burn the image on SSD card. put it in and power on

unxz ubuntu-20.04-gnome-desktop-odroidm1s-20240326.img.xz
sudo dd if=ubuntu-20.04-gnome-desktop-odroidm1s-20240326.img of=/dev/mmcblk0 bs=1M status=progress

## Post-install

# Read this: https://forum.odroid.com/viewtopic.php?t=47615 to move the rootfs on the nvme
# use the sdcard as tmp "run from" to burn the builtin emmc and the nvme
# dd the same image once on the builtin emmc, delete the rootfs partition later

sudo dd if=ubuntu-20.04-gnome-desktop-odroidm1s-20240326.img of=/dev/mmcblk0 bs=1M status=progress

# format the nvme and make a partition p1
sudo mkfs.ext4 /dev/nvme0n1
sudo dd	if=/dev/mmcblk0p2 of=/dev/nvme0n1p1 bs=1M status=progress
sudo fdisk /dev/mmcblk0p2 # delete the rootrf partition from the emmc

#Swap space, 8GB is enough
sudo su -; sudo fallocate -l 8G /swapfile ; chmod 600 /swapfile ; mkswap /swapfile ; swapon /swapfile ; free -m; exit

# reboot with the sdcard removed, should have only 250MB on the emmc and 1TB nvme with the OS on it
# resize the nvme to full size later, not sure how to do it with fdisk

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


