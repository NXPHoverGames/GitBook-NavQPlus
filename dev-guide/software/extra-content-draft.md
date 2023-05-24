# Extra Content (DRAFT)

{% hint style="danger" %}
\<TODO> Fill out missing information
{% endhint %}

## Remove unattended upgrades&#x20;

{% hint style="danger" %}
\<TODO> Add a simple explanation on why to remove unattended upgrades
{% endhint %}

```
apt remove unattended-upgrades
```

## Install nano&#x20;

GNU nano is an easy to use command line text editor for Unix and Linux operating systems. It includes all the basic functionality you’d expect from a regular text editor, like syntax highlighting, multiple buffers, search and replace with regular expression support, spellchecking, UTF-8 encoding, and more.

We will need nano for multiple steps. To install it write:

```
sudo apt install nano
```

### Edit hostname&#x20;

Run the following command to change your hostname. Assuming you want to use the hostname "compcom42".

```
sudo nano /etc/hostname compcom42 
```

#### Change the hostname in hosts file&#x20;

{% hint style="warning" %}
(TODO - Clarify all the text below this point)
{% endhint %}

```
sudo nano /etc/hosts 

… 
127.0.1.1 compcom42 

Add the additional entries 



192.168.42.11   compcom<id> 
192.168.42.5    navq<id>-d2x 
192.168.42.2    t1eth8 
192.168.42.6    d2xmodem 
192.168.42.21   radar1 
192.168.42.22   radar2 
192.168.42.23   radar3 
```

#### Set static ip configuration&#x20;

Network manager is used for network config. See below&#x20;

{% hint style="danger" %}
Missing part!!!!
{% endhint %}

#### Figure out the interface to be used&#x20;

{% hint style="danger" %}
Add explanation
{% endhint %}

```
nmcli con show 
```

From <[https://askubuntu.com/questions/246077/how-to-setup-a-static-ip-for-network-manager-in-virtual-box-on-ubuntu-server](https://askubuntu.com/questions/246077/how-to-setup-a-static-ip-for-network-manager-in-virtual-box-on-ubuntu-server)> &#x20;

#### Set static ip&#x20;

{% hint style="danger" %}
Not clear what the steps are here!
{% endhint %}

Wired connection 2 = 1000base-TX / eth1 \
Wired connection 1 = 100base-T1 / eth0&#x20;

```
nmcli con mod "Wired connection 2" 
  ipv4.addresses "192.168.42.11/24" 
  ipv4.gateway "IP_GATEWAY" (needs to be blank on static ip) 
  ipv4.dns "1.1.1.1,8.8.8.8" 
  ipv4.method "manual"  
```

From <[https://askubuntu.com/questions/246077/how-to-setup-a-static-ip-for-network-manager-in-virtual-box-on-ubuntu-server](https://askubuntu.com/questions/246077/how-to-setup-a-static-ip-for-network-manager-in-virtual-box-on-ubuntu-server)> &#x20;

### Install ROS&#x20;

_**ROS is already installed**_ on the [pre-built Ubuntu 20.04 with ROS2 Galactic image](https://github.com/rudislabs/navqplus-create3-images/releases)&#x20;

See [ROS2 installation script docs](https://onenote/#ROS2%20installation%20script%20docs\&section-id={7172739F-EEC8-4A2A-A5F8-FCA50716CC65}\&page-id={07109F1C-46AC-4EF5-AF42-327F26CCC296}\&end\&base-path=https://nxp1.sharepoint.com/sites/HoverGamesProgram/Shared%20Documents/Project%20-%20Drones4Bats/Drones4Bats/TechDocs.one)&#x20;

### Install VPN&#x20;

See [20220509 - Openvpn client user](onenote:Developments\VPN%20Client%20setup.one#20220509%20-%20Openvpn%20client%20user\&section-id={34009819-A55B-4195-A7A4-EB518C61E8D8}\&page-id={4518F3A6-DC0B-48FA-B1B2-04F502DBD87A}\&end\&base-path=https://nxp1.sharepoint.com/sites/HoverGamesProgram/Shared%20Documents/Project%20-%20Drones4Bats/Drones4Bats)&#x20;

(TODO - update VPN instructions above - external link)
