## Install Node-Red on CC100

### [Home](README.md)

### CC100 firmware image version: 04.03.03(25)

- Download from [Node.js](https://nodejs.org/de/download) LTS tar file for Linux Binaries ARMv7 (**node-vxx.xx.xx-linux-armv7l.tar.xz**)
- As example I use **node-v18.18.2-linux-armv7l.tar.xz** and ip **192.168.1.47**
- Change for your tar file name and CC100 ip.
- Download and install [PuTTY](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html).
- PuTTY must in Path.
- Start PuTTY with ip of CC100 (Connection type: `SSH`)
- Enter user `root` and `changed password`
- Enter the following commands in sequence:
- ```cd /home```
- ```mkdir node```
- ```cd node```
- Open Command Window in Windows.
- Change to Folder where tar file is downloaded (e.g C:\Downloads)
- ```cd C:\Downloads```
- Enter the following commands:
- ```pscp node-v18.18.2-linux-armv7l.tar.xz root@192.168.1.47:/home/node```
- Enter password for root.
- The file is copied to the CC100.
- On PuTTY Windows enter command:
- ... To be continue


