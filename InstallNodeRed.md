## Install Node-Red on CC100

### [Home](README.md)

### CC100 firmware image version: 04.03.03(25)
[Inspired from Thorgrim Jansrud](https://github.com/thorgrimjansrud/node.js-on-wago-device).

- ! Node.js and Node-Red are installed on the CC100 Flash.
- Check the size of the flash before installing.
- Download from [Node.js](https://nodejs.org/de/download) LTS tar file for Linux Binaries ARMv7 (**node-vxx.xx.xx-linux-armv7l.tar.xz**)
- Download [libatomic](http://ftp.de.debian.org/debian/pool/main/g/gcc-13/libatomic1_13.2.0-4_armhf.deb)

- In example I use **node-v18.18.2-linux-armv7l.tar.xz** and ip **192.168.1.47**
- Change file name and ip for your CC100.
- Download and install [PuTTY](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html).
- PuTTY must in Windows Path.
- Start PuTTY with ip of CC100 (Connection type: `SSH`)
- Enter user `root` and `changed password`
### Create folder for node.js in CC100 (with PuTTY):
```
cd /home
mkdir node
cd node
```
### Open window command line and change to folder of downloaded files:
```
cd C:\Downloads
```
### Copy Node.js tar file from PC to CC100 (Windows Command Line):
```
pscp node-v18.18.2-linux-armv7l.tar.xz root@192.168.1.47:/home/node
```
### Copy libatomic deb file from PC to CC100 (Windows Command Line):
```
pscp libatomic1_13.2.0-4_armhf.deb root@192.168.1.47:/home/node
```
### Open PuTTY and extract node.js files:
```
tar -xJvf node-v18.18.2-linux-armv7l.tar.xz -C /home/node
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
cd /home/node
ar x libatomic1_13.2.0-4_armhf.deb
cp usr/lib/arm-linux-gnueabihf/libatomic.so.1 /usr/lib
```
### Clean up
```
cd /home/node
rm libatomic1_13.2.0-4_armhf.deb / 
rm node-v18.18.2-linux-armv7l.tar.xz 
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
### Start Node-Red
```
node-red
```
### Stop Node-Red<br>
press `Ctrl+C`

### Change Storage Folder for Node-Red to SD Card
- Create SD card media for using for Node-Red.
- [Look here how](InstallNodeRedDocker.md)
```
mkdir /media/sd/node
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
