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
