# WiFi

## Connecting to a WiFi network

We suggest using the `nmtui` command to connect to WiFi networks.

```
sudo nmtui
```

This command will show a terminal user interface for connecting to WiFi networks. It is recommended to connect to the NavQPlus over Ethernet before attempting to connect to WiFi.

## Bugs and workarounds

<<\<TODO review below for correctness based on latest Linux image 11/15/2022>>>

### Ping spikes

#### Bug:

Currently when connected to a WiFi network and not connected to an Ethernet network, the NavQPlus will experience ping spikes in the range of up to 500ms. This is due to the WiFi chip attempting a periodic WiFi scan.

#### Workaround:

Currently there is no workaround for this issue. We are actively looking for a solution.

### DNS bug

#### Bug:

You will notice that the NavQPlus is not able to connect to the internet after connecting to a WiFi network and rebooting. This is because NetworkManager will attempt to set a new DNS nameserver every boot.

#### Workaround:

To fix this, please follow the instructions below.

1. Delete /etc/resolv.conf

```
sudo rm /etc/resolv.conf
```

1. Create a new /etc/resolv.conf with the following contents:

```
nameserver 8.8.8.8
```

1. Create a new file at /etc/NetworkManager/conf.d/90-dns-none.conf

```
[main]
dns=none
```

Once you have completed these steps, reboot and you should have access to the internet over your WiFi connection.
