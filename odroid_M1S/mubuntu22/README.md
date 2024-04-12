## Odroid-M1S - Ubuntu Mate 22 from tobetter

## Install

* **Donwloaded**: Get the image from here: http://ppa.linuxfactory.or.kr/images/raw/arm64/jammy/ubuntu-22.04-mate-desktop-odroidm1s-20231114.img.xz

* **Saved in**: On disk 240, under folder:

## Overview

Overall works better than the xubuntu from the same image provider but still runs firefox and other
programms not natively but as snaps which is retarded ... or not if they've compiled it only for one arm64

Installing KDE-all bricked the image, so don't
This image is slow too either due to firefox constantly doing something and using 80% of the CPU
or running under snapd or both. apt natively installs firefox as a container so remove it (see the patches)

