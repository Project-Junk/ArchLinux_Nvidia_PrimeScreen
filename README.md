# Nvidia PrimeScreen

This workaround is  Deprecated use the below instructions instead  


**Use this method instead**
if you have a hybrid gpu as intel and nvidia and if you want to use nvidia gpu for screens
on arch linux then use 
the system76-power service by system76.com ( popOS team ) as it is more efficent and doesn't require any system files tweaking
https://aur.archlinux.org/packages/system76-power.git/
no need to modify any files anymore
install the system76-power service from the above aur repo using yay ( yet another yarourt )
then  enable the system76-power.service using 

```sudo systemctl enable system76-power.service```
after that you can use the hybrid/nvidia only preference using 

# hybrid
```sudo system76-power graphics hybrid``` 

**reboot**
this will enable the intel gpu to be used for display and nvidia gpu for graphics intensive task (games)

# nvidia only
```sudo system76-power graphics  nvidia```

**reboot**

this will enable the nvidia gpu to be used for both display and gpu intensive tasks
(note :- i use this mode as my intel 630 doesn't provide a smooth UI experience on gnome) 

# KDE PLASMA

for KDE Plasma to work with nvidia display you need to search for Xsetup file
if you are using sddm then it will be in ```/usr/share/sddm/scripts/```

then add these two lines to the setup file
```/usr/bin/xrandr --setprovideroutputsource modesetting NVIDIA-0```
```/usr/bin/xrandr --auto```
```/usr/bin/xrandr --dpi 96```
save and reboot and system76-power should set up the nvidia gpu for display

# LIGHT DM
got to /etc/lightdm/display_setup.sh
then add these there
```#!/bin/sh
xrandr --setprovideroutputsource modesetting NVIDIA-0
xrandr --auto



