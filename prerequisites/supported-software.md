---
description: Software available for NavQPlus
---

# Supported Software

## NavQPlus Enablement

NavQPlus has specific enablement that is not typically found in generic EVK's from NXP. [The Ubunti POC](ubuntu-proof-of-concept-ubuntu-poc.md) , [ROS2 ](https://www.ros.org/)and other software has been enabled in order to work with robotics development systems.&#x20;

While our team may have used and tested tthis software, the enablement is under continual development and is expected to change regularly. Where this software is application level (I.e ROS2), and not hardware device level (i.e Gstreamer) you should look for community support for that application and not directly from NXP \
\
Elsewhere in this "engineering notebook" gitbook you will find guidance on how some of this software may be used. Specific sofware used in these examples will be noted.

### OS/Software

Example NavQPlus typical OS images may include the following. (note that this configuration may have already been updated/upgraded to newer versions.)

* NXP Yocto Linux 5.15 kernel
  * Gstreamer
  * eIQ AI/ML tools
  * Ethernet over USB-C Gadget mode (SSH connection to laptop using USB cable)
* Ubuntu 22.04 built on top of NXP Yocto 5.15
  * ROS2 Humble enabled

\


## Yocto Linux

NXP i.MX 8M Plus linux is a Yocto build. Refer to the NXP GIT repo and NXP documentation when building from source.\


[https://www.nxp.com/docs/en/user-guide/IMX\_YOCTO\_PROJECT\_USERS\_GUIDE.pdf](https://www.nxp.com/docs/en/user-guide/IMX\_YOCTO\_PROJECT\_USERS\_GUIDE.pdf)

{% embed url="https://www.nxp.com/design/software/embedded-software/nxp-github:NXP-GITHUB/" %}

{% embed url="https://github.com/nxp-imx/meta-imx" %}

### Other NXP EVK software

NavQPlus is a derivative of the NXP EVK. Refer to the NXP website for the complete variety of software support for i.MX 8M Plus

{% embed url="https://www.nxp.com/search?keyword=i.MX%25208M%2520Plus&start=0&category=software" %}

{% embed url="https://www.nxp.com/design/software/embedded-software/nxp-github:NXP-GITHUB" %}



### Complete overview

For a complete view of all the software available for i.MX 8M Plus please refer to the NXP website here:

{% embed url="https://www.nxp.com/products/processors-and-microcontrollers/arm-processors/i-mx-applications-processors/i-mx-8-applications-processors/i-mx-8m-plus-arm-cortex-a53-machine-learning-vision-multimedia-and-industrial-iot:IMX8MPLUS" %}

###
