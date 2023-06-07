---
description: Controlling a NAVQ+ with an HTML WebServer
---

# WebServer

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

<figure><img src="../../.gitbook/assets/image (5) (1).png" alt=""><figcaption></figcaption></figure>

Lighttpd is looking for an **index.html** page at **/var/www/html**. We will change it, so the index.html will be placed under /var/www. For that, we must edit the Lighttpd config file using nano (if you do not have nano see [this chapter](extra-content-draft.md#install-nano)):

```
sudo nano /etc/lighttpd/lighttpd.conf
```

In this file you should change:

```
server.document-root = “/var/www/html”
```

To:

```
server.document-root = “/var/www”
```

{% hint style="danger" %}
I personally did not have to change the file location. Not sure why
{% endhint %}

It should look something like this:

<figure><img src="../../.gitbook/assets/image (14).png" alt=""><figcaption></figcaption></figure>

Then exit the file and save. For the changes we made just now to take effect, we must reboot the web server. To do that enter both commands in order:

```
sudo /etc/init.d/lighttpd stop
```

```
sudo /etc/init.d/lighttpd start
```

At this point the web server is running and if a page index.html is located at /var/www, we can access it from any browser, typing the NAVQ+ address you can see the default web page by lighttpd. Get the NavQ+ IP address and input it into your browser search bar. &#x20;

Now let's try and place an example template webpage and access it.&#x20;

Stop the server for the next few steps.

<pre><code><strong>sudo /etc/init.d/lighttpd stop
</strong></code></pre>

Clone the following repository to somewhere where you will remember in your home file.&#x20;

```
git clone https://github.com/eslamfayad/Hover_Games3_E.F.git
```

After cloning the repository, you will copy some of the files to /var/www. This can be done with these commands:

```
sudo cp -r "yourdirectory"/Hover_Games3_E.F/ROBOT_WEB_SERVER/images /var/www
sudo cp -r "yourdirectory"/Hover_Games3_E.F/ROBOT_WEB_SERVER/cgi-bin /var/www
sudo cp  "yourdirectory"/Hover_Games3_E.F/ROBOT_WEB_SERVER/index.html /var/www
```

Now access the page again using the IP address of your NavQ+, you should get this:

<figure><img src="../../.gitbook/assets/image (6).png" alt=""><figcaption></figcaption></figure>

You have managed to make a simple webserver. This webpage can be quite useful to use as a GUI for robot controls as displayed in the example page above.&#x20;
