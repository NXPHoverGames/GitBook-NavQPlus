---
description: This is work in progress - derived from Gerald's notes
---

# Setup guide - eMMC (DRAFT)

<\<ToDO - compare also with this [pre-existing link](https://nxp.gitbook.io/8mpnavq/navq+-user-guide/preprodution-quickstart-guide/flashing-with-new-firmware#flashing-the-emmc)   [https://nxp.gitbook.io/8mpnavq/navq+-user-guide/preprodution-quickstart-guide/flashing-with-new-firmware#flashing-the-emmc](https://nxp.gitbook.io/8mpnavq/navq+-user-guide/preprodution-quickstart-guide/flashing-with-new-firmware#flashing-the-emmc)>>

## Install ubuntu image &#x20;

The NavQplus firmware is preferably installed on eMMC for reliability reasons specifically when flying a drone. There is some potential for an SD card to vibrate it's physical connections. However it may be convenient during development to use the SD card \
\
Follow https://iroboteducation.github.io/create3\_docs/setup/navqplus/ \
(TODO: copy these instructions here.)

{% hint style="danger" %}
\<TODO> Fix these instructions to match the other website (missing step 3, 4, 5)

UPDATE IMAGE
{% endhint %}

1.  Download the [pre-built Ubuntu 20.04 with ROS2 Galactic image](https://github.com/rudislabs/navqplus-create3-images/releases), specifically designed for use with the Create® 3.[1](https://iroboteducation.github.io/create3\_docs/setup/navqplus/#fn:1)[3](https://iroboteducation.github.io/create3\_docs/setup/navqplus/#fn:3) \
    <<\<TODO - Create permanent link which includes latest builds.>>>

    <<\<TODO - TEMPORARY LINK to latest image>>>\
    [https://github.com/rudislabs/navqplus-create3-images/releases/](https://github.com/rudislabs/navqplus-create3-images/releases/)
2. Extract the image navqplus-image-\<version>.wic from the compressed downloaded file navqplus-image-\<version>.wic.bz2 and flash it to an [SD card](https://iroboteducation.github.io/create3\_docs/setup/navqplus/#flashing-the-sd-card) or the [EMMC](https://iroboteducation.github.io/create3\_docs/setup/navqplus/#flashing-the-emmc).&#x20;

{% embed url="https://github.com/rudislabs/navqplus-create3-images/releases/" %}



## Flashing the eMMC&#x20;

To flash the eMMC on your NavQ+, you will need to download [UUU](https://github.com/NXPmicro/mfgtools/releases/tag/uuu\_1.4.193), a tool created by NXP to flash NXP boards. Make sure to download the correct application for your platform. The file titled "uuu" with no file extension is a binary file for use on x86/64 Linux.&#x20;

Once you have downloaded UUU, find the [boot switches](setup-guide-emmc.md#boot-switches) on your NavQ+ and flip them to the "Flash" mode.&#x20;

Then, connect the NavQ+ to your computer using the leftmost (USB 1) USB-C® port and the two flash status light should light up as shown in the image. &#x20;

<figure><img src="../../.gitbook/assets/image (9).png" alt=""><figcaption></figcaption></figure>

Run the following command to make sure that the NavQ+ is recognized by UUU:&#x20;

```
./uuu[.exe] -lsusb 
```

<figure><img src="../../.gitbook/assets/image (5).png" alt=""><figcaption></figcaption></figure>

You should see that there is a device detected. If so, you can continue flashing. To flash your board, use the command below:&#x20;

```
.uuu[.exe] -b emmc_all navqplus-image-<version>.wic 
```

Once this process has finished, make sure that the flash was successful by comparing to the image below. If so, configure your [boot switches](setup-guide-emmc.md#boot-switches) to boot from eMMC.&#x20;

<figure><img src="../../.gitbook/assets/image (11).png" alt=""><figcaption></figcaption></figure>

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

### USB to UART adapter

Connect the included USB to UART adapter to the UART2 port on the NavQPlus, and open your favorite serial console application. Open a serial console with a baud rate of 115200. Press enter if there is no output on the screen to get a log-in prompt.

<figure><img src="../../.gitbook/assets/MicrosoftTeams-image.png" alt=""><figcaption></figcaption></figure>

### Ethernet <a href="#ethernet" id="ethernet"></a>

Connect the included IX Industrial Ethernet cable to NavQPlus, and connect the RJ45 connector to your computer, switch, or router on your local network. You can log into NavQPlus over SSH. The default hostname for NavQPlus is imx8mpnavq. To SSH into NavQPlus, you can run the following command:

```
ssh user@imx8mpnavq.local
```

### USB-C® Gadget Ethernet <a href="#usb-c-gadget-ethernet" id="usb-c-gadget-ethernet"></a>

The IP address of the `usb0` network interface on NavQPlus is statically assigned to 192.168.186.3. If you want to use USB-C® gadget ethernet to connect to NavQPlus, you will need to assign a static IP to your existing gadget ethernet interface on your computer.&#x20;

First go to your network settings and click on the plus icon on the top right.

<figure><img src="../../.gitbook/assets/image (10).png" alt=""><figcaption></figcaption></figure>

The network configuration is as follows:

**IP Address:** 192.168.186.2

**Network Mask:** 255.255.255.0

![Network Manager connection profile.](https://iroboteducation.github.io/create3\_docs/setup/data/navqplus/usb\_network.png)

Once you have set up your USB-C® gadget ethernet interface on your computer, you can SSH by running:

```
ssh user@imx8mpnavq.local
```

## Expand Image&#x20;

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

## Configuring WiFi, System Username and Password <a href="#configuring-wifi-system-username-and-password" id="configuring-wifi-system-username-and-password"></a>

### Configuring WiFi on NavQPlus <a href="#configuring-wifi-on-navqplus" id="configuring-wifi-on-navqplus"></a>

To connect NavQPlus to your local WiFi network, you can use the `nmtui` command. This command presents a GUI in your terminal to connect to WiFi. The interface is relatively straightforward. To run `nmtui`, run the following command:

```
sudo nmtui
```

For a non-GUI way to connect to WiFi or manage your network connections, use `nmcli` by running the following command:

```
sudo nmcli device wifi connect <network_name> password "<password>"
```

Once you are finished connecting to your local WiFi network, you can exit the application. Your NavQPlus will continue to connect to this WiFi network even after a reboot.

### Configuring System Username and Password <a href="#configuring-system-username-and-password" id="configuring-system-username-and-password"></a>

To change the default username and password, use the commands below.

Username:

```
usermod -l <new_username> user
mv /home/user /home/<new_username>
```

Password:

```
passwd
```

