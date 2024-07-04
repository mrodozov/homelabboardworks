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
# remove the boot dir from the SSD copy:
rm -rf /mnt/boot
```

Add a line in /etc/fstab with the UUID of the SSD drive, like this one, with the UUID from the blkid command: <br>

```shell
UUID=7d1436c0-a73b-462c-a59e-36701c6a85ce     /   ext4    rw,user,auto    0    0
```

Copy the /boot/boot.src to a backup and then change it to use the SSD <br>
and the /boot/boot.txt to /boot/boot.txt.bk

```shell
cp /boot/boot.src /boot/boot.src.bak
cp /boot/boot.txt /boot/boot.txt.bak
```

remove this line from /boot/boot.txt <br>

```shell
part uuid ${devtype} ${devnum}:${bootpart} uuid
```

change this line: <br>

```shell
setenv bootargs "console=tty1 console=${console} root=PARTUUID=${uuid} rw rootwait smsc95xx.macaddr=${macaddr}"
```

like this: <br>

```shell
setenv bootargs "console=tty1 console=${console} root=PARTUUID=9d5603b3-01 rw rootwait smsc95xx.macaddr=${macaddr}"
```

where the PARTUUID value from whatever blkid in the command above returned for the SSD disk <br>
Change the /boot/boot.src with this, also find in the mkscr script: <br>

```shell
mkimage -A arm -T script -C none -n "hdd bscr" -d boot.txt boot.scr
```

which will rewrite the boot.scr and also will write the /etc/fstab as it is<br>

Then reboot to see if the SSD is mounting, and type <br>

```shell
mount
```

as root to see of both /dev/mmcblk* and /dev/sd* are mounted. The rootfs should be on the SSD, like this<br>

```shell
/dev/sda1 on / type ext4 (rw,relatime)
```

If the rootfs is now on the SSD, only mapping the /boot from the SD card remains. <br>
With blkid see the UUID of the SD card, and add it to the new /etc/fstab which is now on the SSD: <br>

```shell
UUID=30130f54-edfa-495f-8fe1-48424d141754     /mnt/emmc   ext4    rw,user,auto    0    0
/mnt/emmc/boot /boot/ none defaults,bind 0 0
```

This way, the kernel gets updated onto the SD/emmc card, everything else on the SSD <br>

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

```shell
pacman-key --init
pacman-key --populate archlinuxarm
pacman -Sy
pacman -S docker docker-compose
```

</details>

<details>
<summary>Image local storage</summary>
960 GB disk, odroid_images/odroid_u/ArchLinuxARM-odroid-latest.tar.gz
</details>
