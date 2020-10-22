# Description

This is a passthrough mediator for to storing and retrieving PLM questionnare mappings to and from OCL through OpenHIM

# Installation

1.	Clone the openhim-mediator-plm-qmap repo into the /usr/share folder.
2.	Create “openhim-mediator-plm-qmap.service” file with the following content and save it in /etc/system/system/

```
[Unit]
Description=OpenHIM PLM QMAP mediator
[Service]
WorkingDirectory=/usr/share/openhim-mediator-plm-qmap
ExecStart=/usr/bin/npm start
Restart=always
StandardOutput=syslog
StandardError=syslog
SyslogIdentifier=plm-qmap-mediator
Environment=NODE_ENV=production
User=openhim-core
Group=openhim-core
[Install]
```

3.	Run `systemctl start openhim-mediator-plm-qmap.service`


4. After successful installation, configure the mediator with the following settings - 
<p align="center">
<img src="images/mediatorConfig1.png" width="600" text-align="center" title="Mediator Config">
  <img src="images/mediatorConfig2.png" width="600" text-align="center" title="Mediator Config 2">
  <img src="images/mediatorConfig3.png" width="600" text-align="center" title="Mediator Config 3">
  </p>

5. Create a channel through which the mediator is accessed and use the following settings -

<img src="images/channelConfig1.png" width="600" text-align="center" title="Channel Config">
  <img src="images/channelConfig2.png" width="600" text-align="center" title="Channel Config 2">
  <img src="images/channelConfig3.png" width="600" text-align="center" title="Channel Config 3">
   <img src="images/channelConfig4.png" width="600" text-align="center" title="Channel Config 3">
  </p>

