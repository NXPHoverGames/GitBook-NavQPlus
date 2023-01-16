---
description: Example of using the CAN bus
---

# CAN Bus

## Bringing up the CAN buses on NavQPlus

### CAN 2.0

```
sudo ip link set can0 up type can bitrate 125000
sudo ipl ink set can1 up type can bitrate 125000
```

### CAN-FD

```
sudo ip link set can0 up type can bitrate 500000 dbitrate 2000000 fd on
sudo ip link set can1 up type can bitrate 500000 dbitrate 2000000 fd on
```

There is an LED next to each CAN bus PHY on the board that will light up after running one of these commands.

These interfaces support the Linux SocketCAN library. \
Here is a good link showing some simple SocketCAN example code:

[https://www.beyondlogic.org/example-c-socketcan-code/](https://www.beyondlogic.org/example-c-socketcan-code/)

## Schematic

There are four CAN-FD connectors, they are connected "pass-through" style so that the bus may continue on, or a termination resistor network be plugged in.

* J21 and J22 are connected to CAN1 hardware signals (CAN0 logically in Software)
* J19 and J20 are connected to CAN2 hardware signals (CAN1 logically in software

![](<../../.gitbook/assets/image (7).png>)

![](<../../.gitbook/assets/image (8).png>)

![](../../.gitbook/assets/image.png)
