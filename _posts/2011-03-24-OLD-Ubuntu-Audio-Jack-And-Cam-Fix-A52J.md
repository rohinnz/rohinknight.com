---
layout: post
title:  "[OLD] Ubuntu audio jack and cam fix for Asus A52J"
date:   2011-03-24 17:00:00 +1300
categories: linux
---
**This post is from my old website and probably contains outdated information**

After I had installed Ubuntu 10.10 on my Asus A52J laptop, I had two issues
1. The sound wouldn’t play through headphones when I plugged them in.
2. May webcam was upside down in Skype.

I found the answers in these two forum posts:
* [http://ubuntuforums.org/showthread.php?t=1612004](http://ubuntuforums.org/showthread.php?t=1612004)
* [http://ubuntuforums.org/showthread.php?t=1460790&page=12](http://ubuntuforums.org/showthread.php?t=1460790&page=12)

**Headphones problem**

1. Create file /etc/modprobe.d/sound.conf, and enter the following:
```console
options snd-hda-intel model=ideapad
```

2. Reboot (or reload snd-hda-intel)

**Skype cam problem**

To fix the cam in Skype, create a bash script in your home directory
```console
#!/bin/bash
export LIBV4LCONTROL_FLAGS=3 && LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```
