## Install Node-Red on SD Card

### [Home](README.md)

### CC100 firmware image version: 04.03.03(25)
[Inspired from Thorgrim Jansrud](https://github.com/thorgrimjansrud/node.js-on-wago-device).

### **!!Not Tested yet!!**

- Create first SD card media.
[Look here how](CreateSDCard.md)

Installing on the SD card is the same procedure as installing on the CC100 Flash.<br>
Just replace the path **/home/node** with **/media/sd/node**.<br>
But **libatomic** must definitely be installed on flash memory.<br>
Changing Node-Red's storage folders is not necessary as Node-Red writes them to the SD card.<br>

The performance of Node-Red is of course dependent on the SD card.<br>
If there are a lot of write accesses to the SD card, it can become defective over time.

## !! Please don't remove SD card while Node-Red is running !!
