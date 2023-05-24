# Ethernet

## Disable onboard Ethernet

Q: I have connected to WiFi . Is there a way to stop the occasional messages regarding eth1: ? The messages are pictured above in my 2:49PM post, The messages show up every 300 seconds\
\
A: Ed S 12/28/2022 -  One option is to unbind the driver:

```
echo -n "30bf0000.ethernet" > /sys/bus/platform/drivers/imx-dwmac/unbind
```

Note: The redirected file may be opened by the shell before the "sudo echo" command is executed, therefore If the shell is not already root (via "sudo -i") a different form is needed:

```
sudo sh -c "echo -n 30bf0000.ethernet > /sys/bus/platform/drivers/imx-dwmac/unbind"
```

