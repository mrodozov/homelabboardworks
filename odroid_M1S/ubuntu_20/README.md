## homelabboardworks
Settings and howtos/whattos for my single board computers

## Odroid-M1S - Ubuntu 20 from hardkernel

## Prep

* **Donwloaded**: Get the image from here:

https://dn.odroid.com/RK3566/ODROID-M1S/Ubuntu/ubuntu-20.04-gnome-desktop-odroidm1s-20240326.img.xz

# current version works fine and no more NIC problems.

## Install
# burn the image on sdcard. put it in and power on

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
sudo su -; sudo fallocate -l 8G /swapfile ; chmod 600 /swapfile ; mkswap /swapfile ; swapon /swapfile ; echo "/swapfile swap swap defaults 0 0" >> /etc/fstab ; free -m; exit

# reboot with the sdcard removed, should have only 250MB on the emmc and 1TB nvme with the OS on it
# resize the nvme to full size later, not sure how to do it with fdisk

## Wifi drivers
# this image doesn't have the driver for rtl8188eu, get them from here:
# enable software install from source on ubuntu soft update mgr and install the kernel headers
# Build:
git clone https://github.com/lwfinger/rtl8188eu
sudo apt-get install linux-headers-5.10.0-odroid-arm64 gcc-10
cd rtl8188eu
make all -j 4
sudo make install
reboot

## NPU
# Use this changes for the config.ini then run the docker example. the npu works but the module needs modprobe on reboot
https://wiki.odroid.com/odroid-m1s/application_note/yolov8
sudo modprobe rknpu
sudo reboot


## Saved image on local disks

