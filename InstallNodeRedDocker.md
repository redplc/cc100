## Install Node-Red on Docker

### [Home](README.md)

### CC100 firmware image version: >= 04.03.03(25)

### Start Docker
- Select Tab ***Configuration*** -> ***Docker***.
- Check ***Service Enabled***
- Press button ***Submit***

### [Create and Mount SD Card](CreateSDCard.md)

### Assign SD card for Docker
- The SD card must be inserted
- Download and install [PuTTY](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html).
- Start PuTTY select ***Connection type:*** `SSH`
- Enter ip from CC100 in field ***Host Name***
- Press button ***Open***.
- Enter user `root` and password `wago`
- Enter new password (don't forget password).
- Check if docker runs with enter ```docker -v```
- Edit docker configuration file with enter ```nano /etc/docker/daemon.json```
- Change `"data-root":"/home/docker"` to `"data-root":"/media/sd/docker"`
- Exit editor with Ctl-X and save file.
- Enter in PuTTY for restart docker ```/etc/init.d/dockerd restart```
- Enter in PuTTY for check media ```df -h | grep media```

### Installing Node-Red on Docker
- Start PuTTY with ip of CC100 (Connection type: `SSH`)
- Enter user `root` and `changed password`
- Enter the following commands in sequence:
- ```docker run -it \```
- ```--name node-red \```
- ```--privileged \```
- ```--user=root \```
- ```--net=host \```
- ```-v node_red_user_data:/data \```
- ```nodered/node-red```
- Wait until docker installs and start Node-Red
- Open second session with PuTTY
- Check node-red image with enter ```docker images```
- Check running docker images with enter ```docker ps```
- You can attach to node-red deamon with enter ```docker attach node-red```
- For deattach node-red deamon press `Ctrl+P` and `Ctrl-Q`
- Start Node-Red UI with enter on Webbrowswer `[ip-of-cc100]:1880`
- To Start the Node-Red deamon enter ```docker start node-red```
- To Start the Node-Red CLI enter ```docker start -a node-red```
- To Stop the Node-Red enter ```docker stop node-red```
