---
description: 100BaseT1 Ethernet interface
---

# T1 2-Wire Ethernet

## Introduction

100BaseT1 2-Wire Automotive Ethernet provides 100MBPS connections over simple twisted 2 wires for a distance of up to 15 meters. The line signaling on the wire is not directly compatible with traditional 100BaseTX (RJ45) connections, but a physical adapter may be used. Otherwise it is the same as traditional Ethernet.&#x20;

T1 is lightweight and reduces the cabling weight. The interface also does not require the use of magnetics, so it also saves weight and cost in that regard. Typically you will find T1 Ethernet used on Radar, Cameras, MR-CANHUBK3 and NXP flight controllers for drones.&#x20;

This interface is compatible with the T1 Adapter for PC or other embedded devices [RDDRONE-T1ADAPT](https://www.nxp.com/products/interfaces/ethernet-/automotive-ethernet-phy-transceivers/ethernet-media-converter-for-drones-rovers-mobile-robotics-and-automotive:RDDRONE-T1ADAPT) and the [MR-T1ETH8](https://www.nxp.com/products/security-and-authentication/authentication/sja1110-100base-t1-multi-gig-ethernet-switch-example-board:MR-T1ETH8) network switch for robotics.\
[RDDRONE-FMUK66](https://www.nxp.com/design/designs/px4-robotic-drone-vehicle-flight-management-unit-vmu-fmu-rddrone-fmuk66:RDDRONE-FMUK66) and FMURT6 also include T1 Ethernet

## T1 Ethernet Locator

<figure><img src="../../../.gitbook/assets/image (1) (5).png" alt=""><figcaption><p>Location of T1 Ethernet connector</p></figcaption></figure>

J18 is the T1 Ethernet connector and it should not be confused with the similar SE050 Secure-Element NFC connector at the opposite corner of the board.\
This is a JST-GH 2 pin heade. Technically there is a polarity associated with T1 Ethernet, but the TJA1103 Phy is configured to automatically and transparently swap the polarity as needed. It is still a good idea to attempt to maintain the correct polarity.

## NavQPlus uses the TJA1103 T1 Ethernet Phy

[TJA1103 ](https://www.nxp.com/products/interfaces/ethernet-/automotive-ethernet-phy-transceivers/asil-b-compliant-100base-t1-ethernet-phy:TJA1103)is the third-generation product of NXP’s successful family of 100BASE-T1 Automotive Ethernet PHYs. It is perfectly suited to support the rapid expansion of Ethernet to the edge of the network or provide robust connection to domain controllers in the center of the car.

[TJA1103 ](https://www.nxp.com/products/interfaces/ethernet-/automotive-ethernet-phy-transceivers/asil-b-compliant-100base-t1-ethernet-phy:TJA1103)complies with all state-of-the-art conformance test specifications and is designed according to ISO 26262 to meet ASIL B, providing enhanced monitoring and diagnostic features

## No magnetics

Unlike traditional Ethernet, a heavy coupling transformer is not used. A small common mode choke and simple passive RC network is used for noise filtering. There is an ESD protection diode used and the communications signals are capacitively coupled. \
This overall lightweight, small size and cost optimized solution lends itself well to mobile robotics applications. \


<figure><img src="../../../.gitbook/assets/image (24).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (23).png" alt=""><figcaption></figcaption></figure>

The Ethernet PHY itself is also extremely small:

<figure><img src="../../../.gitbook/assets/image (25).png" alt=""><figcaption></figcaption></figure>

## T1 Ethernet LEDs

There are two LEDS that connect directly to the TJA1103 PHY.&#x20;

| Name | Color   | Function       |
| ---- | ------- | -------------- |
| LED1 | Orange  | TMS/GPIO0/CFG0 |
| LED2 | Green   | TDI/GPIO1      |
|      |         |                |

\<TODO - additional description during operation>\




## T1 Ethernet Schematics

{% hint style="info" %}
At the time of publication (1/16/2023) [TJA1103 ](https://www.nxp.com/products/interfaces/ethernet-/automotive-ethernet-phy-transceivers/asil-b-compliant-100base-t1-ethernet-phy:TJA1103)pinout information was not allowed to be made public. It is expected this is a very short term restriction.
{% endhint %}

{% hint style="success" %}
Datasheets and technical documents for TJA1103 are available on request for users with an NXP account.
{% endhint %}

<figure><img src="../../../.gitbook/assets/image (10) (1).png" alt=""><figcaption></figcaption></figure>
