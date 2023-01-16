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

### External I2C #6

\
I2C bus #6 is pin-muxed to the six pin JST-GH connector and is the external I2C bus is enabled on the AUX port of the NavQ+.

A table of the pinout is below. Note that pin 1 is on the left side of the connector:

| Pin | Function       |
| --- | -------------- |
| 1   | 5V             |
| 2   | I2C\_SDA       |
| 3   | I2C\_SCL       |
| 4   | GPT1\_CAPTURE1 |
| 5   | GPT1\_CAPTURE2 |
| 6   | GND            |

You only need to use pins 1, 2, 3, and 6 for I2C.

To detect that a device is present on the bus, you can run the following command:

```
i2cdetect -y 5
```

You may need to add the 'user' user to the i2c group to access the bus. To do this, run the following command, then log out and log back in:

```
sudo usermod -a -G i2c user
```

## I2C (I2C6) Locator

<figure><img src="../../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>

## Schematic

The I2C port is multiplexed with UART4 on the NavQPlus. This is configured in the linux DTB files

<figure><img src="../../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>
