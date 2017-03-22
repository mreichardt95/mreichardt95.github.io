---
layout: post
title: Adventures in EXT4 Datarecovery
---

Late night, being tired and removing python cache files before adding everything to a git source tree. Not a good combination! I accidentally deleted all `*.py` files instead of the cache files. I worked the last 2 hours on it and didn't make any backup. Damnit!
I immediately shut down the computer, booted into a live system and stored a 1:1 copy of my SSD on my NAS using `dd`.
The standard tool for ext4 data recovery is `extundelete`. It uses information on the partition journal and tries to recover files that have just been deleted.
The result: It could restore 50GB of the Android Source tree, which I deleted about a week ago, but NOT ONE FILE that I had been working on recently.
I was listening to music while working. My bad that I used Spotify. It stores cached music streams on the disk. The few seconds that I needed to realize what I've done might have been enough to override the disk space of the deleted files.
At university, I used `foremost` to recover deleted files. It does not support to search for python files out of the box, however it is possible to tune the configuration.
All Python files started with the header:

{% highlight Python %}
#!/bin/python2
"""
CAM4LINUX - a control suite for nzxt devices
Copyright (C) 2017 Matthias Riegler <matthias@xvzf.tech>
This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.
"""
{% endhighlight %}

I wanted to prevent scanning thousands of files for the right ones. So I used `CAM4LINUX` as header. This string shouldn't be in any system file!

I added the following line to `/etc/foremost.conf` and gave it a try.

{% highlight BASH %}
c4l y 20000 CAM4LINUX import ASCII
{% endhighlight %}

Foremost was able to restore about 500 files. Okay, more than I was expecting. I looked through all and found cache files of sublime and several versions of my Python files! I was able to restore everything! 