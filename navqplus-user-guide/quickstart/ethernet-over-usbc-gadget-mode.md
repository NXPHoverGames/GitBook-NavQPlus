---
description: Connecting the NavQ+ with ethernet
---

# Wired Network connections

The NavQPlus has the ability to connect via ethernet in several different ways.&#x20;

* Through the IX Industrial® Type A port. The provided IX to RJ45 adapter cable will allow connecting to RJ45  \*Preferred
* Using the USB-C port with "gadget bode" Ethernet over USB
* Through the 100 Base T1 automotive ethernet. A media converter such as RDDRONE-T1ADAPT, or a switch such as MR-T1ETH8 would allow connection to a typical RJ45 100Base-T port.
* Using a USB-C Ethernet adapter dongle

<figure><img src="../../.gitbook/assets/image (21).png" alt=""><figcaption></figcaption></figure>



### USB to Ethernet Adapter

Here is an example of how the NavQ+ can also be connected through the USB-C port. For this method, a separate adaptor is required to convert the USB-C to RJ45.&#x20;

<figure><img src="../../.gitbook/assets/image (9).png" alt=""><figcaption><p>Example of the USB-C ethernet connection.</p></figcaption></figure>

To be able to connect to the board through SSH it must be connected to the same network. This is possible by using a router and connecting your network cable to it then the NavQ+ and your PC to it. With this connection SSH can be established between your PC and the NavQ+. Below is an example of how the router could be connected.

<figure><img src="../../.gitbook/assets/image (18).png" alt=""><figcaption><p>The PC and the NavQ+ connected to the same router.</p></figcaption></figure>

{% hint style="warning" %}
Not all USB to Ethernet adapters are supported . In some cases you may also find that the board reboots when powering up with an unsupported adapter. While still sub-optimal, you can try circumventing the reboot by unplugging the ethernet and letting the board boot first. Once it is booted up you can retry attaching the adapter and connecting ethernet.
{% endhint %}

After everything is connected correctly a connection can be made through SSH. This is done with the following code, on your PC terminal:

```
ssh user@imx8mpnavq.local
```

or you can input the IP address of your NavQ+:

```
ssh user@<NavQ+'s IP address>
```

You will be asked to input the password.&#x20;

The default password is _**user**_.

{% hint style="info" %}
You can also find your IP address using the command: _ifconfig_&#x20;
{% endhint %}

At this point you may want to consider following steps to connect the NavQPlus WiFi to a local network.&#x20;
