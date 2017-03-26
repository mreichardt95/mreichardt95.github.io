---
layout: post
title: FreeNAS Corral first impressions
---

I've been a [FreeNAS](http://www.freenas.org/) user since a few years. It is my favorite system when it comes to homeserver applications.
That's why I followed the development of FreeNAS 10 (now Corral) and was very excited to see that it is out now. 

## Installation

If you already have a FreeNAS installation the upgrade is <b>super</b> easy! Just change your update train from <b>9.10</b> to <b>Corral</b> and after a reboot voila!

## Features

[FreeNAS Corral](http://www.freenas.org/) has some cool new features. It features now Docker Container support, and virtual machines, that means you can now run Linux & Windows VMs which expands the possibilities from [FreeNAS](http://www.freenas.org/) nearly unlimited. Unfortunatly the support for the old FreeBSD Jail used in 9.10 and bevor has been stopped. That means you need to reinstall al jails and config into either a VM or a Docker Container. At least you can still access the old Jails and get the data out.