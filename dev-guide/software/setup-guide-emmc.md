---
description: This is work in progress - derived from Gerald's notes
---

# Setup guide - eMMC

<\<ToDO - compare also with this [pre-existing link](https://nxp.gitbook.io/8mpnavq/navq+-user-guide/preprodution-quickstart-guide/flashing-with-new-firmware#flashing-the-emmc)   [https://nxp.gitbook.io/8mpnavq/navq+-user-guide/preprodution-quickstart-guide/flashing-with-new-firmware#flashing-the-emmc](https://nxp.gitbook.io/8mpnavq/navq+-user-guide/preprodution-quickstart-guide/flashing-with-new-firmware#flashing-the-emmc)>>

## Install ubuntu image &#x20;

The NavQplus firmware is preferably installed on eMMC for reliability reasons specifically when flying a drone. There is some potential for an SDCard to vibrate it's physical connections. However it may be convenient during development to use the SDCard \
\
Follow [https://iroboteducation.github.io/create3\_docs/setup/navqplus/](https://iroboteducation.github.io/create3\_docs/setup/navqplus/) \
(TODO: copy these instructions here.)

&#x20;

1. Download the [pre-built Ubuntu 20.04 with ROS2 Galactic image](https://github.com/rudislabs/navqplus-create3-images/releases), specifically designed for use with the Create® 3.[1](https://iroboteducation.github.io/create3\_docs/setup/navqplus/#fn:1)[3](https://iroboteducation.github.io/create3\_docs/setup/navqplus/#fn:3)&#x20;
2. Extract the image navqplus-image-\<version>.wic from the compressed downloaded file navqplus-image-\<version>.wic.bz2 and flash it to an [SD card](https://iroboteducation.github.io/create3\_docs/setup/navqplus/#flashing-the-sd-card) or the [EMMC](https://iroboteducation.github.io/create3\_docs/setup/navqplus/#flashing-the-emmc).&#x20;

## Flashing the eMMC&#x20;

To flash the eMMC on your NavQ+, you will need to download [UUU](https://github.com/NXPmicro/mfgtools/releases/tag/uuu\_1.4.193), a tool created by NXP to flash NXP boards. Make sure to download the correct application for your platform. The file titled "uuu" with no file extension is a binary file for use on x86/64 Linux.&#x20;

Once you have downloaded UUU, find the [boot switches](https://iroboteducation.github.io/create3\_docs/setup/navqplus/#boot-switches) on your NavQ+ and flip them to the "Flash" mode.&#x20;

Then, connect NavQ+ to your computer using the leftmost (USB 1) USB-C® port and the two flash status light should light up as shown in the image. &#x20;

![](<../../.gitbook/assets/image (5) (1).png>)

Run the following command to make sure that the NavQ+ is recognized by UUU:&#x20;

```
./uuu[.exe] -lsusb 
```

``<img src="../../.gitbook/assets/image (6).png" alt="" data-size="original">``

You should see that there is a device detected. If so, you can continue flashing. To flash your board, use the command below:&#x20;

```
.uuu[.exe] -b emmc_all navqplus-image-<version>.wic 
```

Once this process has finished, make sure that the flash was successful by comparing to the image below. If so, configure your [boot switches](https://iroboteducation.github.io/create3\_docs/setup/navqplus/#boot-switches) to boot from eMMC.&#x20;

## Boot Switches&#x20;

NavQ+ can be configured to boot from either SD card or eMMC. It also has a flash mode that allows you to flash either the eMMC or SD card over USB-C®. See the table below for the boot switch configuration.&#x20;

| Mode   | Switch1 | Swtich2 |
| ------ | ------- | ------- |
| SD     | ON      | ON      |
| eMMC   | OFF     | ON      |
| Flash  | ON      | OFF     |

## Log in for the first time&#x20;

Power on the NavQ+ by plugging in a USB-C® cable to the centermost (USB 2) USB-C® port. NavQ+ will boot, and you will be able to confirm it has fully booted by observing the LEDs on board. The 3 LEDs by the USB1 port should be on, as well as two LEDs next to the CAN bus connectors.&#x20;

To log into NavQ+, you can use the included USB to UART adapter, Ethernet, or USB-C® gadget mode (recommended). The default username/password combo is as follows:&#x20;

```
Username: user 
Password: user 
```



### Expand Image&#x20;

The flashed images will need expanding to utilize all the available storage. After logging into the NavQ+ open a terminal and run:&#x20;

* Expand image on the SD:&#x20;

{% code overflow="wrap" %}
```
echo -e "d\n2\nn\np\n2\n196608\n\n\nw" | sudo fdisk /dev/mmcblk1 && sudo resize2fs /dev/mmcblk1p2 
```
{% endcode %}



* Expand image on the eMMC:&#x20;

{% code overflow="wrap" %}
```
echo -e "d\n2\nn\np\n2\n196608\n\n\nw" | sudo fdisk /dev/mmcblk2 && sudo resize2fs /dev/mmcblk2p2 
```
{% endcode %}

### Remove unattended upgrades&#x20;

```
apt remove unattended-upgrades
```



### Install nano&#x20;

```
apt install nano
```

&#x20;

### Edit hostname&#x20;

Assuming you want to use the hostname "compcom42"

```
sudo nano /etc/hostname compcom42 
```

#### Change the hostname in hosts file&#x20;

{% hint style="warning" %}
(TODO - Clarify all the text below this point)
{% endhint %}

```
sudo nano /etc/hosts 

… 
127.0.1.1 compcom42 

Add the additional entries 



192.168.42.11   compcom<id> 
192.168.42.5    navq<id>-d2x 
192.168.42.2    t1eth8 
192.168.42.6    d2xmodem 
192.168.42.21   radar1 
192.168.42.22   radar2 
192.168.42.23   radar3 
```

#### Set static ip configuration&#x20;

Network manager is used for network config. See below&#x20;

&#x20;

#### Figure out the interface to be used &#x20;

```
nmcli con show 
```

From <[https://askubuntu.com/questions/246077/how-to-setup-a-static-ip-for-network-manager-in-virtual-box-on-ubuntu-server](https://askubuntu.com/questions/246077/how-to-setup-a-static-ip-for-network-manager-in-virtual-box-on-ubuntu-server)> &#x20;

&#x20;

#### Set static ip&#x20;

Wired connection 2 = 1000base-TX / eth1 \
Wired connection 1 = 100base-T1 / eth0&#x20;

```
nmcli con mod "Wired connection 2" 
  ipv4.addresses "192.168.42.11/24" 
  ipv4.gateway "IP_GATEWAY" (needs to be blank on static ip) 
  ipv4.dns "1.1.1.1,8.8.8.8" 
  ipv4.method "manual"  
```

From <[https://askubuntu.com/questions/246077/how-to-setup-a-static-ip-for-network-manager-in-virtual-box-on-ubuntu-server](https://askubuntu.com/questions/246077/how-to-setup-a-static-ip-for-network-manager-in-virtual-box-on-ubuntu-server)> &#x20;

### Install ROS&#x20;

_**ROS is already installed**_ on the [pre-built Ubuntu 20.04 with ROS2 Galactic image](https://github.com/rudislabs/navqplus-create3-images/releases)&#x20;

See [ROS2 installation script docs](https://onenote/#ROS2%20installation%20script%20docs\&section-id={7172739F-EEC8-4A2A-A5F8-FCA50716CC65}\&page-id={07109F1C-46AC-4EF5-AF42-327F26CCC296}\&end\&base-path=https://nxp1.sharepoint.com/sites/HoverGamesProgram/Shared%20Documents/Project%20-%20Drones4Bats/Drones4Bats/TechDocs.one)&#x20;

### Install VPN&#x20;

See [20220509 - Openvpn client user](onenote:Developments\VPN%20Client%20setup.one#20220509%20-%20Openvpn%20client%20user\&section-id={34009819-A55B-4195-A7A4-EB518C61E8D8}\&page-id={4518F3A6-DC0B-48FA-B1B2-04F502DBD87A}\&end\&base-path=https://nxp1.sharepoint.com/sites/HoverGamesProgram/Shared%20Documents/Project%20-%20Drones4Bats/Drones4Bats)&#x20;

(TODO - update VPN instructions above - external link)
