# Boot

NavQ+ should boot normally after applying power. If the voltage at PWR IN is too low, the boot could hang upon initializing the CPU in the Linux Kernel. Please make sure that your power input is 5-20V.

The boot process starts with U-Boot, loading the device trees in the boot partition and loading the Linux Kernel.

Once the NavQ+ has booted to the shell, the login information is as follows:

Username: user

Password: user
