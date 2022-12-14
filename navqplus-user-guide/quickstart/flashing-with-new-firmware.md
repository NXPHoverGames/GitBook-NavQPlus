---
description: Changing the NavQPlus firmware and booting from SD Card or EMMC flash
---

# Flashing new firmware

## Introduction

When new images are released, we will provide a link to them. To flash NavQPlus, normally there are two options. You can either flash the eMMC chip on-board, or flash the SD card included with the kit. The eMMC runs faster, but is not removable like the SD card. The SD card is easily removeable and can be programmed quickly and directly from a PC. It is up to you to choose which one to use.&#x20;

### Images

Here are links to images that can be downloaded and used on the NavQPlus. \
See below for instructions on how to flash the SD card or eMMC.\
\
<<\<TODO - LINK to Downloadable pre-compiled images>>>



## Flashing image to an SDCard

The NavQPlus typically comes with a 16GB SD card or larger that you can flash with the pre-built Ubuntu 20.04 image. See below for instructions to flash your SD card on each platform.

{% hint style="info" %}
You must have an SD card reader available on your system to perform these instructions. Low cost USB dongles or hubs with SD Card slots are available.
{% endhint %}

### Flashing SD card using Windows PC

Several free programs are available to flash an SD card with an image, we use [Win32DiskImager](https://win32diskimager.org/).

Once you have downloaded Win32DiskImager, insert your SD card into your computer, open the program, and select the `navqplus-image-{vX.X}.wic` file as your image.

Next, select your SD card under Device.

{% hint style="danger" %}
Make CERTAIN that your Device selection is the correct drive letter for your SD card!!! You don't want to erase your hard drive! \
Only click "Write" after double checking for the correct drive letter!
{% endhint %}

Once the flashing process has finished, you should get a message saying that the write was successful.

### Flashing SD card using Linux / Mac

To flash your SD card with the image you downloaded in step 1, we suggest using `dd`.

To do this, open a terminal and navigate to the folder that you downloaded the

&#x20;`navqplus-image-{vX.X}.wic` file.

Once you are there, insert your SD card, and find the device path for it. Typically, it will be something like `/dev/sdX` on Linux or `/dev/diskX` on Mac.

{% hint style="danger" %}
Be VERY careful that you select the correct drive path when using dd to flash your SD card. You can confirm with the "Disks" app on Ubuntu or the "Disk Utility" app on Mac.
{% endhint %}

Once you have found your device path, run the following command in your terminal to flash the SD card:

#### Linux:

```markup
sudo dd if=navqplus-image-{vX.X}.wic of=/dev/sdX bs=1M status=progress oflag=sync
```

#### Mac:

```
sudo dd if=navqplus-image-{vX.X}.wic of=/dev/diskX bs=1m status=progress oflag=sync
```

Once this is done, your SD card will be flashed with the image.&#x20;

#### Set Boot Switches for SD Card Boot

* Remember to check that your [boot switches](flashing-with-new-firmware.md#boot-switches) are set to boot from SD.

## uuu Flashing the eMMC

To flash the eMMC on your NavQPlus, you will need to download [uuu](https://github.com/NXPmicro/mfgtools/releases), a tool created by NXP to flash NXP boards. Make sure to download the correct application for your platform. The file titled "uuu" with no file extension is a binary file for use on x86/64 Linux.

* After downloading uuu, find the [boot switches](flashing-with-new-firmware.md#boot-switches) on your NavQ+ and flip them to the "Flash" mode.
* Connect NavQ+ to your computer using the centermost USB-C port.&#x20;
* Run the following command to make sure that the NavQ+ is recognized by uuu:

```
./uuu[.exe] -lsusb
```

**\<TODO: Add image of output>**

* You should see that there is a device detected. If so, you can continue flashing. \
  \
  To flash your board, use one of the commands below depending on how the image was supplied:\


{% hint style="info" %}
When flashing the EMMC an additional .bin file is needed in addition to the .wic file. Recently [**the latest** uuu (as of 1.4.243](https://github.com/NXPmicro/mfgtools/releases/tag/uuu\_1.4.243)) was upgraded so these two files can now be included in a single zip, and used without uncompressing. You may be supplied the .zip or the two separate files.&#x20;
{% endhint %}

#### &#x20;EMMC image supplied in .zip format then:

```
sudo ./uuu navqplus-image-{vX.X}_.zip
```

#### EMMC image supplied as  .bin and  .wic files:

```
sudo ./uuu[.exe] -b emmc_all navqplus-image-{vX.X}.bin -flash_evk navqplus-image-{vX.X}.wic
```

{% hint style="success" %}
The SDCARD image also has a .wic file extension, so be sure you are using the correct file! You cannot flash this to EMMC without the corresponding .bin file, but you can use the EMMC .wic file to program an SDCARD. it is the same image
{% endhint %}

* Once this process has finished, make sure that the flash was successful by comparing to the image below. If so, configure your [boot switches](flashing-with-new-firmware.md#boot-switches) to boot from eMMC.

**TODO: Add image**

## Boot Switches Configuration

NavQPlus can be configured to boot from either SD card or eMMC. It also has a flash mode that allows you to flash either the eMMC or SD card over USB-C®. \
\
See the table below for the boot switch configuration.

| Mode  | Switch 1 | Switch 2 |
| ----- | -------- | -------- |
| SD    | ON       | ON       |
| eMMC  | OFF      | ON       |
| Flash | ON       | OFF      |

{% hint style="info" %}
(NOTE: This boot switch table is referenced from several locations in this gitbook)
{% endhint %}
