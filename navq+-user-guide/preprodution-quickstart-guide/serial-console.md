# Serial Console

The NavQPlus kit comes with a USB-C to UART adapter and cables. This adapter is used to tap into the serial debugging console on NavQPlus.

* Simply connect the USB-C cable to your computer and the adapter, then plug in the JST-GH connector at the end of the adapter to the UART2 port on NavQPlus.

![](<../../.gitbook/assets/image (1) (1).png>)

Use your favorite serial console software (PuTTY, Minicom, MobaXTerm, and screen are a few examples) to access the NavQPlus serial console directly. **The baud rate is 115200**.

{% hint style="info" %}
The serial console may be used to observe the full boot sequence including uboot. \
\
The terminal program on your PC should not disconnect on reboot or reset since the connection at the PC is really to the USB-UART adapter board.
{% endhint %}
