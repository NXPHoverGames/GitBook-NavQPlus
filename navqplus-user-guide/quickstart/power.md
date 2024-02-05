---
description: Powering NavQPlus
---

# Power supply options



<figure><img src="../../.gitbook/assets/image (5).png" alt=""><figcaption></figcaption></figure>

{% hint style="danger" %}
NEVER use USB-C to USB-A cables without a hub or blocking device. In this embedded platform software has complete control over USB-PD and it is POSSIBLE to provide power >5V on the USB-C connector without handshaking. USB-A is only 5V tolerant and this can damage certain devices.
{% endhint %}

There are two ways to power the NavQPlus. You can power it through the `PWR IN` port or through the middle\*  USB-C port (\*dependent on software image loaded)

{% hint style="info" %}
**It is  preferred to power the board through the PWR **_**IN port for highest reliability.**_
{% endhint %}

\
This is because it is possible that the USB-C power management logic may be configured in software in a manner that limits current or resets the power management in the time between the bootloader running  and the Linux image running . This leads to unexpected behavior at power up. If you suspect something unusual is occurring on power up or you see the board rebooting, please try powering through PWR\_IN first.&#x20;

The PWR IN port accepts an input in the 5V-20V\* range. (Technically higher (24V?), but has not been fully validated or characterized)

The PWR IN port pinout schematic is as follows: (center pin is unused). Pin 1, 2 are the power input, Pin 4, 5 are negative (GND).

![](<../../.gitbook/assets/image (4) (1).png>)

The input power voltage connection PWR\_UNREG is 5V-20V

## Unexpected Power Resets

If you encounter unexpected resets, it could be any of the following issues



### **Insufficient Current Available:**&#x20;

That your power supply is not able to provide enough current for the board or the board + peripherals resulting in a brownout condition when internal blocks, interfaces, peripherals turn on and draws additional current.

\
Supplying power with a LiPo battery may help debug if you have a bench or wall adapter power supply limitation.&#x20;



### **Power Glitch from other boards:**&#x20;

The PWR IN port is connected to an onboard power control switch that **can sense reverse current spikes** on the power supply and de-assert a power good signal, causing a reset. This may happen when another device is sharing the power supply and "glitches" the power supply when plugged in live. A reverse blocking diode and additional bulk capacitors on a power distribution board or inline with the power cable may be desired.



### &#x20;**Linux Image problems:**&#x20;

As mentioned above, when powering from USB-C, the specific Linux image should be checked to ensure that the Linux Kernel is not resetting the USB power when it starts up after the bootloader is completed. (i.e the bootloader configures USB-C, then the Linux Kernel may also be set to re-configure/reset the USB-C also and in the process switching it off again.
