# Install Node-Red on Wago CC100 on scratch

### CC100 firmware image version: 04.03.03(25)

### Update Firmware of CC100

- Download last [CC100 Firmware](https://downloadcenter.wago.com/software).
- Download Create Bootable SD Tool e.g. [Rufus Portable](https://rufus.ie/en/).
- Write downloaded image to SD with tool.
- Insert SD into CC100 slot and turn power on.
- On default the CC100 gets the ip from DHCP server on network.
- Wait until all leds turns off.
- Look on your router website for a device with name CC100-xxxxx
- Or type on Windows on commandline `netstat -ao`.
- Open Webbrowswer with this ip.
- Enter Username ***admin*** and Password ***wago***
- Change password for user ***admin***
- Select Tab ***Configuration*** -> ***Administration*** -> ***Create Image*** -> Button ***Start Copy***
- This copies the SD image to CC100 flash.
- Turn power of CC100 off and remove SD card.
- Turn power of CC100 on.
- The CC100 boots from flash memory.
- Wait until all leds turns off.

### Adjust Settings of CC100
- Look on your router website for a device with name CC100-xxxxx
- Or type on Windows on commandline `netstat -ao`.
- Open Webbrowswer with this ip.
- Enter Username ***admin*** and Password ***changed password***

### Set Clock and NTP server
- Check clock with select Tab ***Configuration*** -> ***Clock***.
- To set automatic clock update select Tab ***Configuration*** -> ***Ports and Services** -> **NTP Client***
- Enter on field ***Time Server 1*** a NTP-Server address e.g **time.google.com**
- Press Button **Update Time**
- Check ***Service enabled** and press button ***Submit***
- Check clock again with select Tab ***Configuration*** -> ***Clock***.

### Set PLC Runtime
- If you not use CODESYS select Tab ***Configuration*** -> ***PLC Runtime*** -> ***PLC Runtime Version*** -> None
- Press Button **Submit** 

### Create SD card media for using for docker
- Make sure the SD card does not contain a boot image.
- Turn power of CC100 off and insert SD card.
- Turn power of CC100 on and wait until all leds turns off.
- Open Webbrowswer with ip of CC100.
- Enter Username ***admin*** and Password ***changed password***
- Select Tab ***Configuration*** -> ***Mass Storage*** -> ***Create new Filesystem on Memory Card***
- ***Filesystem type*** must select Ext4.
- Enter in field ***Label*** `sd`
- Press button ***Start*** -> ***Continue***.
- The SD Card is now mounted to `/media/sd/`

### Start Docker
- Select Tab ***Configuration*** -> ***Docker***.
- Check ***Service Enabled***
- Press button ***Submit***

### Assign SD card for Docker
- Download and install [PuTTY](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html).
- Start PuTTY select ***Connection type:*** `SSH`
- Enter ip from CC100 in field ***Host Name***
- Press button ***Open***.
- Enter user `root` and password `wago`
- Enter new password (don't forget password).
- Check if docker runs with enter `docker -v`
- Edit docker confuguration file with enter `nano /etc/docker/daemon.json`
- Change `"data-root":"/home/docker"` to `"data-root":"/media/sd/docker"`
- Exit editor with Ctl-X and save file.
- Enter in PuTTY for stop docker `/etc/init.d/dockerd stop`
- Enter in PuTTY for start docker `/etc/init.d/dockerd start`
- Enter in PuTTY for check media `df -h | grep media` 

### Installing Node-Red on Docker
- Start PuTTY with ip of CC100 (Connection type: `SSH`)
- Enter user `root` and `changed password`
- Enter `docker run -d \`
- `--name node-red \`
- `--privileged=true \`
- `--user=root \`
- `--net=host \`
- `-v node_red_user_data:/data \`
- `nodered/node-red`
- Wait until docker installs Node-Red
- check node-red image with enter `docker images`
- Node-Red runs as deamon in background
- You can attach to node-red deamon with enter `docker attach node-red`
- For deattach node-red deamon press `Ctrl+P` and `Ctrl-Q`
- Start Node-Red UI with enter on Webbrowswer `[ip-of-cc100]:1880`
- To Start the Node-Red deamon enter `docker star node-red`
- To Stop the Node-Red deamon enter `docker stop node-red`


