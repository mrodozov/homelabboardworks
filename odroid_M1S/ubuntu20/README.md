## homelabboardworks
Settings and howtos/whattos for my single board computers

## Odroid-M1S - Ubuntu 20 from hardkernel

## Install

* **Built in**: The installater on the bultin eMMC is the oldest image, run 'uname -a' to see the date

* **Donwloaded**: Get the image from here:

https://dn.odroid.com/RK3566/ODROID-M1S/Ubuntu/
This one has the same problem as the builtin, read how to deal with it from here:

https://forum.odroid.com/viewtopic.php?f=212&t=47582

or use this images http://ppa.linuxfactory.or.kr/images/raw/arm64/jammy/
which doesn't need fixing the network from this thread:
https://forum.odroid.com/viewtopic.php?t=47807

The problem is not the network settings on the board but the fucked up LAN settings on the router
and/or the board settings :/

Also the builting ubuntu20 on the soldered eMMC is the *-focal version from https://ppa.linuxfactory.or.kr/images/raw/arm64/focal
which is now empty who knows why and not much different from the jammy.

Just use the jammy