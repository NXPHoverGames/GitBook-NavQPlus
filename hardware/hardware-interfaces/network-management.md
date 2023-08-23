# Network Management

This image uses **Netplan** to configure **t**he network manager which is "_Networkmanager_".

Setting the IP address using ifconfig will NOT be applied persistently, and can/will be overidden periodically by _Networkmanager_ \
\
This manages  network conflicts for controlling IP networks like Ethernet and WiFi.\
\
Network Manger has several command line utilities

* _nmcli_  to get current network status
*   _nmui_ is a termnial user interface to modify connections&#x20;

    * set static IP/ DHCP
    * set DNS
    * connect to a wifi network&#x20;



\<ToDo?> add additional demonstration steps to configure wifi connection?



{% hint style="success" %}
For more information please refer to online documentation regarding Netplan/Network manager.
{% endhint %}

You can follow this tutorial below in order to set Static IP with NavQ+ :

{% embed url="https://askubuntu.com/questions/246077/how-to-setup-a-static-ip-for-network-manager-in-virtual-box-on-ubuntu-server" %}

