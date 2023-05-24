---
description: UART2 - A53 Debug
---

# UART2 (A53 Debug)

## Introduction

UART2 by default is the Debug or Console port into the main A53 processors running Linux on NavQPlus. It is possible to reassign its use by modifying the Linux configuration and .dtb files.&#x20;

## UART2 Locator

<figure><img src="../../../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>

## UART2 interface and voltage

The signaling from the SOM to the NavQPlus carrier board on J10 is at 3V3. Full handshaking with CTS RTS lines is provided:\


<figure><img src="../../../.gitbook/assets/image (7) (2).png" alt=""><figcaption></figcaption></figure>

## Console connection

Normal usage of UART2 is a console for bootup and Linux. The benefit of using the debug/console is that you can observe all details from powerup.

\
Details of the console connection including the Baud rate are provided under "Serial Console" in the Quickstart section of this gitbook. See the link below:

{% embed url="https://nxp.gitbook.io/8mpnavq/navqplus-user-guide/quickstart/serial-console" %}
