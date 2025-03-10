# Fix grub missing on arch linux or other OS

1. Using bootable usb, like rufus. Install Linux ISO in yout bootabe USB

2. Booting on bootable usb type 

```bash
lslbk
```

## Example:

```
sda           8:0    0 149.1G  0 disk
|-sda1        8:1    0     1G  0 part /boot
|-sda2        8:2    0   144G  0 part /
`-sda3        8:3    0     4G  0 part [SWAP]


Description:

/dev/sda1: Boot Partition

/dev/sda2: Root Partition

/dev/sda3: Swap Partition
```

## Mount in root and boot Partition

```bash
mount /dev/sda2 /mnt
```

```bash
mount /dev/sda1 /mnt/boot
```

```bash
arch-chroot /mnt
```

```bash
pacman -S grub efibootmgr
```

```bash
pacman -Sy os-prober
```

```bash
sudo nano /etc/default/grub
```

## scroll to the bottom and uncomment this hash (#)

```bash
GRUB_DISABLE_OS_PROBER=false
```

## Click on Keyboard

### CTRL + O
### ENTER
### CTRL + X


```bash
grub-install --target=x86_64-efi --efi-directory=/boot --bootloader-id=GRUB
```

```bash
grub-mkconfig -o /boot/grub/grub/cfg
```

### if you found windows boot manager, you can reboot the system

if it don't show. You need to boot on arch linux (before booting into arch linux, make sure to unplug the bootable usb. )

follow this command:

```bash
sudo pacman -sy
```

```bash
grub-mkconfig -o /boot/grub/grub/cfg
```

```bash
reboot your system to make sure windows boot manager is in GRUB.
```
