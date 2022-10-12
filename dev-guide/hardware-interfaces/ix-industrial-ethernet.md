# IX Industrial Ethernet

{% hint style="warning" %}
NOTE: OCT,2022 - While the board and the SOC support this interface, current chip supply issues means that we are _**unable to procure the Ethernet PHY from a 3rd party semiconductor vendor**_ at this point in time. Your board MAY NOT be populated with this PHY. This is particularly true for _**HOVERGAMES3 participants**_ that are getting the early access edition of the board.&#x20;

\
These boards will ship with a USB-C to Ethernet adapter that will also give two additional USB-A connectors (which could be used for a keyboard and mouse for example)\
\
If you are in dire need of the IX interface, please contact us directly for an update on availability.
{% endhint %}

## Using IX Industrial Ethernet

IX industrial ethernet defines a new rugged and small connector type for traditional 100BaseTX  and 1000BaseTX interfaces. These traditionally would use RJ45 with plastic clips. The signals used are exactly the same and only the connector changes to the IX connector. \
You can get IX to IX cables as well as IX to RJ45 cables.\
\
Plugging an IX Industrial Ethernet cable to RJ45 into the NavQ+ will allow you to connect via ethernet to a laptop. And an IX to IX could allow you to connect to something like our [MR-T1ETH8](https://www.nxp.com/products/security-and-authentication/authentication/sja1110-100base-t1-multi-gig-ethernet-switch-example-board:MR-T1ETH8) ethernet switch board which was also made for mobile robotics\
\
The IX Ethernet interface on NavQPlus is capable of gigabit 1000BaseTX speeds.

## ![IX industrial ethernet connector shown on right edge of board.](<../../.gitbook/assets/NavQPlus 20210930\_162135.jpg>)

## Current issues with this port

~~Currently, this port does not have a static MAC address. The MAC address for this port will change every boot. We are developing a workaround for this.~~&#x20;
