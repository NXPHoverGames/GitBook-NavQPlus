---
description: Unqualified Specifications for guidance only
---

# Unofficial Specifications

## Introduction

General specifications have been requested for NavQPlus. Currently there are no official qualified specifications.&#x20;

## Physical Hardware&#x20;

The CAD model below and associated measuring tools can be used to determine physical characteristics of interest. The model may also be downloaded in a variety of file formats by following the link to open in Fusion360.

{% embed url="https://a360.co/408nS79" %}
NavQPlus Enclosure and board (may be downloaded through link)
{% endembed %}

\


## Electrical Specifcations

_**PLEASE NOTE: These are unofficial specifications only. The values below may be used for guidance, but are not guaranteed.**_&#x20;

### Voltage input&#x20;

* 5-20V&#x20;
* Power supplied via High voltage USB PD power switch(es)&#x20;
  * Power input and can be from **dedicated connector** or through **USB-C**

{% hint style="danger" %}
IMPORTANT: Software may be constructed which allows power from the dedicated connector to flow to the USB-C connectors **without proper and complete driver control** over the USB PD device negotiation. IF for example the USB-C connector uses a USB-C to USB-A connector, a higher voltage than is allowed on USB-A may become present. Depending on what USB A device is connected this could cause permanent damage to the USB A device.
{% endhint %}

### Power consumption

* A detailed power analysis has not been done. Below are estimates
  * Expectation is MAX 5W and typical 3W
  * 5W =\~12V@450mA

### Enclosure dimensions

* CAD files available for board outline and case though the [link above](https://a360.co/408nS79)
* 90mmx70mm exclusive of case mounting tabs
* Tabs 82mm at max width.
* CASE Mounting tabs are 72mmx72mm
* CASE / Heatsink secondary mounting 53mmx53mm&#x20;

### Weight

* 98.4grams with Fin type heatsink attached\*
  * \* production units use a flat aluminum plate which reduce weight further

