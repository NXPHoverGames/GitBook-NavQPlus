---
description: I2C configuration and setup
---

# I2C

{% hint style="danger" %}
This page is a work in progress 10/14/2023
{% endhint %}

## Install I2C tools

If not already present, the first step is to install the I2C tools to be able to use the I2C ports.&#x20;

```
sudo apt-get update -y
```

```
sudo apt-get install -y i2c-tools
```

##

## Adjust I2C user group

To use the I2C commands without root, you'll need to add the NavQ+ user to the i2c group. To do this, you can run the following command:

```
sudo usermod -a -G i2c user
```

```
sudo su
```

```
echo 'KERNEL=="i2c-[0-9]*", GROUP="i2c"' >> /etc/udev/rules.d/10-local_i2c_group.rules
```

##

## Check the I2C connection

Now to check the connection and confirm that the port is working correctly. Connect something to the I2C JST-GH port, then run this command:

```
i2cdetect -y 5
```

## Example

{% hint style="success" %}
The link below is a 3rd party example that shows the use of I2C from one of the NXP HoverGames participants.
{% endhint %}

{% embed url="https://www.hackster.io/504828/smart-and-sustainable-agriculture-system-8492a1?auth_token=a5b0f47e26f311e040c56947e273ed9a#toc-checking-connection-6" %}
