---
section: "blog"
category: "build"
title: "RPi to UNI-T UT61E Comms"
author: "Stello"
date: "2021-3-31"
tags: ["blog", "van", "electrical", "test", "equipment"]
---

![metameta](RPi-to-UNI-T-UT61E-Comms.JPG)

### Getting an RPi talking to a UNI-T UT61E

This was super painless once I got the right model of multimeter.  Turns out the UT61E+ is NOT supported by sigrok (and it says so right on the webpage UT61E if you can read).  Note, the model I got came with an RS-232 cable, so I did have to dig out a RS232-USB cable ().   This is all it took:

1. ```apt-get install sigrok-cli```

2. ```python3 -m serial.tools.list_ports```
```
/dev/ttyAMA0     
/dev/ttyUSB0
```
3. ```sigrok-cli --driver=uni-t-ut61e-ser:conn=/dev/ttyUSB0 -O analog --samples 5```

```
P1: 2.421 kΩ AUTO
P1: 2.421 kΩ AUTO
P1: 2.421 kΩ AUTO
P1: 2.421 kΩ AUTO
P1: 2.421 kΩ AUTO
```
4. Woo

For kicks, I went ahead and hooked up the RD6018 and had a script cycle through voltage commands modulo 10 while reading the voltage off the UT61E all via the RPi.  Hello Automated Testing World!
