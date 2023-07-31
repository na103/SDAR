# Simple Dialup Access Router
This is an how-to, not step by step guide (you need a minimal cisco router configuration skill), to set-up an little single PSTN line access router for your lab.<br>
Is useful for testing and connect to a modern Internet BBS all kind of device with a old modem inside, like Videotel or Minitel terminal.<br>
<br>
![alt text](https://github.com/na103/SDAR/blob/main/img/SDAR.jpg)
# What you need
* 1 Cisco 1751-V Router with 1 VIC 2FXS interface
* 1 Cisco blue console cable, Rj45 - 9 pin female (part number 72-3383-01)
* 1 Cisco rs232 adapter 25 pin male - 9 pin male (part number 29-4043-01)
* 1 3Com U.S. Robotics 56K modem or any modem that support V.23 standard.
* 2 rj11 phone cable and an adapter for your videotel/minitel plug
# Set-up
use the rs232 adapter to connect the modem to the router's auxiliary port with console cable.<BR>
connect the modem line port to a router fxs port with rj11 telephone cable.<br>
plug the videotel/minitel telephone cable to the other fxs port. you may need a rj11 adapter<br>
<br>
![alt text](https://github.com/na103/SDAR/blob/main/img/setup.png)
<br>
# Modem configuration
V.23 in default modem configuration is disabled, you need to activate fallback with command ats27=16<br>
and set the autoanswer with ats0=1<br>
note: if you use another type of modem, registry settings for V.23 could be different<br>
# Router configuration
when the videotel terminal is connected to the aux port via modem, a raw telnet session is activated on a bbs server due the autoconnect command.<br>
you can also decide to not do this and leave the router console at connection and start after the telnet command manually.<br>
in this case remove autocommand line. <br>
```
line aux 0
 login
 modem InOut
 autocommand  telnet bbs.retrocampus.com 23 /noecho /stream /quiet
 transport input all
 escape-character NONE
 databits 7
 parity even
 stopbits 1
 speed 1200
```
you can find a complete configuration example in repo

# License

This work is licensed under a Creative Commons Attribution 4.0 International License. See [https://creativecommons.org/licenses/by/4.0/](https://creativecommons.org/licenses/by/4.0/).

