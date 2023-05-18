---
description: How to boot the board
---

# Boot

## Introduction

NavQPlus should boot normally after applying power.  While booting it will output text to the serial console if one is attached. Otherwise you may choose to wait a few moments until an SSH over Ethernet or USB-Ethernet is available when it is fully booted.

{% hint style="info" %}
There are DIP switches on board that select the boot source as either SDCARD or on board EMMC. Ensure they match your intentions\
See this link for the [Boot DIP switch settings](flashing-with-new-firmware/flashing-with-new-firmware.md).
{% endhint %}

###

### Voltage/current applied for successful boot&#x20;

If the voltage at PWR IN is too low the boot process could hang upon initializing the CPU in the Linux Kernel. Please make sure that your power input is 5-20V. The NavQPlus has relatively low current requirements and typically will not draw more than 4 watts with everything enabled, however it may also supply power to external devices. Ensure that your power source is able to maintain enough voltage at the requested current.

{% hint style="warning" %}
NOTE: If powering from USB-C it is possible with some Linux kernel/boot configurations that the USB-C port hardware is limiting current or switches modes as software progresses. This may result in a hang or a reboot. If you suspect this is the case, try powering from the PWR\_IN port instead.
{% endhint %}



## UBoot - Observing complete boot process using console

The boot process starts with U-Boot, loading the device trees in the boot partition and loading the Linux Kernel.

{% hint style="info" %}
In order to observe the full complete boot process, you will need a serial port adapter connected to the board serial console. A USB-serial port adapter cable assembly is provided for this purpose. However once satisfied low level booting is operating normally, you typically may just wait until a remote SSH connection is able to be established via networking.
{% endhint %}

## Shell login

Once the NavQPlus has booted to the shell, the login information is as follows:

Username: user

Password: user
