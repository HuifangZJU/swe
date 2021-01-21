# multi-people using unix desktop

## install VNC server
e.g. realvnc

### start vncserver from root
```
sudo update-rc.d vncserver-x11-serviced defaults
```
## choose desktop
### LXDE
```
sudo apt-get install lxde
```

add file: /etc/vnc/xstartup.custom
``` bash
#!/bin/sh
DESKTOP_SESSION=LXDE
export DESKTOP_SESSION
startlxde
vncserver-virtual -kill $DISPLAY
```
### [KDE plasma-desktop](http://bbs.archbang.org/viewtopic.php?id=5088)
add file: /etc/vnc/xstartup.custom
``` bash
#!/bin/sh
DESKTOP_SESSION= plasma
export DESKTOP_SESSION
startkde
vncserver-virtual -kill $DISPLAY
```

**Notice:** xstartup.custom needs the sudo permission

```
sudo chmod +x xstartup.custom
```

## adding desktop
add the following into /etc/rc.local
```
su mirsking -c "vncserver-virtual -geometry 1600x900 :24"
```
