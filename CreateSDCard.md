## Create SD card media

### [Home](README.md)

### CC100 firmware image version: >= 04.03.03(25)

Flash storage space on the CC100 is limited.<br>
If the flash memory space is exceeded, the CC100 cannot function properly.<br>
Therefore, data should be saved to an external SD card.<br>

- Use a suitable SD card (e.g from Wago, Industrial or High Endurance).
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
