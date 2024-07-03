## Odroid-U - archlinux kernel 6.7

<details>
<summary>Download</summary>
<br>
Image: http://os.archlinuxarm.org/os/ArchLinuxARM-odroid-latest.tar.gz
<br>
read this https://archlinuxarm.org/platforms/armv7/samsung/odroid-u2
the overview section
</details>
<details>
<summary>Install</summary>
<br>
http://os.archlinuxarm.org/os/ArchLinuxARM-odroid-latest.tar.gz
<br>
Finish the https://archlinuxarm.org/platforms/armv7/samsung/odroid-u2 <br>
installation section <br>
Then this thread: https://forum.odroid.com/viewtopic.php?t=1522 <br>
and install <br>

```shell
pacman-key --init
pacman-key --populate archlinuxarm
pacman -S uboot-tools
```

</details>

<details>
<summary>Move to SSD and use the SD card for boot and keeping the kernel</summary>
Login as root, list the SSD drive UUID and PARUUID with <br>

```shell
fdisk -l
blkid
```

Mount the SSD somewhere under /mnt , like sdb1 after checking which device it is with fdisk

```shell
mount /dev/sdb1 /mnt/SSD
```

Copy the rootfs part to the emmc/SD, to keep only the boot and the kernel on the emmc/SD

```shell
cd /
rsync -av * /mnt/SSD
```

Change the /boot/boot.src with the mkscr script: <br>


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
pacman -Sy
pacman -S docker docker-compose
</details>

<details>
<summary>Image local storage</summary>
960 GB disk, odroid_images/odroid_u/ArchLinuxARM-odroid-latest.tar.gz
</details>
