# hid-sony-clone-fix-dkms
A quick hack to the hid-sony driver meant for the third party / clone DS4 controllers 
that do not support HID feature report 0x81.

If you see the following in your kernel logs, this patch is meant to work around that.
```
failed to retrieve feature report 0x81 with the DualShock 4 MAC address
```

If you are having an issue where the USB controller disconnects this and other devices every few seconds, 
please use a USB hub and connect your DS4 clone to that.

Also, I take no responsibility should anything happen to your PC or anything you connect to it, 
should you use this hack.  
You are the one who chooses to keep using that knock-off controller, so it's on you.  
This is not a proper fix, it just works around the issue.  
I recommend getting an original DS4 instead and using it without this hack.

# Installation/Building (Arch Linux)
I decided to pull the pkg.tar.zst releases and encourage you to build it to avoid issues. Building is easy.  

First, make sure you have `base-devel` and your headers for all your currently installed kernels installed.  
Then do these:
```
git clone https://github.com/Kyuunex/hid-sony-clone-fix-dkms.git -b archlinux-5.15
cd hid-sony-clone-fix-dkms
makepkg -si
```
If you want to install a version of this hack based on hid-sony from a different version of the kernel, 
change the branch. This repo has multiple branches.

# Installation/Building (Ubuntu)
I don't support this currently, I'm busy, but have a look at 
[this issue](https://github.com/Kyuunex/hid-sony-clone-fix-dkms/issues/1) for more info
