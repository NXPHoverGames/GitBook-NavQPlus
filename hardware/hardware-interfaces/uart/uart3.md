---
description: UART3 for users
---

# UART3 (SPI)

## Introduction

UART3 is available for general use. Hardware flow control is supported.

Note from the schematic clip below, that the MPU can multiplex these signals with SPI1. This is normally configured in the Linux image and is not the default configuration.

## UART3 Interface voltage

The signaling from the SOM to the NavQPlus carrier board on J9 is at 3V3 but the Murata 1ZM expects 1.8V. The level conversion is done using U26.

## UART3 Locator

<figure><img src="../../../.gitbook/assets/image (4) (1).png" alt=""><figcaption><p>UART3</p></figcaption></figure>

## Schematic

<figure><img src="../../../.gitbook/assets/image (14) (1).png" alt=""><figcaption><p>UART3/ SPI 1 interface on J9</p></figcaption></figure>

All the UART signals are protected from ESD using the Nexperia IP4292CZ components. This is part of an optimized BOM as they are also required for the USB interfaces. In additional to its exceptional performance the board layout may be optimized because of being able to route traces straight under the component. \


<figure><img src="../../../.gitbook/assets/image (2) (3).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (1) (3).png" alt=""><figcaption><p>ESD Protection components on UARTS</p></figcaption></figure>

## Software

~~UART3 may be accessed as a standard `/dev/ttyS_` in Linux.~~\
UART3 may be accessed /dav/ttymxc2 in linux\
\<TODO-check wich ttyS number it is>&#x20;



##
