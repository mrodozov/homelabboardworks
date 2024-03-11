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

First remove the https://ppa.linuxfactory.or.kr records in /etc/apt/sources.list and sources.list.d
apt-get update
apt-get install gnome-session gdm3
#install brave
sudo curl -fsSLo /usr/share/keyrings/brave-browser-archive-keyring.gpg https://brave-browser-apt-release.s3.brave.com/brave-browser-archive-keyring.gpg
echo "deb [signed-by=/usr/share/keyrings/brave-browser-archive-keyring.gpg] https://brave-browser-apt-release.s3.brave.com/ stable main"|sudo tee /etc/apt/sources.list.d/brave-browser-release.list
sudo apt update
sudo apt install brave-browser
sudo apt install gnome-terminal

#collect the shell commands from here later for patches, make swapspace and stuff from the x86 machine

* **Move to SSD drive*: leave the link here from odroid forum or shell recipe how to do it

* **Install Brave**: firefox runs as snapd container just don't do it it's using a t of CPU to do nothing
see how to add brave repo on their site

* **Stop report daemon (apport)**: Since there is always something that doesn't work correct apport is using a lot of CPU , just stop it like this:

https://askubuntu.com/questions/93457/how-do-i-enable-or-disable-apport






