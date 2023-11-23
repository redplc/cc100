
## Update Firmware of CC100

### [Home](README.md)

### CC100 firmware image version: >= 04.03.03(25)

- Download last [CC100 Firmware](https://downloadcenter.wago.com/software).
- Download Create Bootable SD Tool e.g. [Rufus Portable](https://rufus.ie/en/).
- Write downloaded image to SD with tool.
- Insert SD into CC100 slot and turn power on.
- On default the CC100 gets the ip from DHCP server on network.
- Wait until all leds turns off.
- Look on your router website for a device with name CC100-xxxxx
- Open Webbrowswer with this ip.
- Enter Username ***admin*** and Password ***wago***
- Change password for user ***admin***
- Select Tab ***Configuration*** -> ***Administration*** -> ***Create Image*** -> Button ***Start Copy***
- This copies the SD image to CC100 flash.
- Turn power of CC100 off and remove SD card.
- Turn power of CC100 on.
- The CC100 boots from flash memory.
- Wait until all leds turns off.
