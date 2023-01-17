# I2C

## Accessing the external I2C bus

The i.mx 8M Plus has a number of I2C busses on board. Internally they are connected to a variety of onboard peripherals. Normally you will not need to address these peripherals directly, and they will be handled by Linux drivers.

* I2C1 - SOM only for PMIC control
* I2C2 - MIPI CSI1, LVDS1, DSI
* I2C3 - MIPI CS2, LVDS2, PCIe
* I2C4 - USB1 TCPC, USB2 TCPC, Secure Element, RTC
  * TCPC1 I2C ADDR: 1010001X&#x20;
  * TCPC2 I2C ADDR: 1010010X
  * RTC I2C ADDR: 1010011X
  * PD1 I2C ADDR: 1110010X&#x20;
  * PD2 I2C ADDR: 1110011X&#x20;
  * SE050 I2C ADDR: 1001000X

### External I2C #6 on AUX Connector

\
AUX connector: I2C bus #6 is pin-muxed with UART4 to the six pin JST-GH J12 connector and is the external I2C bus is enabled on the AUX port of the NavQ+.\
By default these are configured for I2C and not UART4 (internal MCU)&#x20;

{% hint style="info" %}
Note that UART4 typically is used to connect to the internal Microcontroller of the i.MX 8M Plus, and it is also pinmuxed on J11. The two alternative pinmuxing locations are so a custom Linux DTB could be configured depending on your needs for UART4, SPI2 or I2C. &#x20;
{% endhint %}

A table of the J12  pinout is below. Note that pin 1 is on the left side of the connector:

| Pin | Function        | Voltage |
| --- | --------------- | ------- |
| 1   | 5V              | 5V      |
| 2   | I2C\_SDA        | 3V3     |
| 3   | I2C\_SCL        | 3V3     |
| 4   | GPT1\_CAPTURE1  | 3V3     |
| 5   | GPT1\_CAPTURE2  | 3V3     |
| 6   | GND             | GND     |

You only need to use pins 1, 2, 3, and 6 for I2C.\
These GPIO are 3.3 volt tolerant only. \


## I2C device detection

To detect that a device is present on the bus, you can run the following command:

```
i2cdetect -y 5
```

You may need to add the 'user' user to the i2c group to access the bus. To do this, run the following command, then log out and log back in:

```
sudo usermod -a -G i2c user
```

## I2C (I2C6) Locator

<figure><img src="../../.gitbook/assets/image (2).png" alt=""><figcaption><p>Location of I2C #6 on AUX connector</p></figcaption></figure>

## Schematic

{% hint style="warning" %}
The I2C port is multiplexed with UART4 on the NavQPlus. This is configured in the linux DTB files. Therefore the schematic below shows the UART signal names. The Multiplexed I2C signal names are shown on the far left of the image
{% endhint %}



<figure><img src="../../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>
