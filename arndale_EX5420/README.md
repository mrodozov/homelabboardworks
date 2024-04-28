## homelabboardworks
Settings and howtos/whattos for my single board computers

## Arndale Exynos 5420 board

## Kernel img from linaro, burned on ssd and working:
https://releases.linaro.org/archive/14.02/ubuntu/boards/arndale-octa/arndale-octa-saucy_server_20140222-611.img.gz

## Install - dd the image on SSD
gunzip arndale-octa-saucy_server_20140222-611.img.gz
dd if=arndale-octa-saucy_server_20140222-611.img of=/dev/sdc bs=4096 status=progress

## there is nothing installed on this not even sshd, it is trying to update from ubuntu sources tho

## Images on local disk: