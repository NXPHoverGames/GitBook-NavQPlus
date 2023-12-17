# Wireless Networking

## Configuring WiFi, System Hostname, Username or Password <a href="#configuring-wifi-system-hostname-username-or-password" id="configuring-wifi-system-hostname-username-or-password"></a>

### Configuring WiFi on NavQPlus <a href="#configuring-wifi-on-navqplus" id="configuring-wifi-on-navqplus"></a>

To connect NavQPlus to a WiFi network, use the `nmcli` command. The interface is relatively straightforward, to connect with `nmcli`, run the following command:

```bash
sudo nmcli device wifi connect <network_name> password "<password>"
```

If struggling to connect to a network, see if it is visible by running:

```
sudo nmcli device wifi list
```

Once connected to the WiFi network the NavQPlus will continue to connect to that network even after a reboot.



### What wifi network is the NavQPlus currently connected to?

To see what Wifi network the NavQPlus is currently connected to run without `sudo`:

`nmcli device wifi list`

Or if running with `sudo` it will be the network preceeded with a star.



### Connecting to NavQPlus over WiFi <a href="#connecting-to-navqplus-over-wifi" id="connecting-to-navqplus-over-wifi"></a>

Once setup to connect over a local WiFi network, SSH into the NavQPlus over WiFi by running:

```bash
ssh <username>@<hostname>.local
```

Or depending on network setup:

```bash
ssh <username>@<hostname>
```

