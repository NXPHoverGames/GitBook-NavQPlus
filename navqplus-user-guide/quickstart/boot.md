---
description: How to boot the board
---

# Boot

NavQPlus should boot normally after applying power.  While booting, the device will output status information to the serial console, accessible on the [UART2 connector](../../hardware/hardware-interfaces/uart/uart2-a53-debug.md). Once the boot process has completed, the system console is also available by starting an SSH session over (USB-)ethernet or Wi-Fi.

{% hint style="info" %}
There are [DIP switches on board that select the boot source](flashing-with-new-firmware/flashing-with-new-firmware.md) as either SD card or on-board eMMC memory. Ensure their settings match your intentions.
{% endhint %}

## Power requirements for successful boot&#x20;

If the applied voltage at PWR\_IN is too low, the boot process could hang upon initializing the CPU in the Linux kernel. Please make sure that your power input is 5-20V. The NavQPlus has relatively low current requirements and typically will not draw more than 4 watts of power when all on-chip peripherals are enabled, however the board may also supply power to external devices. Ensure that your power source is able to maintain a stable voltage level at the requested current.

{% hint style="warning" %}
If powering from USB-C it is possible with some Linux kernel/boot configurations that the USB-C port hardware is limiting current, or switches modes as software progresses. This may result in a hang or a reboot. If you suspect this is the case, try powering from the PWR\_IN port instead.
{% endhint %}

## U-Boot - Observe full boot process through the serial console

The boot process starts with U-Boot, loading the device trees in the boot partition and loading the Linux kernel. If you desire to observe the complete boot process, you will need to monitor the [serial console](serial-console.md) output on [UART2](../../hardware/hardware-interfaces/uart/uart2-a53-debug.md) by using the provided USB to serial converter cable.

## Shell login

Once the NavQPlus has booted to the shell, the default login credentials are as follows:

Username: _user_\
Password: _user_
