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
