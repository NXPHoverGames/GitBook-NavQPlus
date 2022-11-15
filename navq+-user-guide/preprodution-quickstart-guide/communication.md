# Communication

There are several interfaces for communication between boards on NavQPlus. The existing communication protocols are as follows:

1. <mark style="color:green;">UART (UART3, /dev/ttymxc2)</mark>
2. <mark style="color:green;">100BaseT1 "2-wire" Automotive Ethernet</mark>
3. <mark style="color:green;">1000BaseTX Gigabit Ethernet (through the IX Industrial Ethernet connector)\*</mark>
4. <mark style="color:green;">CAN-FD Bus w/</mark> [<mark style="color:blue;">TJA1463 CAN-SIC signal improvement</mark>](https://www.nxp.com/products/interfaces/can-transceivers/can-signal-improvement/can-signal-improvement-capability-transceiver-with-sleep-mode:TJA1463) <mark style="color:green;">PHYs (can0 and can1 interfaces)</mark>&#x20;
5. <mark style="color:green;">I2C</mark>
6. <mark style="color:green;">USB-C (including Gadget mode)</mark>
7. <mark style="color:red;">SPI</mark>

\*The 1000BaseTX Ethernet is not installed on "-XE" versions of 8MPNAVQ due to supply shortages from 3rd party suppliers.&#x20;

{% hint style="info" %}
HoverGames3 boards are 8MPNAVQ-4GB-XE and do not have the Gigabit Ethernet installed. However a USB hub with RJ45 Ethernet adapter is provided. Gadget mode on USB-C may also be used to provide a network interface to a PC.
{% endhint %}

&#x20;

* Currently tested and working interfaces are highlighted <mark style="color:green;">green</mark>.&#x20;
* Non-tested/Non-Validated interfaces are listed <mark style="color:red;">red</mark>.
* Testing list updated Nov 2022

