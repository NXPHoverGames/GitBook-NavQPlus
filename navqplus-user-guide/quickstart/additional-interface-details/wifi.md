---
description: Setting up the NavQ+ to connect to WiFi
---

# WiFi (DRAFT)

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
