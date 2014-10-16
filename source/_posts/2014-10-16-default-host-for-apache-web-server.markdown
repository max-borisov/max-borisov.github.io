---
layout: post
title: "Default host for Apache web server on Ubuntu"
date: 2014-10-16 09:14:44 +0300
comments: true
categories: 
---
Here is how you can set a default host:

1. Go to **/etc/apache2/sites-available**.
2. Find a **default.conf** file.
3. Inside **VirtualHost** directive put the line **DocumentRoot /var/www/yoursite.com**
4. Restart apache - **/etc/init.d/apache restart**

Use IP address or yoursite.com domain to access your server.
Code tested on **Ubuntu 13.10**.

Where the **conf** file is located and how it should be modified.

![](/images/posts/apache-default-host/img_2.png)
![](/images/posts/apache-default-host/img_1.png)
