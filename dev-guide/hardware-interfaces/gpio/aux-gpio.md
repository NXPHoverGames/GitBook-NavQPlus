---
description: GPIO on the AUX connection
---

# AUX - GPIO

## Introduction

The AUX port contain is by default configured for I2C6 + GPIO. Alternative pinmuxing is available on AUX for UART4. Any alternative configurations are not default and need to be configured in the Linux Image and .dtb files

## AUX interface voltage

The signaling from the SOM to the NavQPlus carrier board on J12 is at 3V3&#x20;

Any alternative pinmuxed output configurations on the AUX connector would also be 3V3 signaling. \
\


## Aux Locator

<figure><img src="../../../.gitbook/assets/image (15).png" alt=""><figcaption></figcaption></figure>



## Schematic

### UART

Note that J11/UART4 is the default location for UART4 signals. Also by default UART4 is assigned to the M7 Core on the i.MX8M Plus. An RTOS such as FreeRTOS or Zephyr would normally use it as the default console to the embedded MCU.

### GPIO

J12 "AUX" is includes two pins for GPIO labelled GPT1\_CAPTURE1 and GPT2\_CAPTURE2

### &#x20;UART NetNames

You may note that the signal names are differed on J11 vs J12. This is only a labelling detail, since the pinmuxing on the chip is used to "move" the UART4 interface from one set of pins on the MPU (and board to board header). In order to route these signals independently on the carrier board, they need their own net names.

<figure><img src="../../../.gitbook/assets/image (12).png" alt=""><figcaption></figcaption></figure>

### ESD Protection

All the UART signals are protected from ESD using the Nexperia IP4292CZ components. This is part of an optimized BOM as they are also required for the USB interfaces. In additional to its exceptional performance the board layout may be optimized because of being able to route traces straight under the component. \


<figure><img src="../../../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (1).png" alt=""><figcaption><p>ESD Protection components on UARTS</p></figcaption></figure>

## Software

\<TODO- determine how to access these GPT pins in software>&#x20;



##
