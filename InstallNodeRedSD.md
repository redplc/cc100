## Install Node-Red on SD Card

### [Home](README.md)

### CC100 firmware image version: >= 04.03.03(25)
[Inspired from Thorgrim Jansrud](https://github.com/thorgrimjansrud/node.js-on-wago-device).

- Node.js and Node-Red are installed on the SD Card.
- Download from [Node.js](https://nodejs.org/en/download) **LTS** tar file for Linux Binaries ARMv7 (**node-vxx.xx.xx-linux-armv7l.tar.xz**)
- Download [libatomic](http://ftp.de.debian.org/debian/pool/main/g/gcc-13/)
file **libatomic1_13.x.x-x_armhf.deb**

- In example I use **node-v18.18.2-linux-armv7l.tar.xz** and ip **192.168.1.47**
- Change **node.js** file name and ip for your CC100.
- Download and install [PuTTY](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html).
- PuTTY must in Windows Path.
- Start PuTTY with ip of CC100 (Connection type: `SSH`)
- Enter user `root` and `changed password`
- Create SD card media for using for Node-Red.
- [Look here how](CreateSDCard.md)


### Create folder for node.js in CC100 (with PuTTY):
```
cd /media/sd
mkdir node
cd node
```
### Open window command line and change to folder of downloaded files:
```
cd C:\Downloads
```
### Copy Node.js tar file from PC to CC100 (Windows Command Line):
```
pscp node-v18.18.2-linux-armv7l.tar.xz root@192.168.1.47:/media/sd/node
```
### Copy libatomic deb file from PC to CC100 (Windows Command Line):
```
pscp libatomic1_13.2.0-4_armhf.deb root@192.168.1.47:/media/sd/node
```
### Open PuTTY and extract node.js files:
```
cd /media/sd/node
tar -xJvf node-v18.18.2-linux-armv7l.tar.xz -C /media/sd/node
```
### Edit profile file:
```
sudo nano ~/.profile
```
### Add to end of file:
```
# Nodejs
VERSION=v18.18.2
DISTRO=linux-armv7l
export PATH=/home/node/node-$VERSION-$DISTRO/bin:$PATH
```
### Refresh profile
```
. ~/.profile
 ```
### Unpack libatomic to folder **/usr/lib**
```
cd /media/sd/node
ar x libatomic1_13.2.0-4_armhf.deb
tar xvf data.tar.xz
cp usr/lib/arm-linux-gnueabihf/libatomic.so.1 /usr/lib
```
### Test Installation:
```
node -v
npm -v
```
### Install Node-Red
```
npm install -g --unsafe-perm node-red
```
### Change Storage Folder for Node-Red to SD Card
```
sudo nano /root/.node-red/settings.js
```
- Locate lines, uncomment and change paths:
```
userDir: '/media/sd/node',
nodesDir: '/media/sd/node/.node-red/nodes',
```
- All flows and nodes are now on **/media/sd/node**

### Start Node-Red
```
node-red
```
## !! Please don't remove SD card while Node-Red is running !!
