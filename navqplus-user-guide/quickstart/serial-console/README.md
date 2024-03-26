---
description: Connecting to the serial console
---

# Serial Console

The NavQPlus kit comes with an FTDI type USB-C to UART adapter cable and a small adapter board for this cable to the serial port JST-GH connector . This adapter is used for a serial debugging console on the NavQPlus.

## USB to UART adapter

Executive Summary: Connect the included USB to UART adapter to the UART2 port on the NavQPlus, and open your favorite serial console application (e.g. PuTTy for Windows users, Minicom on Linux). Open a serial console and set the baud rate to 115200. If there is no output on the screen, try to press enter to get a log-in prompt.

<div align="center">

<figure><img src="../../../.gitbook/assets/image (4) (2).png" alt=""><figcaption><p>USB to serial cable and adapter board (Not exactly as shown)</p></figcaption></figure>

</div>

<figure><img src="../../../.gitbook/assets/image (33).png" alt=""><figcaption></figcaption></figure>



Connect USB cable+ adapter to your computer. Then plug in the JST-GH connector from the adapter into  UART2 (A53 Debug/Console) port on NavQPlus.

<figure><img src="../../../.gitbook/assets/image (3) (1) (2).png" alt=""><figcaption></figcaption></figure>

## Serial Terminal Software

Use your favorite serial console software such as PuTTY (Minicom, MobaXTerm, or screen) to access the NavQPlus serial console directly.&#x20;

### **Console Baud Rate**

**The baud rate is 115200**.

{% hint style="info" %}
The serial console may be used to observe the full boot sequence including uboot. \
\
BONUS!: The terminal program on your PC should not disconnect on reboot or reset of the NavQPlus since the connection at the PC is really to the USB-UART adapter board (inside the TTL-232R-USB cable).
{% endhint %}

## Successful Boot?

If correct code was loaded, and the boot switches also set back to the correct boot source (SDCARD vs EMMC), then in the terminal software you should see the Linux boot details printing out.&#x20;

### Default username and default password

The system will ask for the username and then the password. The default username/password is as follows:&#x20;

```
Username: user 
Password: user 
```

At this point you can start using Linux on the NavQPlus.
