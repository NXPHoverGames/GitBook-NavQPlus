---
description: Unofficial Schematics for NavQPlus SOM and Carrier
---

# Schematics

The official schematics for NavQPlus are published on NXP.com/navqplus.\
a copy is provided here for convenience, but note that it is possible that it becomes out of sync/out of date with the official source. Please use the NXP official source for any critical requirements.

Note that NavQPlus is an open design using i.MX 8M Plus SOC from NXP. The SOM used is identical to the one on the larger NXP EVK. The carrier board includes a number of additional features and has it's own BSP derivative in order to support these components. \
You are welcome to reproduce or modify the carrier board to your own specifications.

## NavQPlus Carrier board

This is the main board for NavQPlus (8mpnavq) and can be used to reference the connectors and testpoints.

{% file src="../.gitbook/assets/NAVQ-PLUS-2A Schematic-E3.pdf" %}
NavQPlus Carrier board
{% endfile %}

## NavQPlus SOM module

This SOM is identical to the NXP EVK SOM, with the exception that the IO are jumpered for 3v3 voltage instead of 1v8

{% file src="../.gitbook/assets/8MP-LPDDR4-1A-Schematic PDF.pdf" %}
SOM module
{% endfile %}

\
\
