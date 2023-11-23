## Adjust Settings of CC100

### [Home](README.md)

### CC100 firmware image version: >= 04.03.03(25)

### Open Web-Based-Managment of CC100
- Look on your router website for a device with name CC100-xxxxx
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
