# living_wallpaper
## this is my attempt at making a "living wallpaper". the end result is an interactive, configurable desktop back ground. this can be adapted to host any basic webpages as a desktop background.

# preview:


https://github.com/user-attachments/assets/506c5788-335b-4a17-8d76-12315dc525c5



# requirements / limitations
## 1. "it works on my machine"... this works on Kubuntu(Ubuntu + KDE). iirc i saw some people doing something similar on Fedora + KDE, but Im using Ubuntu. YMMV with other distro/GUI/HW combo's. please see my specs below.
## 2. you will need python for my implementation. there are other ways to host a local server but this is what i used. 
## 3. this solution will not persist after reboot. eventually i will add a cron job to perform these steps at boot. for now though, these steps will need to be repeated everytime you reboot your work station. 

# how to
## clone code to local machine
```
$ git clone git@github.com:gabicarter/living_wallpaper.git
```
## start your local server from the living wallpaper dir you just created
```
$ cd /living_wallpaper/
$ python3 -m http.server 8080
```
## in a another terminal/window, from your home directory, use xwinrap to start a browser in "kiosk mode" and point it to your local server
```
xwinwrap -g 1920x1080+0+0 -ni -s -st -sp -b -nf -- chromium --kiosk --app=http://localhost:8080
```
## use KDE system settings to adjust the UI level where your kiosk browser sits. you can move this UI layer beneath the layers you need to interact with. make sure to use the "click layer to import" option. this will pass your clicks through to the bottom layer. anything you click on above that layer will be interacted with(see the video above), but if you click "empty" space on your desktop outside of open windows or dock menu the click will be passed to the kiosk browser at the bottom of your UI layers. 



# addition info

## - PR's welcome. 
### this could def be better. it could be consolidated into one cron or baked into the boot process. also, the base workflow can be used to make other interesting, interactive backgrounds too. pretty much any html/JS website that is light enough. id love to hear your ideas!

## - my env specs
```
OS: Kubuntu 24.04.1 LTS x86_64
Kernel: 6.8.0-52- generic
Uptime: 49 mins
Packages: 2901 (dpkg), 38 (brew), 36 (snap)
Shell: bash 5.2.21
DE: Plasma 5.27.12
I
Terminal: tilix
CPU: AMD Ryzen 9 5950X (32) @ 3.400GHz
GPU: NVIDIA GeForce RTX 3060 Ti Memory: 4597MiB /48087MiB
```
