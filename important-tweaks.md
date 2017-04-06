## Important Tweaks

### Fix video tearing in Intel Graphics (laptop)
This one worked well, for me, I tested using a transformers 1080p 60fps video (the video is 4k, but I used only 1080)
When people show up it gets some tearing, after this config it fixed. To be honest this one made linux usable to me, I would go back if the tearing continued.

The problem was fixed using the solution presented here:
[http://askubuntu.com/a/668590/630696]

So in short, we need to create a file:

`/etc/X11/xorg.conf.d/20-intel.conf`

Containing:
```
Section "Device"
   Identifier  "Intel Graphics"
   Driver      "intel"
   Option      "TearFree"    "true"
EndSection
```

Also, we need to logout/restart so the changes take effect.

Worked on Ubuntu Mate, however, apparently also works on Arch based distros.