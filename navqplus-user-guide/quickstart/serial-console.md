# Serial Console

The NavQPlus kit comes with a USB-C to UART adapter and a TTL to USB cable. This adapter is used to tap into the serial debugging console on NavQPlus.

Simply connect the USB-C cable to your computer and the adapter, then plug in the JST-GH connector at the end of the adapter to the UART2 (A53 Debug/Console) port on NavQPlus.

![Location of UART2](<../../.gitbook/assets/image (1) (1) (1) (1).png>)

<figure><img src="../../.gitbook/assets/image (4) (2).png" alt=""><figcaption><p>USB to serial cable and adapter board</p></figcaption></figure>

<img src="../../.gitbook/assets/image (8).png" alt="" data-size="original"><img src="../../.gitbook/assets/image (3).png" alt="" data-size="original">

## Serial Terminal Software

Use your favorite serial console software such as PuTTY (Minicom, MobaXTerm, or screen) to access the NavQPlus serial console directly.&#x20;

### **Console Baud Rate**

**The baud rate is 115200**.

{% hint style="info" %}
The serial console may be used to observe the full boot sequence including uboot. \
\
BONUS!: The terminal program on your PC should not disconnect on reboot or reset of the NavQPlus since the connection at the PC is really to the USB-UART adapter board (inside the TTL-232R-USB cable).
{% endhint %}

