---
title: "Arch Linux Install Guide"
date: 2024-08-21T12:52:57Z
draft: false
tags: [Arch Linux, Linux, Guide, Linux Guide]
---
A usefull guide for installing arch linux using the command-line.

## Overview
Arch Linux is a linux distro that a lot of people say is too hard to install because you have to do everything yourself, but as arch linux has grown the user base has as well and with that, it has become more simple to install.

This guide is aimed at helping you install arch linux on your device. Let's get to the installation.

# Installing Arch Linux

## Reqirements

1. Internet (It is recommended to use ethernet, but I will go over using wifi as well)
2. USB Drive for installer.
3. Arch Linux Installer ISO.
4. Another computer for flashing the USB and reading the guide.

## Getting Started

Download Balena Etcher to your computer from [HERE](https://www.balena.io/etcher).

After downloading Balena Etcher install it and download the Arch Linux ISO from [HERE](https://archlinux.org/download/).

Open Balena etcher and select the Arch Linux ISO to flash. Select the drive you want to flash the installer to. Then click flash. (**Note if you are on MacOS or Linux, it might ask for a password**)

After flashing the ISO to you USB drive, plug the drive into your computer and select the drive from your bios menu and boot into the installer.

### Installing Arch Linux

after booting into the installer you will be greeted with the command line. 

check if you system supports UEFI
```
# cat /sys/firmware/efi/fw_platform_size
```

sync the clock with UTC

```
# timedatectl
```

list drives

```
# lsblk
```

start fdisk

```
# fdisk /dev/the_disk_to_be_partitioned
```

#### Example disk layout

| Mount point on the Installed System | Partition | Partition Type |Suggested Size|
| :---------- | :---                          | :---                   | :---    |
| /efi        |   /dev/efi_system_partition   | Efi                    | 512 MiB |
| [SWAP]      |   /dev/swap_partition         | Linux Swap             | Use this: [Swap Calc](https://pickwicksoft.github.io/swapcalc/) |
| /           |   /dev/root_partition         | Linux x86_64 root (/)  | Remainder of the device. <br>At least 23–32 GiB. |

### Creating and Formating the partitions

```
When I type enter hit the return key
n
ENTER
ENTER
ENTER
+512M
ENTER
n
ENTER
ENTER
ENTER
+2G
ENTER
n
ENTER
ENTER
ENTER
p
ENTER
W
ENTER
```

I will be using EXT4 for this example but you can use any format that is supported though there might be extra setup for BTRFS.

create a root partition

```
# mkfs.ext4 /dev/root_partition/
```

create a swap partition

```
# mkswap /dev/swap_partition
```

create an efi partition

```
# mkfs.fat -F 32 /dev/efi_system_partition
```

#### Mount the file systems

mount the root partition

```
# mount /dev/root_partition /mnt
```

mount the efi partition

```
# mount --mkdir /dev/efi_system_partition /mnt/efi
```

turn on swap

```
# swapon /dev/swap_partition
```

### Installation

#### Install essential packages

packages that you shoul install

 - base
 - base-devel
 - linux
 - linux-firmware
 - grub
 - efibootmgr
 - cpu microcode (amd-ucode for amd chips or intel-ucode for intel chips)
 - iwd or networkmanager (for wifi)
 - git
 - zsh
 - zsh-autosuggestions
 - zsh-completions
 - openssh
 - python3
 - sudo
 - man (documentation)
 - reflector 
 - pipewire pipewire-alsa pipewire-pulse pipewire-jack (audio drivers)
 - wireplumber (audio manager)
 - nano or vim (for text editing)

 install packages
```
# pacstrap -K /mnt base base-devel linux linux-firmware grub efibootmgr amd-ucode networkmanager git zsh zsh-autosuggestions zsh-completions openssh python3 sudo man reflector pipewire pipewire-alsa pipewire-pulse pipe-wire-jack wireplumber nano
```

#### Fstab

```
# genfstab -U /mnt >> /mnt/etc/fstab

# cat /mnt/etc/fstab
```

#### Chroot

```
# arch-chroot /mnt
```

#### Localization

Edit /etc/locale.gen and uncomment en_US.UTF-8 UTF-8 and other needed UTF-8 locales. Generate the locales by running:

```
# locale-gen
```

Create the locale.conf file, and set the LANG variable accordingly:

```
/etc/locale.conf
----------------
LANG=en_US.UTF-8
```

#### network config

Create the hostname file:

```
/etc/hostname
----------------
*yourhostname*
```

#### Root Password

set the root password:

```
# passwd
```

#### Create a User

add your user:

```
# useradd -mG wheel yourname
```


Uncomment the wheel group to allow execution of any command( ie: remove the # from the wheel line below where it says something like: "Uncomment to let members of group wheel execute any action" ). if you want to use nano then write EDITOR=nano instead.

```
# EDITOR=vim visudo
```

#### Grub Config

Install the grub bootloader:

```
# grub-install --target=x86_64-efi --efi-directory=/efi --bootloader-id=Arch
```

Generate the grub config file:

```
# grub-mkconfig -o /boot/grub/grub.cfg
```

#### Enable ssh and Networking

```
# systemctl enable sshd

# systemctl enable NetworkManager
```

#### Reboot

```
# reboot
```

## Post Install Configuration

This section is optional but recommended because it gives you a desktop and display manager as well as other useful tools for Arch Linux.

### Getting a Desktop environment and Display manager

Here are some Desktop Environments that I recommend.

| Desktop environment | Install Command | Pros | Cons |
| ------------------- | --------------- | ---- | ---- |
| XFCE | ```# pacman -S xfce4 xfce4-goodies xorg-server lightdm``` | Very Simple <br> Lightweight <br> Customizable | Lack of advanced features |
| GNOME | ```# pacman -S gnome gnome-extras gdm``` | Easy to use <br> clean interface | Heavy on resources <br> not customizable |
| KDE Plasma | ```# pacman -S plasma-meta kde-applications-meta sddm``` | Heavily cutomizable <br> clean interface | very resource intensive |

There are other desktop environments you can choose but the above are what I reccomend if you want to get started.

For the guide I will outline the setup for each DE (desktop environment) and DM (display manager) in the table above.

#### XFCE 

Use the command written below to install XFCE4 and the LightDM display manager:

```
# sudo pacman -S xfce4 xfce4-goodies xorg-server lightdm
```

then to enable lightdm:

```
# sudo systemctl enable --now lightdm
```

#### GNOME

Use the command below to install GNOME and the GDM display manager:

```
# sudo pacman -S gnome gnome-extras gdm
```

then to enable gdm:

```
# sudo systemctl enable --now gdm
```

#### KDE Plasma

Use the command below to install KDE Plasma and the SDDM display manager:

```
# sudo pacman -S plasma-meta kde-applications-meta sddm
```

then to enable sddm:

```
sudo systemctl enable --now sddm
```

