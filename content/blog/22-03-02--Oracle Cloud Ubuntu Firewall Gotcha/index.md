---
title: Oracle Cloud Ubuntu Firewall Gotcha 
date: 2022-03-01T13:37:00.000Z
description: Opening firewall for Ubuntu instance in Oracle Cloud is not as easy as it seems.
---
# Problem

I was excited to try out Oracle Cloud free tier. They promised amazing VPS's at a great price, free. However I had a MAJOR headache setting up a simple web server. 

I'm familiar with running Ubuntu linux and wanted to run a web server quickly. However I found that opening a port to the internet was more difficult than i remember.

Ultimately Oracle Cloud sets you up with a Ubuntu instance that has the default Ubuntu firewall (ufw) disabled by default, and they use iptables to dictate network traffic.

# Solution

For a simple example, I started a web server using port 80 to demonstrate. 

This is all you need to get a web server going quick. 

`sudo apt install nginx` 

To open port 80 on the Ubuntu instance:

`sudo iptables -I INPUT -p tcp -s 0.0.0.0/0 --dport 80 -j ACCEPT`

You're good to go now. 

You may want to ensure that the firewall on Oracle cloud has opened that port as well. 

To check your Oracle Cloud firewall, locate the subnet that the VPS instance is under. Then ensure that the subnet has a security list that opens port 80.

Mine looks something like this:

```
Stateless   Source      IP Protocol     Source Port     Destination Port
	No	    0.0.0.0/0	TCP	            All	            80		
```

You can do this same thing with Network Security Groups (NSG), but I found security list the quickest and simplest way to get up and running.
