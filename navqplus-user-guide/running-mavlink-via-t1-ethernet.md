---
description: T1 Ethernet between FMUK66 and NavQPlus
---

# Running MavLink over T1 Ethernet

## Prerequisite

The RDDRONE-FMUK66 has a two wire 100BaseT1 Ethernet interface on board. The NavQPlus also includes a 100BaseT1 Ethernet interface on board that can be used to connect to the RDDRONE-FMUK66.

## Setting a fixed IP to use Ethernet for FMU communication

It is not recommended to use DHCP in a vehicle such as a drone, since you generally don't want the network to change without knowing about the explicit details.  Therefore since there is no DHCP and **FMUK66** by default has a fixed IP of **10.0.0.2,** we need to set a fixed IP on the NavQPlus for `eth0` to be able to communicate via Ethernet to FMUK66.

{% hint style="info" %}
It is suggested to use IP address **10.0.0.3** for **navq+**.
{% endhint %}

### netplan connection manager

For the Ubuntu build, the linux program `netplan` is used for configuring the network settings. To force `netplan` to use a fixed IP (as in case when no DHCP is available) the following file needs to be modified.

It is possible that the file access permission must be changed so that it can be modified. For that purpose use the linux command tool `chmod` and add write permissions to the current user.

```
~$ sudo nano /etc/netplan/01-network-manager-all.yaml
```

```
network:
  version: 2
  renderer: NetworkManager
  ethernets:
    eth0:
      dhcp4: false
      dhcp6: false
      addresses:
        - 10.0.0.3/24
      routes:
        - to: default
          via: 10.0.0.3
```

This disables DHCP and sets a fixed IP of 10.0.0.3. Note that 10.0.0.3 is set as router since in this particular hardware configuration no other device is there.

### connman connection manager

For the Yocto build, the linux program `connman` is used for configuring the network settings. To force `connman` to use a fixed IP (as in case when no DHCP is available) the following file needs to be created:

{% hint style="warning" %}
It is important is that you have a Ethernet cable connection before, otherwise connman will not register the network.
{% endhint %}

```
~$ sudo nano /var/lib/connman/ethernet.config
```

```
[global]
Name = Ethernet_config
Description = Ethernet fixed IP setting

[service_onboard_ethernet]
Type = ethernet
IPv4 = 10.0.0.3/255.255.255.0/10.0.0.3
```

The IP4 settings are in the order of  ownIP/netmask/router. Note that 10.0.0.3 is set as router since in this particular hardware configuration no other device is there.

## Setting up FMUK66 for mavlink over T1 Ethernet

T1 Ethernet is supported by PX4 on FMUK66 with latest master.

{% hint style="info" %}
To enable the RDDRONE-FMUK66 mavlink telemetry via UDP sending to a specific IP you must add the following file on the FMUK66 SDcard:

_/etc/extras.txt_
{% endhint %}

```
set +e
mavlink start -x -u 14551 -o 14551 -r 200000 -t 10.0.0.3 -m onboard
set -e
```

In the example configuration above, 10.0.0.3 is the IP address of NavQPlus on the vehicle.\
\
More detailed description of the mavlink start parameters can be found here: [https://dev.px4.io/v1.9.0/en/middleware/modules\_communication.html](https://dev.px4.io/v1.9.0/en/middleware/modules\_communication.html)

\
Additionally the **MAV\_BROADCAST** parameter on the FMU needs to be set to "2 - only multicast".

{% hint style="info" %}
Distributing MavLink data can be done by installing [mavlink-router](installing-mavlink-router.md) on NavQPlus.
{% endhint %}
