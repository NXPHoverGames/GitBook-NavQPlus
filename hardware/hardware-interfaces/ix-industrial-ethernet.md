# IX Industrial Ethernet

{% hint style="warning" %}
Some versions of the NavQPlus do not include the IX Ethernet interface typically will have -XE in their part numbering

i.e. **8MPNAVQ-4GB-XE or**&#x20;

**part number 8MPNAVQ-8GB-XE**
{% endhint %}

## Using IX Industrial Ethernet

IX industrial ethernet defines a new rugged and small connector type for traditional 100BaseTX  and 1000BaseTX interfaces. These traditionally would use RJ45 with plastic clips whereas IX industrial is primarily metal shell and clip design. The signals used are exactly the same and only the connector changes to the IX connector. \
Both  IX-to-IX cables as well as IX-to-RJ45 cables are available off the shelf..\
\
Plugging an IX-to-RJ45 cable into the NavQPlus will allow you to connect via ethernet to a laptop. An IX-to-IX would allow connection to the NXP [MR-T1ETH8](https://www.nxp.com/products/security-and-authentication/authentication/sja1110-100base-t1-multi-gig-ethernet-switch-example-board:MR-T1ETH8) ethernet switch board or similar industrial equipment. \
\
Note that the [MR-T1ETH8](https://www.nxp.com/products/security-and-authentication/authentication/sja1110-100base-t1-multi-gig-ethernet-switch-example-board:MR-T1ETH8) was was also made for mobile robotics with the intention of demonstrating the NavQPlus being able to connect to a multitude of T1 devices such as [Automotive Radar modules ](https://www.smartmicro.com/automotive-radar/drvegrd-169)and cameras.\
\
The IX Ethernet interface on NavQPlus is capable of gigabit 1000BaseTX speeds.

## ![IX industrial ethernet connector shown on right edge of board.](<../../.gitbook/assets/NavQPlus 20210930\_162135.jpg>)

## Use 100BaseT1 instead of IX Ethernet port

There are two boards from the mobile robotics team that can also convert from T1 Ethernet back to a 100BaseTX:

* [MR-T1ETH8](https://www.nxp.com/design/development-boards/analog-toolbox/sja1110-100base-t1-multi-gig-ethernet-switch-example-board:MR-T1ETH8)
* [RDDRONE-T1ADAPT](https://www.nxp.com/products/interfaces/ethernet-/automotive-ethernet-phys/ethernet-media-converter-for-drones-rovers-mobile-robotics-and-automotive:RDDRONE-T1ADAPT), there is also a [separate gitbook for this board here](https://app.gitbook.com/o/-L9GLsni4p7csCR7QCJ8/s/-M9tTGlc2SB\_GfvlG8d4/)
