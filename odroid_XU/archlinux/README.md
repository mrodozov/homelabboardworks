## Odroid-XU - archlinux kernel 6.11

<details>
<summary>Download</summary>
<br>
Image: http://os.archlinuxarm.org/os/ArchLinuxARM-odroid-xu-latest.tar.gz
<br>
</details>
<details>
<summary>Install</summary>
<br>
read this https://archlinuxarm.org/platforms/armv7/samsung/odroid-xu
and complete the "installation" section
<br>
</details>

<details>
<summary>Fix boot and mounting mmc partitions</summary>
After installation, the boot hangs during booting from the SD card <br>
This is because there are at least two errors in the /boot/boot.ini <br>
Check this two threads: <br>
https://archlinuxarm.org/forum/viewtopic.php?f=47&t=14401
https://archlinuxarm.org/forum/viewtopic.php?f=47&t=15645
1. Comment this line in /boot/boot.ini
#setenv fdt_high "0xffffffff"
2. Change the root=/dev/mmcblk0p2 to root=/dev/mmcblk1p2


</details>

<details>
<summary>Users</summary>
<br>
users: default and root
<br>
pass: user default and root default
</details>

<details>
<summary>Post install</summary>

</details>

<details>
<summary>Image local storage</summary>
960 GB disk, odroid_images/odroid_xu/ArchLinuxARM-odroid-xu-latest.tar.gz
</details>
