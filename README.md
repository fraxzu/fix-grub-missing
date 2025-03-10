Fix grub missing on arch linux or other OS

1. Using bootable usb, like rufus. Install Linux ISO in yout bootabe USB

2. Booting on bootable usb type lslbk

Example:
sda           8:0    0 149.1G  0 disk
|-sda1        8:1    0     1G  0 part /boot
|-sda2        8:2    0   144G  0 part /
`-sda3        8:3    0     4G  0 part [SWAP]

/dev/sda1: Boot Partition

/dev/sda2: Root Partition

/dev/sda3: Swap Partition

Mount in root and boot Partition
4. mount /dev/sda2 /mnt

5. mount /dev/sda1 /mnt/boot

6. arch-chroot /mnt

7. pacman -S grub efibootmgr

8. pacman -Sy os-prober

9. sudo nano /etc/default/grub

10. scroll to the bottom and uncomment this hash (#)

GRUB_DISABLE_OS_PROBER=false

11. CTRL + O
    ENTER
    CTRL + X

12. grub-install --target=x86_64-efi --efi-directory=/boot --bootloader-id=GRUB

13. grub-mkconfig -o /boot/grub/grub/cfg

14. if you found windows boot manager
you can reboot the system

if it don't show. You need to boot on arch linux (before booting into arch linux, make sure to unplug the bootable usb. )

follow this command:

14. sudo pacman -sy
15. grub-mkconfig -o /boot/grub/grub/cfg

16. reboot your system to make sure windows boot manager is in GRUB.
