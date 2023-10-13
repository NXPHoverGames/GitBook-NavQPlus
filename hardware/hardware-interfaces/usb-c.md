---
description: Using the USB-C interface
---

# USB-C

## Port configuration

NavQPlus includes two USB 3.0 Type C ports that are capable of acting as PD devices.

PD modes, Controller, Peripheral mode, USB Gadget Mode are configured at compile time, and may change depending on what image you are using.&#x20;

{% hint style="danger" %}
It is VERY IMPORTANT to be aware of **PD mode** (power delivery mode) settings on your board. This is an embedded board with complete manual control.&#x20;

\
It is POSSIBLE to configure the settings and cables such that the powerfrom the POWER IN connector flows through to the USB C port without full negotiation.&#x20;

This is particularly problematic if you be using a USB C to USB type A cable/connector, USB A ports is only specified to 5V. USB C are protected to 20V &#x20;

\
PERMANENT DAMAGE TO THE CONNETED DEVICE could occur!
{% endhint %}

The default image as of the date shown here configures the USB ports as follows. (Last updated 10/13/2023 )

## USB 1:&#x20;

USB-C port closest to the edge of the board.&#x20;

This port is used for _connecting_ devices, such as USB-C hubs, cameras, sensors, and more.

## USB 2:&#x20;

USB-C port closest to the middle of the board.&#x20;

This port is used for _powering_ the board, as seen in the Power page in the User Guide. This port accepts USB-C PD, and also allows data transfer.&#x20;

USB Gadget Ethernet is supported over this port with the interface `usb0`.
