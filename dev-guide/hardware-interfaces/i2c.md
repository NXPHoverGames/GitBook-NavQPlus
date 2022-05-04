# I2C

## Accessing the external I2C bus
The external I2C bus is enabled on the AUX port of the NavQ+.

A table of the pinout is below. Note that pin 1 is on the left side of the connector:

| Pin | Function |
| --- | --- |
| 1 | 5V |
| 2 | I2C_SDA |
| 3 | I2C_SCL |
| 4 | GPT1_CAPTURE1 |
| 5 | GPT1_CAPTURE2 |
| 6 | GND |

You only need to use pins 1, 2, 3, and 6 for I2C.

To detect that a device is present on the bus, you can run the following command:

```
i2cdetect -y 5
```

You may need to add the 'user' user to the i2c group to access the bus. To do this, run the following command, then log out and log back in:

```
sudo usermod -a -G i2c user
```