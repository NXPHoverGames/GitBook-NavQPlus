# External RTC - Timestamp inputs

The NXP PCF2131 Nano-Power Highly Accurate RTC with Integrated Quartz Crystal is included on board. \
The PCF2131 is a CMOS real time clock (RTC) and calendar with an integrated temperature compensated crystal (Xtal) oscillator (TCXO) and a 32.768 kHz quartz crystal optimized for very high accuracy and ultra-low power consumption.\
\
This IC has four timestamping hardware inputs. These can log events such as tampering or an enclosure being opened even when no power is applied to the rest of the board. \
See the Datasheet for this part for more information.

Note this RTC is in addition to the internal RTC for the i.MX 8M Plus.

\
Note that at time of publishing, there are several Linux drivers available from various public sources, but the one integrated with the NavQPlus BSP does not support this function yet.
