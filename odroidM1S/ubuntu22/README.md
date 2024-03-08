## homelabboardworks
Settings and howtos/whattos for my single board computers

## Odroid-M1S - Ubuntu 22 from 

## Install

* **Donwload**: Get the image from here: http://ppa.linuxfactory.or.kr/images/raw/arm64/jammy/ubuntu-22.04-server-odroidm1s-20231114.img.xz

Before flashing it, unxz it:

unxz ubuntu-22.04-server-odroidm1s-20231114.img.xz
burning it in .xz format leads to problems and Balena or Fedora media writer or dd wont stop you to burn it as it is. Then you can see the issues with dmesg (too late)

* **Flash**: flash it on SD card

* **Install Gnome**: the xfce and mate are kinda retarded just install gnome. KDE bricks the image don't do it (at least this image)

#collect the shell commands from here later for patches, make swapspace and stuff from the x86 machine

* **Move to SSD drive*: leave the link here from odroid forum or shell recipe how to do it

* **Install Brave**: firefox runs as snapd container just don't do it it's using a lot of CPU to do nothing
see how to add brave repo on their site

* **Stop report daemon (apport)**: Since there is always something that doesn't work correct apport is using a lot of CPU , just stop it like this:

https://askubuntu.com/questions/93457/how-do-i-enable-or-disable-apport






