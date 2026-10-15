# VFIO-Tool: best Linux tool ever made by AI! (Seriously, I made it using AI, but every contrib is welcome!)



# ==== DISTROS TESTED ====

Debian (me): worked

Gentoo (me): broke my Gentoo install on GPU switching (I may be to blame)

# ==== DEPENDENCIES =====

To run this script successfully, your system needs standard GNU core utilities
(like sed, grep, awk, cat, etc.) which are pre-installed on virtually every
Linux distribution.

The primary external command the script relies on is lspci (to scan for GPUs and
SSDs), which is provided by the pciutils package.

Beyond that, the script relies on your distribution's native bootloader (GRUB or
systemd-boot) and initramfs generators, which are almost always installed by
default based on the OS you are using.

Here is the breakdown of dependencies by distribution and how to install them if
they are missing:

1. Debian / Ubuntu / Linux Mint

These distributions use GRUB and update-initramfs by default.

  - Dependencies: pciutils, initramfs-tools, grub2-common
  - Install command:
    sudo apt update
    sudo apt install pciutils initramfs-tools grub2-common

2. Pop!_OS

Pop!_OS is Ubuntu-based but uses systemd-boot (managed by kernelstub) instead of
GRUB.

  - Dependencies: pciutils, initramfs-tools, kernelstub
  - Install command:
    sudo apt update
    sudo apt install pciutils initramfs-tools kernelstub

3. Arch Linux

Arch uses mkinitcpio by default. Bootloaders vary by user preference, but
systemd-boot and grub are the most common.

  - Dependencies: pciutils, mkinitcpio, and grub (only if you use GRUB)
  - Install command:
    sudo pacman -S pciutils mkinitcpio

4. Fedora / RHEL (Red Hat Enterprise Linux)

These distributions use dracut and GRUB2 by default.

  - Dependencies: pciutils, dracut, grub2-tools
  - Install command:
    sudo dnf install pciutils dracut grub2-tools

5. SUSE (openSUSE / SLES)

SUSE distributions generally use dracut and GRUB2.

  - Dependencies: pciutils, dracut, grub2
  - Install command:
    sudo zypper install pciutils dracut grub2

6. Gentoo

Gentoo is heavily customizable. Users typically generate their initramfs using
either dracut or genkernel. The script supports both.

  - Dependencies: sys-apps/pciutils, sys-boot/grub, and either sys-kernel/dracut
    OR sys-kernel/genkernel
  - Install command:
    sudo emerge --ask sys-apps/pciutils
    ## And one of the following based on your setup:
    sudo emerge --ask sys-kernel/dracut
    sudo emerge --ask sys-kernel/genkernel

Summary of what the script actually calls:

If you are building a custom minimal OS, make sure these commands are accessible
in your $PATH:

  - Base utils: bash, lspci, grep, awk, tr, head, cut, sed, cat, rm, wc
  - Initramfs Updaters (Needs AT LEAST 1): update-initramfs, mkinitcpio, dracut,
    or genkernel
  - GRUB Updaters (Only if using GRUB): update-grub, grub-mkconfig, or
    grub2-mkconfig
======= USAGE =======
Download the code from here and in terminal;
1) chmod +x vfio-tool
2) sudo ./vfio-tool
