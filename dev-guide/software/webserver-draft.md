---
description: Controlling a NAVQ+ with an HTML WebServer
---

# WebServer (DRAFT)

The idea is to control the robot (or anything), using low level commands written with shell scripts commanded straight from a HTML page. Not using higher level languages as Python for example, makes the robot very responsive and quick to act.

A WebServer is used to control the NAVQ+ using low level commands written with shell scripts commanded straight from a HTML page. This page will explain how to set-up a WebServer and control your NAVQ+.

The webserver we will use is called Lighttpd, for more information on the Lighttpd read the following link:

{% embed url="https://redmine.lighttpd.net/projects/lighttpd/wiki" %}

First step is to install Lighttpd WebServer and components. Use the following code in your NAVQ+ serial console application:

```
sudo apt-get -y install lighttpd
```

```
sudo lighttpd-enable-mod cgi
```

```
sudo lighttpd-enable-mod fastcgi
```

This is the output you should receive after running all three codes above:

<figure><img src="../../.gitbook/assets/image (6).png" alt=""><figcaption></figcaption></figure>

Lighttpd is looking for a **index.html** page at **/var/www/html**. We will change it, so the index.html will be placed under /var/www. For that, we must edit the Lighttpd config file using nano:

```
sudo nano /etc/lighttpd/lighttpd.conf
```

{% hint style="danger" %}
Having issues with this file in the NavQ+ (file seems empty)
{% endhint %}

In this file you should change:

```
server.document-root =“/var/www/html”
```

To:

```
server.document-root =“/var/www”
```

For the changes we made just now to take effect, we must reboot the web server. To do that enter both commands in order:

```
sudo /etc/init.d/lighttpd stop
```

```
sudo /etc/init.d/lighttpd start
```

At this point the web server is running and if a page index.html is located at /var/www, we can access it from any browser, typing the NAVQ+ address you can see the default web page by lighttpd.

