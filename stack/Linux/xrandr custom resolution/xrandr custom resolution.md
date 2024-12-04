---
Owner: Sharafat Karim
Last edited time: 2022-12-15T19:42
---
  

![[dp.sh]]

![[dp2.sh]]

---

xrandr custom resolution guide  
(this way you can create a bash script like this one (  
[https://t.me/UbuntuLocal/187](https://t.me/UbuntuLocal/187)))

First generate a "modeline" by using cvt  
Syntax is: cvt width height refreshrate (refresh rate is optional)  

`cvt 1680 1050 60`

this gives you:

1680x1050 59.95 Hz (CVT 1.76MA) hsync: 65.29 kHz; pclk: 146.25 MHz

Modeline "1680x1050_60.00" 146.25 1680 1784 1960 2240 1050 1053 1059 1089 -hsync +vsync

Now tell this to xrandr:

`xrandr --newmode "1680x1050_60.00" 146.25 1680 1784 1960 2240 1050 1053 1059 1089 -hsync +vsync`

Then you can now add it to the table of possible resolutions of an output of your choice:

`xrandr --addmode VGA-0 1680x1050_60.00`

The changes are lost after reboot, to set up the resolution persistently, create the file ~/.xprofile with the content:

```Python
#!/bin/sh
xrandr --newmode "1680x1050_60.00"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync
xrandr --addmode VGA-0 1680x1050_60.00
```

> I forgot the source of these text. I think google uncle can help you!