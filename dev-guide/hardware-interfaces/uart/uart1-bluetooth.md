---
description: UART1 - Bluetooth
---

# UART1 (Bluetooth)

## Introduction

UART1 is assigned to communicate with the Bluetooth portion of the WiFi/BT Wireless module on the NavQPlus Baseboard. Therefore it is not available for general use (outside of creating your own  modified custom baseboard). \
\


<figure><img src="../../../.gitbook/assets/image (1) (1).png" alt=""><figcaption><p>SOM to Baseboard connector</p></figcaption></figure>

## UART1 interface voltage

The signaling from the SOM to the NavQPlus carrier board on J16 is at 3V3 but the Murata 1ZM expects 1.8V. The level conversion is done using U26.

<figure><img src="../../../.gitbook/assets/image (5).png" alt=""><figcaption></figcaption></figure>

## Software

[https://ubuntu.com/core/docs/bluez](https://ubuntu.com/core/docs/bluez)

{% embed url="https://ubuntu.com/core/docs/bluez" %}

## Murata Module&#x20;

The module is [Murata 1ZM](https://www.murata.com/products/connectivitymodule/wi-fi-bluetooth/overview/lineup/type1zm) using the NXP 88W8987 chipset.\
\
Type 1ZM is a small and very high performance module based on NXP 88W8987 combo chipset which supports Wi-Fi® 802.11a/b/g/n/ac + Bluetooth® 5.1 BR/EDR/LE up to 433Mbps PHY data rate on Wi-Fi® and 3Mbps PHY data rate on Bluetooth®. The WLAN section supports SDIO 3.0 interface and the Bluetooth® section supports high-speed 4-wire UART interface and PCM for audio data.

The 88W8987 implements highly sophisticated enhanced collaborative coexistence hardware mechanisms and algorithms, which ensure that WLAN and Bluetooth® collaboration is optimized for maximum performance.

In IEEE 802.11ac mode, the WLAN operation supports rates of MCS0 - MCS9 (up to 256 QAM) in 20MHz, 40MHz and 80MHz channels for data rate up to 433Mbps.

Type 1ZM module is packaged in an impressively small form factor that facilitates integration into size- and power-sensitive applications such as IoT applications, handheld wireless system, gateway and more.\
