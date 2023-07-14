---
description: How to power the board
---

# Power

\<TODO> Improve page!

<figure><img src="../../.gitbook/assets/image (5).png" alt=""><figcaption></figcaption></figure>

There are two ways to power the NavQPlus. You can power it through the PWR IN port or through the USB-C port in the middle.

\
**It is preferred to power the board through the PWR **_**IN port for highest reliability.**_\
This is because it is possible that the USB-C logic may be configured in software in a manner that limits current. This leads to unexpected behavior at power up. If you suspect something is "weird" on power up or you see the board rebooting, please try powering through PWR\_IN first.&#x20;

The PWR IN port accepts an input in the 6V-20V range. (Technically should work from 5V to 29V, but has not been fully characterized)

The PWR IN port pinout schematic is as follows: (center pin is unused)

![](<../../.gitbook/assets/image (4) (1).png>)

With Pin 1 being the top pin in the image above. PWR\_UNREG is just 5-20V power.

## Unexpected Power Resets

{% hint style="warning" %}
&#x20;If you encounter unexpected resets, it could be&#x20;

1\) That your power supply is not able to provide enough current for the board or the board + peripherals resulting in a brownout condition when internal blocks, interfaces, peripherals turn on and draws additional current.\
Supplying power with a LiPo battery may help debug if you have a bench or wall adapter power supply limitation.&#x20;



2\) The PWR IN port is connected to a power switch that can be sense to reverse current spikes on the power supply and de-assert a power good signal, causing a reset. This may happen when something is sharing the power supply and powers up on a hot power supply and "glitches" the power line. A reverse blocking diode on a power distribution board or inline with the power cable may be desired.



3\) As mentioned above, when powering from USB-C, the specific linux image should be checked to ensure that the Linux Kernel is not resetting the USB power when it starts up after the bootloader is completed. (i.e the bootloader configures USB-C, then the Linux Kernel may also be set to re-configure/reset the USB-C also and in the process switching it off again.
{% endhint %}
