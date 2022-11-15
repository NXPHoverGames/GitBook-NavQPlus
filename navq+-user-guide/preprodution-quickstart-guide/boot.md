# Boot

NavQPlus should boot normally after applying power. If the voltage at PWR\_IN is too low, the boot could hang upon initializing the CPU in the Linux Kernel. Please make sure that your power input is 5-20V.

{% hint style="warning" %}
If powering from USB-C it is possible with some Linux kernel/boot configurations that the USB-C port hardware is limiting current or switches modes as software progresses. This may result in a hang or a reboot. If you suspect this is the case, try powering from the PWR\_IN port instead.
{% endhint %}

The boot process starts with U-Boot, loading the device trees in the boot partition and loading the Linux Kernel.

{% hint style="info" %}
In order to observe the full complete boot process, you will need a serial port adapter connected to the board serial console. A USB-serial port adapter cable assembly is provided for this purpose. However normally you may just wait until an remote SSH connection is able to be established via networking.
{% endhint %}

Once the NavQPlus has booted to the shell, the login information is as follows:

Username: user

Password: user
