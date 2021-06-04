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

- Prepare an installation medium

```sh
# using 'dd' command to write the arch iso to the installation medium 
# 'if' and 'of' are meant to be the input and output file flags
# progress flag gives us a visual indication during the process

dd if=/path/to/arch/iso of=/path/to/installation/medium progress=status
```
