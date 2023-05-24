---
description: Connecting the NavQ+ with ethernet
---

# Ethernet connection (DRAFT)

\<todo> describe connection using firmware that has the USBC configured in Gadget mode and appears as an Ethernet network interface.

\<todo> Check if all information is correct



The NavQ+ has the possibility to be connected through ethernet in two different ways. Using the USB-C port or through the IX Industrial® Type A port.&#x20;

<figure><img src="../../.gitbook/assets/image (21).png" alt=""><figcaption></figcaption></figure>

Here is an example of how the NavQ+ should be connected through the USB-C port. An adaptor is required to convert the USB-C to RJ45.

<figure><img src="../../.gitbook/assets/image (9).png" alt=""><figcaption><p>Example of the USB-C ethernet connection.</p></figcaption></figure>

To be able to connect to the board through SSH it must be connected to the same network. This is possible by using a router and connecting your network cable to it then the NavQ+ and your PC to it. With this connection SSH can be established between your PC and the NavQ+. Below is an example of how the router should be connected.

<figure><img src="../../.gitbook/assets/image (18).png" alt=""><figcaption><p>The PC and the NavQ+ connected to the same router.</p></figcaption></figure>

{% hint style="warning" %}
A common issue when booting up the NavQ+, with the USB-C port is used as ethernet, is that the board get stuck on a reboot loop. This is fixed by just unplugging the ethernet and letting it boot. Once it is booted up you can connect the ethernet back.
{% endhint %}

After everything is connected correctly a connection can be made through SSH. This is done with the following code, on your PC terminal:

```
ssh user@imx8mpnavq.local
```

or you can input the IP adress of your NavQ+:

```
ssh user@<NavQ+'s IP address>
```

You will be asked to input the password. The default password is _**user**_.

{% hint style="info" %}
You can find your IP address using the code: _ifconfig_&#x20;
{% endhint %}

