---
title: "How to triple-boot Windows, macOS and Linux?"
tags: ["tools", "development"]
layout: "post"
url: "articles/tripleboot"
author: "Eduardo Flores"
publishdate: 2020-09-16
summary: As developers, we sometimes require to test our software on different platforms, this can be hard to do especially if you don't own a Mac, fortunately, there is a way to do exactly that
---

![Header](header.png)

As developers, we sometimes require to test our software on different platforms, this can be hard to do especially if you don't own a Mac, fortunately, there is a way to do exactly that.

For the past months I've been using Windows, Linux, and macOS in a single machine, here's how I did it.

# Disclaimer

In order to get this working, you have to meet the following requirements:

1. At least two hard drive units to install the operating systems, but if you prefer to have three separate disks for each system that works too.
2. Integrated Intel graphics or dedicated AMD Radeon graphics.
3. Intel (Ivy Bridge or higher) or AMD (Bulldozer or higher) processor.
4. Basic knowledge of command lines and how to use a terminal.

# Windows

Let's start with Windows.

1. Download the Media Creation Tool from Microsoft's [website](https://www.microsoft.com/software-download/windows10)
2. Create a bootable USB using **Media Creation Tool**.
3. Boot into the USB and [install](https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/install-windows-from-a-usb-flash-drive) Windows in either of the drives.
4. Boot into Windows.

This is the first step, let's get to Linux.

# Linux

This guide will focus on installing Ubuntu, as it is the most popular distribution, but you can choose any distribution you like, my recommendation is [PopOS!](https://pop.system76.com/) for developers.

1. Download the ISO from Canonical's [website](https://ubuntu.com/download/desktop)
2. Create a bootable USB using [Rufus](https://rufus.ie/).
3. Boot into the USB and install Linux either alongside Windows in the same drive in case you have two drives or in the second drive assuming you have three drives.
4. Boot into Linux.

Once you've successfully booted your system, follow the instructions to install macOS.

# macOS

Now you have a dual-boot between Windows and Linux, it's time to inject macOS into the mix. There is no standard way of creating the bootable USB, every computer requires manual setup.

If you'd like to follow the visual guide, check out this [link](https://youtu.be/eUnVzJsINCI).

If you'd like to follow the written guide, check out this [link](https://dortania.github.io/OpenCore-Install-Guide/).

1. Follow either of the guides mentioned before to create the bootable USB.
2. Once you've created the USB is time to boot from it.
3. Install macOS in the third drive.
4. Boot to macOS and follow the [post-install](https://dortania.github.io/OpenCore-Post-Install/) instructions to get it booting without the USB.

# Set up BIOS

Once all the systems are installed, you need to go to your BIOS options.

1. Either press the [DEL] or [F2] key, depending on your system, when your manufacturer logo shows up on screen to get to the BIOS.
2. Select OpenCore or the drive where you installed macOS as your default boot option and save changes.

Now every time you boot your computer you will be presented with a bootloader, letting you choose between your installations.
You can improve how the bootloader looks by following this [guide](https://dortania.github.io/OpenCore-Post-Install/cosmetic/gui.html).

If you enjoyed this article, consider sharing it so more people can benefit from it! Also, feel free to [@me](https://twitter.com/edfloreshz) on Twitter.
