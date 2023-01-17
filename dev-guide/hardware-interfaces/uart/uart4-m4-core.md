---
description: UART3 for users
---

# UART4 (M4 Core)

## Introduction

UART4 is available for general use. Hardware flow control is supported.

Note from the schematic clip below, that the MPU can multiplex these signals with SPI2. This is normally configured in the Linux image, and is not the default configuration.\


## UART4 interface voltage

The signaling from the SOM to the NavQPlus carrier board on J11 is at 3V3&#x20;

Alternative output is on the AUX connector at location J12 also at 3V3 signalling. However this is not the default linux BSP, and would require changes to the dtb files.\
\


### Schematic

Note that J11/UART4 is the default location for UART4 signals. Also by default UART4 is assigned to the M7 Core on the i.MX8M Plus. An RTOS such as FreeRTOS or Zephyr would normally use it as the default console to the embedded MCU.\
\
You may note that the signal names are differed on J11 vs J12. This is only a labelling detail, since the pinmuxing on the chip is used to "move" the UART4 interface from one set of pins on the MPU (and board to board header). In order to route these signals independently on the carrier board, they need their own net names.

<figure><img src="../../../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>

All the UART signals are protected from ESD using the Nexperia IP4292CZ components. This is part of an optimized BOM as they are also required for the USB interfaces. In additional to its exceptional performance the board layout may be optimized because of being able to route traces straight under the component. \


<figure><img src="../../../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (4).png" alt=""><figcaption><p>ESD Protection components on UARTS</p></figcaption></figure>

## Software

UART3 may be accessed as a standard `/dev/ttyS_` in Linux.\
\<TODO-check wich ttyS number it is>&#x20;



##
