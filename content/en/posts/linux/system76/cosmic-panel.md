---
title: "COSMIC Panel First Look"
tags: ["rust", "linux", "pop_os", "system76"]
type: "blank"
author: "Eduardo Flores"
cover: /images/articles/linux/system76/cosmic_panel/cosmic_panel.png
publishdate: 2022-01-19
---

This article shows how the new COSMIC Panel will look like.

After a few months of development, System76 has finally released the first official pictures of what the new COSMIC desktop will look like, specifically the COSMIC Panel.

## Applets

Looks like System76 is moving away from the traditional "extensions" and plans to design an API for third party applets, this is similar to what KDE, XFCE and others are doing.

So far, we know that these applets will be able to be placed in the dock and the top panel, but this may not be the only places we might see them.

This is exciting news, this will make COSMIC a much more powerful desktop environment, making it extendable and customizable.

Let's get our first look.

## Sound Applet

Perhaps one of the most exciting ones is the new sound applet. 

![sound_applet](/images/articles/linux/system76/cosmic_panel/sound_applet.png "Sound Applet")

Here's a look at the previous version for reference.

![current_applet](/images/articles/linux/system76/cosmic_panel/current_applet.png "Current Applet")

Right off the bat, we notice a big change compared to the previous version, starting with the fact that we no longer have a single menu for everything, instead we have an applet for each category.

This allows the applet to do so much more, we're now able to:

- Change the output and input devices.
- Control currently playing media.
- Access the sounds settings.
- Display media controls in the top panel.

## Power Applet

The power applet is a bit interesting, we can now control the power settings with one click, no more settings hidden inside submenus.

![power_applet](/images/articles/linux/system76/cosmic_panel/power_applet.png "Power Applet")

We have big buttons for Suspend, Restart and Shut Down, which is greatly appreciated.

## Network Applet

The network applet has a lot of changes, that is because we barely had one before.

![network_applet](/images/articles/linux/system76/cosmic_panel/network_applet.png "Network Applet")

This applet will allow us to:

- Toggle Airplane Mode and Wi-Fi.
- See a list of the available networks.
- Access network settings.
- See the currently connected network, IP address and its status.

#### Wireless connection

![wifi_process](/images/articles/linux/system76/cosmic_panel/wifi_process.png "WiFi Process")

![wifi_disconnect](/images/articles/linux/system76/cosmic_panel/wifi_disconnect.png "WiFi Disconnect")

The applet will also allow us to scroll through the available networks, and connect to them.

![wifi_expanded](/images/articles/linux/system76/cosmic_panel/wifi_expanded.png "WiFi Expanded")

![try_establish](/images/articles/linux/system76/cosmic_panel/try_establish.png "Try Establish")

![try_connect](/images/articles/linux/system76/cosmic_panel/try_connect.png "Try Connect")

This will make connecting to a wireless network, without losing focus on the applet possible.

#### Wired connection 

When we plugin a cable, we will be able to see the it and the network speed at the top of the applet. 

![wifi_off](/images/articles/linux/system76/cosmic_panel/wifi_off.png "WiFi Off")

![wired_wifi](/images/articles/linux/system76/cosmic_panel/wired_wifi.png "Wired WiFi")

#### Airplane Mode and Proxy

![airplane_proxy](/images/articles/linux/system76/cosmic_panel/airplane_proxy.png "Airplane Proxy")

#### VPN

![vpn](/images/articles/linux/system76/cosmic_panel/vpn.png "VPN")

## Bluetooth Applet

The bluetooth applet will also allow us to connect to a device without having to leave the applet.

![bluetooth_applet](/images/articles/linux/system76/cosmic_panel/bluetooth_applet.png "Bluetooth Applet")

![bluetooth_connection](/images/articles/linux/system76/cosmic_panel/bluetooth_connection.png "Bluetooth Connection")

## Date, Time and Calendar Applet

![calendar_applet](/images/articles/linux/system76/cosmic_panel/dtc.png "Calendar Applet")

![date_settings](https://user-images.githubusercontent.com/57502897/150221125-83c41f40-6eca-42ff-8742-5a28ef898040.png "Date Settings")

## Notifications Applet

![nca](/images/articles/linux/system76/cosmic_panel/nca.png "Notification Center")

## Graphics Mode Applet

![gma](/images/articles/linux/system76/cosmic_panel/gma.png "Graphics Applet")

## Input Source Applet

![isa](/images/articles/linux/system76/cosmic_panel/isa.png "Input Source Applet")

## Desktop with Applets

This is how the new COSMIC desktop will look like with the new applets.

![desktop](/images/articles/linux/system76/cosmic_panel/desktop.png "Desktop")

## Cosmic Settings for Applets

It looks like we're going to be able to chose the segment in which we want our applets to appear, not only that, we will also be able to choose the order in which they appear, moving them right or left as shown below.

![cosmic_settings](https://user-images.githubusercontent.com/57502897/150034807-a9972733-0384-4c62-a44d-b40aeb6740d8.png "Cosmic Settings")

## Conclusion

This is a huge improvement compared to the previous version, and it's a big step forward for the COSMIC desktop.

You can test a demo version of the COSMIC desktop [here](https://www.figma.com/proto/ZeGTqzAM7dVZgjEW3uhxcd/Top-panel-(Copy)?node-id=1096%3A100109&scaling=min-zoom&page-id=559%3A11099&starting-point-node-id=1096%3A100109&show-proto-sidebar=1).

If you want more details, you can check out the [COSMIC Panel Repository](https://github.com/pop-os/cosmic-panel).