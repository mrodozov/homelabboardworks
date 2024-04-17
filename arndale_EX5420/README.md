## homelabboardworks
Settings and howtos/whattos for my single board computers

## Arndale Exynos 5420 board

## Kernel build

read this:
https://stackoverflow.com/questions/23969985/cannot-start-the-linux-kernel
checkout single branch as it's a big repo:
git clone https://git.linaro.org/kernel/linux-linaro-tracking -b linux-linaro-tracking --single-branch
# to be checked, write here if the 
make olddefconfig
make ARCH=arm -j4 LOADADDR=0x20008000 uImage
make ARCH=arm -j4 dtbs

## Install
mount /dev/mmcblk0p2 /mnt
cp arch/arm/boot/uImage /mnt/uImage
cp arch/arm/boot/dts/exynos5420-arndale-octa.dtb /mnt/board.dtb



