---
author: Shinu Donney
title:  Installing Arch Linux with btrfs
subtitle: Installing Arch Linux May ISO with btrfs filesystem in UEFI boot mode
date: 2021-05-01
time_to_read: 10
categories: [linux arch_linux, technology]
---

## A brief walkthrough of installing Arch Linux with btrfs filesystem

> Note: the method that I have listed here is applicable to EFI boot mode.
For legacy BIOS, the steps are a bit different.

### Prepare an installation medium with the bootable arch iso

```sh
# using 'dd' command to write the arch iso to the installation medium 
# 'if' and 'of' are meant to be the input and output file flags
# progress flag gives us a visual indication during the process

dd if=/path/to/arch/iso of=/path/to/installation/medium progress=status
```

### Set the appropriate keyboard layout

the default is US. You may need to change it according to your locale.

### Connect to the network

Connecting to wired is pretty straight forward. To connect to a wireless
network, follow the steps given below:

```sh
# to get iwd prompt
iwctl  

## now in iwd prompt
$_ station <device_name> connect <network_name>

## you will be prompted for password if you have any
## and then exit iwd
$_ exit

# you should be connected and good to go
# verify you're connected
ping -c 3 archlinux.org
```

### Update system clock

```sh
timedatectl set-ntp true
```

### Partitioning your disks

Use cfdisk (by far the easiest) or fdisk or any other partioning app of your
choice to partition the disks. (I will be making a detailed post on partitioning
the disks and encrypting with LUKS).

a common layout:

- EFI: 512M
- swap: <=8G
- system: rest of the memory

In btrfs, you don't need to bother providing another partition for home and
root, because you will be using subvolumes and we will be assigning different
mount points different subvolumes.
