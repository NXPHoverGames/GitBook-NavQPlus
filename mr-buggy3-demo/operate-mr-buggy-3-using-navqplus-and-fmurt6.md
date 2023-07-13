---
description: 07/2023
---

# Operate MR-Buggy 3 using NavQPlus and FMURT6

## Introduction

This tutorial describes how to operate [MR-Buggy 3](https://nxp.gitbook.io/nxp-cup/mr-buggy3-developer-guide-2022/getting-started) with [Logitech Joystick](https://www.logitechg.com/en-in/products/gamepads/f310-gamepad.940-000112.html?searchclick=logi) using [NavQPlus](https://nxp.gitbook.io/8mpnavq/) and [FMURT6](https://www.nxp.com/part/RDDRONE-FMURT6#/).&#x20;

The [synapse](https://github.com/CogniPilot?q=synapse\&type=all\&language=\&sort=) packages from  [CogniPilot](https://github.com/CogniPilot) are built on NavQPlus which will read input from the Joystick and send the appropriate commands to FMURT6 over ethernet.

The [mrbuggy](https://github.com/CogniPilot/cerebri/tree/main/app/mrbuggy3) application in [CogniPilot/cerebri](https://github.com/CogniPilot/cerebri/tree/main) running on FMURT6 takes commands from NavQPlus and sends operation signals to MR-Buggy 3 servo and motor controller.

## Items Needed

<table><thead><tr><th align="center">S. No.</th><th width="484">NAME</th><th align="center">QUANTITY</th></tr></thead><tbody><tr><td align="center">1</td><td><a href="https://www.nxp.com/part/RDDRONE-FMURT6#/">RDDRONE-FMURT6</a></td><td align="center">1</td></tr><tr><td align="center">2</td><td><a href="https://holybro.com/products/pixhawk-debug-adapter">Pixhawk Debug Adapter</a></td><td align="center">1</td></tr><tr><td align="center">3</td><td><a href="https://www.segger.com/products/debug-probes/j-link/models/j-link-edu-mini/">J-Link EDU Mini</a></td><td align="center">1</td></tr><tr><td align="center">4</td><td><a href="https://www.pcboard.ca/jst-sh-10-pin-cable">JST SH 10-Pin Cable</a></td><td align="center">1</td></tr><tr><td align="center">5</td><td><a href="https://www.apple.com/shop/product/HN892ZM/A/mophie-usb-a-cable-with-usb-c-connector-1-m">USB-C (Male) to USB-A (Male) Cable</a></td><td align="center">4</td></tr><tr><td align="center">6</td><td><a href="https://in.rsdelivers.com/product/rs-pro/rs-pro-usb-20-cable-male-usb-a-to-male-micro-usb-b/1828498">Micro-USB (Male) to USB-A (Male) Cable</a></td><td align="center">1</td></tr><tr><td align="center">7</td><td><a href="https://www.adafruit.com/product/1675">.05" 10-Pin Ribbon Cable</a></td><td align="center">1</td></tr><tr><td align="center">8</td><td><a href="https://nxp.gitbook.io/nxp-cup/mr-buggy3-developer-guide-2022/getting-started">MR-Buggy 3 Kit</a></td><td align="center">1</td></tr><tr><td align="center">9</td><td><a href="https://www.logitechg.com/en-in/products/gamepads/f310-gamepad.940-000112.html?searchclick=logi">Logitech G F310</a></td><td align="center">1</td></tr><tr><td align="center">10</td><td><a href="https://www.apple.com/in/shop/product/MJ1M2ZM/A/usb-c-to-usb-adapter">USB-A (Female) to USB-C (Male) Adaptor</a></td><td align="center">1</td></tr><tr><td align="center">11</td><td><a href="https://nxp.gitbook.io/8mpnavq/">NavQPlus</a></td><td align="center">1</td></tr><tr><td align="center">12</td><td><a href="https://thinklucid.com/product/ix-industrial-ethernet-cat6a-cable-2-0m-black/">Cat6a (Male) ix Industrial to RJ45 (Male) Ethernet Cable</a></td><td align="center">1</td></tr><tr><td align="center">13</td><td>USB-UART serial debugger</td><td align="center">1</td></tr><tr><td align="center">14</td><td><a href="https://www.keysight.com/in/en/support/E3648A/100w-dual-output-power-supply-two-8v-5a-20v-2-5a.html">E3648A 100W Dual Output Power Supply</a></td><td align="center">1</td></tr><tr><td align="center">15</td><td><a href="https://dronescout.co/product/jst-gh-2-pin-1-25-mm-cable-15-cm/">JST GH 1.25mm Pitch 2 Pin Cable</a> (Female to Female)</td><td align="center">1</td></tr><tr><td align="center">16</td><td><a href="https://www.adafruit.com/product/5754">JST GH 1.25mm Pitch 6 Pin Cable</a> (Female to Female)</td><td align="center">1</td></tr></tbody></table>

## Hardware Procedure

<figure><img src="../.gitbook/assets/block_diagram (4).svg" alt=""><figcaption><p>Block Diagram of the Complete Hardware Setup</p></figcaption></figure>

<figure><img src="../.gitbook/assets/2023-07-07 13.37.51 (1).jpg" alt=""><figcaption><p>RDDRONE-FMURT6</p></figcaption></figure>

<figure><img src="../.gitbook/assets/2023-07-07 13.36.58 (1).jpg" alt=""><figcaption><p>NavQPlus</p></figcaption></figure>

<figure><img src="../.gitbook/assets/2023-07-07 14.38.47 (1).jpg" alt=""><figcaption><p>USB-UART Serial Debugger</p></figcaption></figure>

<figure><img src="../.gitbook/assets/2023-07-07 14.40.11.jpg" alt=""><figcaption><p>Pixhawk Debug Adaptor and J-Link EDU Mini</p></figcaption></figure>

#### Power Supply Setup

1. Press "Power" Button.
2. Press "Output On/Off" Button.
3. Select "Voltage" from "Voltage/Current" Button.
4. Set the Voltage to 7.4 V from the "Tuning Nob."
5. Connect the output wires to XT60 M1 on buggy.

<figure><img src="../.gitbook/assets/2023-07-07 14.34.52.jpg" alt=""><figcaption><p>E3648A 100W Dual Output Power Supply</p></figcaption></figure>

## FMURT6 Software Procedure (on host machine)

#### Prerequisites

1. Unrestricted network connection
2. [Ubuntu 22.04](https://releases.ubuntu.com/jammy/) on native machine
3. Setup ssh keys

```
sudo apt update
sudo apt upgrade

sudo apt install git
```

#### Software Setup

```
mkdir -p ~/git/cognipilot/
cd ~/git/cognipilot/
git clone git@github.com:CogniPilot/helmet.git
cd helmet
./scripts/install.sh -f dream/mrbuggy3.yaml
```

{% hint style="info" %}
Type "y" + "enter" when required.
{% endhint %}

```
source ~/.bashrc
source ~/.profile
```

#### Building and Flashing

```
cd ~/git/cognipilot/ws/cerebri/app/mrbuggy3
west build -b mimxrt1062_fmurt6 -p
```

{% hint style="info" %}
Download and install Jlink from: [https://www.segger.com/downloads/jlink/](https://www.segger.com/downloads/jlink/)
{% endhint %}

```
west flash
```

{% hint style="warning" %}
If you get an error with "west flash," make sure J-Link EDU Mini is directly connected to your machine. If that doesn't work then unplug and re-plug the FMURT6 board.
{% endhint %}

## NavQPlus Software Procedure (on navq+ board)

#### Prerequisites

1. [Ubuntu 22.04.3 Humble Image](https://github.com/rudislabs/navqplus-create3-images/releases/tag/v22.04.3)
2. Unrestricted network connection
3. Setup ssh keys

{% hint style="info" %}
NavQ+ requires internet connection for the following setup. If an ethernet connection is not available, connect the board to the native ubuntu machine via ethernet and [create a network bridge from wifi to ethernet on your machine](https://amigotechnotes.wordpress.com/2019/01/25/share-usb-tethering-to-wifi-and-ethernet-devices/).&#x20;
{% endhint %}

#### Accessing Shell&#x20;

```
minicom -D /dev/<device_name> -b 115200
```

{% hint style="info" %}
username=user

password=user
{% endhint %}

#### Software Setup

```
sudo apt update
sudo apt upgrade
sudo apt install ros-humble-actuator-msgs

mkdir -p ~/git/cognipilot/src
cd ~/git/cognipilot/src
git clone git@github.com:CogniPilot/synapse_ros.git
git clone git@github.com:CogniPilot/synapse_msgs.git
git clone git@github.com:CogniPilot/synapse_protobuf.git
git clone git@github.com:CogniPilot/synapse_tinyframe.git

cd ~/git/cognipilot
colcon build --symlink-install
```

{% hint style="warning" %}
Comment out both the interfaces listed in \~/CycloneDDSConfig.xml;
{% endhint %}

#### Network Setup

````
sudo vi ~/.net.sh

``` (Add the following lines in ~/.net.sh)
#!/bin/bash
sudo ethtool -s eth0 master-slave forced-slave
sudo ifconfig eth0 192.0.2.2 netmask 255.255.255.0
```
````

{% code fullWidth="false" %}
```
echo "bash /home/$USER/.net.sh" >> ~/.bashrc
source ~/.bashrc
```
{% endcode %}

## Running and Demonstration

#### Execution on NavQPlus

{% hint style="info" %}
Since, ros2 commands block the shell, we will need two shells for the following.
{% endhint %}

```
ros2 run joy joy_node --ros-args -r /joy:=/cerebri/in/joy

cd ~/git/cognipilot/install
source setup.bash
ros2 launch synapse_ros synapse_ros.launch.py
```

{% hint style="warning" %}
If the TCP connection fails, reset FMURT6.
{% endhint %}

#### Operation from Joystick

<figure><img src="../.gitbook/assets/image (32).png" alt=""><figcaption><p>Logitech Joystick G F310 Button Mapping</p></figcaption></figure>

1. Set the Joystick to X-Input Mode (from the switch behind the controller).
2. Press the mode button such that the green light next to it is turned on.
3. Press green button A (0) to select manual mode.
4. Press start button (7) to arm in the selected mode.
5. Use vertical d-pad axis (1) for acceleration/reverse.
6. Use horizontal right-stick axis (3) for steering.
7. All controls: joy axes 1 is throttle, joy axes 3 is yaw/steering, button 7 is arm, button 6 is disarm, button 1 is mode manual, button 1 is mode auto, button 2 is mode cmd\_vel.
