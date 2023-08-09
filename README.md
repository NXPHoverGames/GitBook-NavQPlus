---
description: >-
  A small form factor companion computer for mobile robotics applications,
  featuring the i.MX 8M Plus application processor, able to run Ubuntu Linux.
cover: .gitbook/assets/NavQPlus 20210930_162135.jpg
coverY: 0
---

# NavQPlus

{% hint style="success" %}
Also take a look at some of our other GitBooks:

* [NXP Mobile Robotics](http://127.0.0.1:5000/o/-L9GLsni4p7csCR7QCJ8/s/-M8v3AGPa-j5DtYx8zqd/): Quick reference and index for all our mobile robotics solutions.
* [HoverGames](http://127.0.0.1:5000/o/-L9GLsni4p7csCR7QCJ8/s/-L9GLtb-Tz\_XaKbQu-Al/): Drone & rover dev. kits, with FMUK66 vehicle management unit.&#x20;
* [NXP Cup](http://127.0.0.1:5000/o/-L9GLsni4p7csCR7QCJ8/s/-L9GLtaxrQtBdBRsFIJB/): Autonomous model car competition for students.
* [MR-CANHUBK3](http://127.0.0.1:5000/o/-L9GLsni4p7csCR7QCJ8/s/twBzyvivLuBKj9SMDwV9/): Small form factor CAN-FD to 100BASE-T1 ethernet bridge.
* [UCANS32K146](http://127.0.0.1:5000/o/-L9GLsni4p7csCR7QCJ8/s/-M7FJ\_hQKd8L0MNgduui/):  CAN-FD node for mobile robotics applications.
* [RDDRONE-BMS772](https://nxp.gitbook.io/rddrone-bms772/): Battery management system (3-6 cells).
* [RDDRONE-T1ADAPT](https://nxp.gitbook.io/rddrone-t1adapt): 100BASE-T1 ethernet adapter.
{% endhint %}

![](.gitbook/assets/navqplus\_image.jpg)

## Introduction

The 8MPNAVQ or "NavQPlus" is a small purpose-built Linux computer evaluation kit (EVK) based on the [NXP i.MX 8M Plus SoC](https://www.nxp.com/products/processors-and-microcontrollers/arm-processors/i-mx-applications-processors/i-mx-8-applications-processors/i-mx-8m-plus-arm-cortex-a53-machine-learning-vision-multimedia-and-industrial-iot:IMX8MPLUS). It is focused on the common needs of mobile robotics systems, with a small form factor, [Dronecode](https://www.dronecode.org/)-compliant JST-GH connectors, and available software stack including Ubuntu Linux and [ROS2](https://ros.org/).

The entire design is available for companies building their own similar hardware. NavQPlus is built as a stack of boards, the top board being a SoM (System-on-Module) containing the processor, memory and other components with strict layout requirements, and where the secondary boards are relatively inexpensive (often 4 layer boards) and allows for versions with customization to be easily built.

Note that the SoM is almost identical to the larger [NXP EVK for i.MX8M Plus](https://www.nxp.com/design/development-boards/i-mx-evaluation-and-development-boards/evaluation-kit-for-the-i-mx-8m-plus-applications-processor:8MPLUSLPD4-EVK) with the exception of the I/O voltage level being changed to 3.3V. This makes NavQPlus an excellent stepping stone or bridge from the large EVK to a system that can be duplicated for testing _in situ_, or even copied directly for your application.

### Experimental nature

Because NavQPlus is experimental and contains a new set of boards and peripherals, please expect and plan for software enablement to undergo several iterations. Our intent is to provide an Ubuntu PoC (Proof of Concept) "user-friendly Linux" with typical packages and additional tools included, rather than the traditional Yocto-based distribution that is typical of the highly optimized and stripped down Linux operating systems used in deeply embedded products. Since this Ubuntu PoC is also built on top of Yocto, it is still able to be reduced and optimized for full commercial deployment as well.

### Ubuntu PoC

It should be noted that Ubuntu PoC is NOT supported by Canonical. They are however available on a contractual basis to provide commercial support for Ubuntu on NXP processors.

## Features

1. NXP i.MX 8M Plus SoC on a SoM with LPDDR4 DRAM and eMMC flash.
   * 4x Arm Cortex-A53 core
   * 1x Arm Cortex-M7 core
   * 1x Neural Processing Unit (2.3 TOPS)
   * 1080p60 H.265/H.264 encoder
   * Dual Camera Image Signal Processor (HDR, Dewarp)
2. A secondary board with connectors to hardware interfaces, such as:
   * Dual MIPI-CSI camera interfaces
   * Two CAN-FD interfaces
   * I2C, SPI, UART, GPIO
   * SD card slot
   * 2.4/5GHz WiFi and Bluetooth 5.0 using [NXP 88W8987](https://www.nxp.com/products/wireless/wi-fi-plus-bluetooth-plus-802-15-4/2-4-5-ghz-dual-band-1x1-wi-fi-5-802-11ac-plus-bluetooth-5-2-solution:88W8987)-based [Murata Type 1ZM module](https://www.murata.com/products/connectivitymodule/wi-fi-bluetooth/overview/lineup/type1zm)
   * Micro-HDMI, MIPI-DSI, and LVDS for displays
   * USB-C, including power input & output
   * 1 Gigabit Ethernet with ix Industrial connector
   * JTAG BOOT

### Block Diagram

<figure><img src=".gitbook/assets/1279000-CS_Nav Q Plus_BD_2048x1152_blue.jpg" alt=""><figcaption><p>NavQPlus Block Diagram</p></figcaption></figure>

## Applications

The NavQPlus is suitable for many purposes, including generic robots, various vision systems, and AI/ML applications.

* Unmanned Aerial Vehicles (UAVs)
  * Such as multicopters and VTOL (Vertical Take-off and Landing) aircraft
* Rovers and other unmanned ground vehicles (UGVs)
  * Road-going Delivery Vehicles
  * Robotic Lawn Mowers
  * Robotic Vacuum Cleaners
* Marine Vessels
* Camera and Vision Processing Modules
* Time-of-Flight (ToF) Cameras
* AI/ML Inference
* Cellular Gateway
* Vision systems in other applications
  * e.g. a hospital bed monitor that detects if a patient is sitting up or at risk of falling out of bed.

Two specific complete developer tool examples are the [NXP HoverGames drone](http://127.0.0.1:5000/o/-L9GLsni4p7csCR7QCJ8/s/-L9GLtb-Tz\_XaKbQu-Al/), and the [NXP Cup car](http://127.0.0.1:5000/o/-L9GLsni4p7csCR7QCJ8/s/-L9GLtaxrQtBdBRsFIJB/).

## Software

The intent of the 8MPNavQ in HoverGames is to enable participants with a solution that allows them to harness common robotics packages and libraries such as:

* ROS/ROS2
* OpenCV
* GStreamer
* pyeIQ
  * TensorFlow/TFLite
  * PyTorch
  * Arm NN
  * etc.
* And more!

The 8MPNavQ runs Linux with a package manager, so you should be able to install the packages that you need to complete your projects successfully and efficiently.

## Feedback

{% hint style="info" %}
We are making a continuous effort to improve this GitBook, some pages and sections may still be a work in progress. Your input and feedback is very welcome. You may provide feedback in our [Discord channel](https://discord.com/channels/1014291298812960913/1027691375770218638) (to access the channel you must first [join the Hackster.io Discord server](https://discord.gg/g6aSSak9NV)). Alternatively, you can open an issue or pull request to the [GitHub repository](https://github.com/NXPHoverGames/GitBook-NavQPlus) that mirrors this GitBook.
{% endhint %}
