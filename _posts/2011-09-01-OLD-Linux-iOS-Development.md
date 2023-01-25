---
layout: post
title:  "[Old] Linux iOS Development Setup"
date:   2011-09-01 17:00:00 +1300
categories: linux
---
**This post is from my old website and contains outdated information**

Here is what I did to setup Snow Leopard with xcode in Virtualbox and deploy my work to my iPhone.

I’m running Ubuntu Linux on my Asus A52J laptop with an Intel i3 CPU and 2 GB of RAM

**Install Snow Leopard**

[www.sysprobs.com](https://www.sysprobs.com/) has many useful tutorials for installing Snow Leopard in Virtualbox. I used this one for installing it on my Intel i3: [http://www.sysprobs.com/mac-os-snow-leopard-intel-i3i5-i7-processors-virtualbox](http://www.sysprobs.com/mac-os-snow-leopard-intel-i3i5-i7-processors-virtualbox)

You will need a copy of snow leopard. I first downloaded a copy of Snow Leopard and then purchased a copy after I had confirmed everything was working. If you decide to do this then please don’t be a pirate by not purchasing a copy after you have everything working. You can probably pick up a secondhand copy of Snow Leopard somewhere for a good price.

You will also need eboot.iso because Virtualbox will not be able to boot directly into Snow Leopard.

Next, download Virtualbox and create a machine with the following setup:

Set OS to Mac OSX and version to Mac OSX Server
Create a dynamically expanding hard disk of with a size of 25GB or more. Snow leopard and xcode will take up almost 20GB combined. Set memory to 1024MB (or more if possible). I first tried to install OSX under Windows 7 but I always got an out of memory error during installation. It looks like Ubuntu only uses a small amount of memory.
Enable 3D Acceleration and set video memory to high.
Disable EFI
Enable IO APIC, PAE/NX, VT-x/AMD-V, Nested Paging
Start the virtual machine and boot from the eboot.iso, and then inserted the snow leopard DVD and mounted it. Then hit refresh and press the right arrow key to select it and hit enter.

Once the installation screen appears, select English and in the next screen go to the disk utilities and create a new partition on the virtual hard disk. Then install snow leopard on it.

**Upgrade snow leopard and install MultiBeast**

Xcode requires 10.6.3 or later. If your version is less then you’ll need to upgrade.
Download the 10.6.5 upgrade and MultiBeast to your snow leopard installation.

Install the upgrade and when it tells you to restart your computer at the end, DO NOT. Instead install MultiBeast and then restart. If you restart after the upgrade but do not install MultiBeast, then you may experience problems, like your mouse no longer working!

**Installing Xcode and the iOS SDK**

You can download xcode with the ios sdk from the apple website. It is a big file, around 3.5GB.
Install xcode. This should be fairly easy provided you have enough space. After installation it will take up almost 10GB!

**Deploying your work to the iPhone**

There are two ways to do with. The first option is to pay Apple $99. This is definitely the easiest option and probably the best if you are sure you will release something to the Apple store.

The other option allows you to test your work for free, but it does require a jailborken iPhone.
Install AppSync on your iPhone via Cydia.
In snow leopard

Applications > Utilities > Keychain Access
Certificate Assistant > Create a Certificate
Create new certificate

Name: iPhone Developer
Certificate Type: Code Signing

Accept defaults for everything else and click continue until certificate is created

Edit /Developer/Platforms/iPhoneOS.platform/Info.plist
Replace all instances of XCiPhoneOSCodeSignContext with XCCodeSignContext

In xcode: Project > Edit Project Settings > Build
Set code signing identity to the certificate you just created.

Also, to deploy for earlier version of iOS, like iOS X 4.1. Change deployment version

**Setting up a shared folder**

You’ll probably want to transfer files from Linux to snow leopard at some stage. The easiest option is to use NFS.

```console
sudo apt-get install nfs-kernel-server
vim /etc/exports
```
I added the following line to the exports file. The * means anyone can mount it.

```console
/home/your_name/shared_dir_on_host    *(rw,insecure,no_subtree_check)
```
Ideally you would want something like this

```console
/home/your_name/shared_dir_on_host    mac_os_host_name(rw,insecure,no_subtree_check)
```
But I couldn’t seem to get this to work. NFS is still quite new to me.

After editing the exports file you need to reload the settings:

```console
sudo /etc/init.d/nfs-kernel-server restart
sudo exportfs
```
Now in snow leopard open a terminal and mount the shared dir:

```console
mkdir dir_to_mount_shared_dir_on_snow_leopard
mount ubuntu_host_name:/home/your_name/shared_dir_on_host dir_to_mount_shared_dir_on_snow_leopard
```

You may want to add this to a bash script for future.

**Disable Screen Saver and Power Management**

If snow leopard crashes after it is left alone for about 10 minutes, it could be because of the screen saver. It was in my case.

Under settings, disable the screen saver and the energy saving settings which turn off the hard drive and monitor.

**Screen Resolution**

Completely close Virtualbox and then enter this command from the terminal:

```console
VBoxManage setextradata “VM name” “CustomVideoMode1″ “1280×800×32”
```

Replace VM name with the actual name of your virtual machine and likewise for the screen resolution.

Source: [http://www.sysprobs.com/increase-mac-os-virtual-machine-screen-resolution-virtualbox-vmware-player](http://www.sysprobs.com/increase-mac-os-virtual-machine-screen-resolution-virtualbox-vmware-player)

**Sound**

Go to this link and follow the instructions: [http://forums.virtualbox.org/viewtopic.php?f=30&t=33358](http://forums.virtualbox.org/viewtopic.php?f=30&t=33358)

The sound quality might not be perfect when you get it working, but it should be sufficient for development purposes.


### Fixing Audio and Cam Issue
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
