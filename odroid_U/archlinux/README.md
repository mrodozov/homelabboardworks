## homelabboardworks
Settings and howtos/whattos for my single board computers

users: default and root
pass: user default and root default

## Odroid-U - archlinux kernel 6.14

* **Donwloaded**: Get the image from here:
http://os.archlinuxarm.org/os/ArchLinuxARM-odroid-latest.tar.gz
# read this https://archlinuxarm.org/platforms/armv7/samsung/odroid-u2

## Install
unzip -e odroid_u3-armv7l-ubuntu20.04minimal-1601403301.zip

## Post install:
# as root
pacman -Sy
pacman -S docker docker-compose

## Image location on disks: 960GB disk
odroid_images/odroid_u/ArchLinuxARM-odroid-latest.tar.gz
