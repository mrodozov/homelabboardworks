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
https://archlinuxarm.org/forum/viewtopic.php?f=47&t=14401 <br>
https://archlinuxarm.org/forum/viewtopic.php?f=47&t=15645 <br>
1. Comment this line in /boot/boot.ini <br>
#setenv fdt_high "0xffffffff" <br>
2. Use the UUIDs of the two partitions in /etc/fstab <br>
```
# Static information about the filesystems.
# See fstab(5) for details.

# <file system> <dir> <type> <options> <dump> <pass>
UUID=2577-D534					/boot   vfat    defaults        0       0
UUID=23fae9aa-a78e-4201-8330-6c23890cc910	/	ext4    defaults        0       0
```
instead of assuming the mmc numbering

</details>

<details>
<summary>Move to SSD and use the SD card for boot and keeping the kernel</summary>

<br>
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
Once the boot and partition mounts are fixed install gnome:
```
pacman-key --init
pacman-key --populate archlinuxarm
pacman -Syu
pacman -S xorg, gnome
systemctl enable gdm.service
systemctl start gdm.service
```
</details>

<details>
<summary>Image local storage</summary>
960 GB disk, odroid_images/odroid_xu/ArchLinuxARM-odroid-xu-latest.tar.gz
</details>
