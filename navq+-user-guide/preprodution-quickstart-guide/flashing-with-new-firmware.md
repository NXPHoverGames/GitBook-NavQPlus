# Flashing with new firmware

When new images are released, we will provide a link to them. To flash NavQPlus, normally there are two options. You can either flash the eMMC chip on-board, or flash the SD card included with the kit. The eMMC runs faster, but is not removable like the SD card. The SD card is easily removeable and can be programmed quickly and directly from a PC. It is up to you to choose which one to use. \
\
<<\<TODO - LINK to Downloadable pre-compiled images>>>

See below for instructions on how to flash the SD card or eMMC on NavQPlus.

## Flashing the SD card

The NavQPlus typically comes with a 16GB SD card or larger that you can flash with the pre-built Ubuntu 20.04 image. See below for instructions to flash your SD card on each platform.

{% hint style="info" %}
You must have an SD card reader available on your system to perform these instructions.
{% endhint %}

### Flashing using Windows PC

To flash your SD card with the image you downloaded there are a number of programs to do this, we tend to use [Win32DiskImager](https://win32diskimager.org/).

Once you have downloaded Win32DiskImager, insert your SD card into your computer, open the program, and select the `navqplus-image-{vX.X}.wic` file as your image.

Next, select your SD card under Device.

{% hint style="danger" %}
Make sure that your Device selection is the correct drive letter for your SD card. Don't erase your hard drive! Only click "Write" after double checking for the correct drive letter!
{% endhint %}

Once the flashing process has finished, you should get a message saying that the write was successful.

### Flashing using Linux / Mac

To flash your SD card with the image you downloaded in step 1, we suggest using `dd`.

To do this, open a terminal and navigate to the folder that you downloaded the `navqplus-image-{vX.X}.wic` file.

Once you are there, insert your SD card, and find the device path for it. Typically, it will be something like `/dev/sdX` on Linux or `/dev/diskX` on Mac.

{% hint style="danger" %}
Be careful that you select the correct drive path when using dd to flash your SD card. You can confirm with the "Disks" app on Ubuntu or the "Disk Utility" app on Mac.
{% endhint %}

Once you have found your device path, run the following command in your terminal to flash the SD card:

#### Linux:

$ sudo dd if=navqplus-image-{vX.X}.wic of=/dev/sdX bs=1M status=progress oflag=sync

```markup
$ sudo dd if=navqplus-image-{vX.X}.wic of=/dev/sdX bs=1M status=progress oflag=sync
```

#### Mac:

```
$ sudo dd if=navqplus-image-{vX.X}.wic of=/dev/diskX bs=1m status=progress oflag=sync
```

Once this is done, your SD card will be flashed with the image.&#x20;

#### Set Boot Switches for SD Card Boot

If you have changed them, remember to make sure that your [boot switches](flashing-with-new-firmware.md#boot-switches) are set to boot from SD.

## Flashing the eMMC

To flash the eMMC on your NavQPlus, you will need to download [UUU](https://github.com/NXPmicro/mfgtools/releases/tag/uuu\_1.4.193), a tool created by NXP to flash NXP boards. Make sure to download the correct application for your platform. The file titled "uuu" with no file extension is a binary file for use on x86/64 Linux.

Once you have downloaded UUU, find the [boot switches](flashing-with-new-firmware.md#boot-switches) on your NavQ+ and flip them to the "Flash" mode.

Then, connect NavQ+ to your computer using the centermost USB-C® port. Run the following command to make sure that the NavQ+ is recognized by UUU:

```
$ ./uuu[.exe] -lsusb
```

**TODO: Add image**

You should see that there is a device detected. If so, you can continue flashing. To flash your board, use the command below:

```
$ ./uuu[.exe] -b emmc_all navqplus-image-{vX.X}.bin-flash_evk navqplus-image-{vX.X}.wic
```

Once this process has finished, make sure that the flash was successfull by comparing to the image below. If so, configure your [boot switches](flashing-with-new-firmware.md#boot-switches) to boot from eMMC.

**TODO: Add image**

## Boot Switches Configuration

(This table is referenced from several places in this gitbook)\
NavQPlus can be configured to boot from either SD card or eMMC. It also has a flash mode that allows you to flash either the eMMC or SD card over USB-C®. \
\
See the table below for the boot switch configuration.

| Mode  | Switch 1 | Switch 2 |
| ----- | -------- | -------- |
| SD    | ON       | ON       |
| eMMC  | OFF      | ON       |
| Flash | ON       | OFF      |
