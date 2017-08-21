# About
This project is about creating a small HiFi audio system.

We intend to build a two way stereo system (2 boxes, each 2 speakers)
with small size (about 20 cm height, 15 cm width and depth).

The systems purpose is providing good audio quality in small rooms.
The speakers can be places on a desk besides the computer screen for example.

# System design and architecture
There will be a master and a slave box.

Master box:
- DSP crossover with analog/USB/BT input
- 2 x class D amps, for each speaker one
- Tweeter + mid-range driver

Slave Box:  
Same as master box, but no crossover and input stuff.  
Master box provides the ready to use audio signal and
a data link for slave via SPDIF.

Master box should run in mono mode when
slave is not present.

![system architecture](https://raw.githubusercontent.com/janhieber/small_hifi/master/system_architecture.png)
Edit ``system_architecture.xml`` on [draw.io](https://www.draw.io/)

# Technical
- [Mainboard](controlboard/)
- [Class D amplifier](amplifier/)
- [Box](box/)

# Tools
We try to use free tools when possible.

- ECAD/EDA: [KiCAD](http://kicad-pcb.org/)
- CAD: [FreeCAD](https://www.freecadweb.org/)
- Drawings/charts: [draw.io](https://www.draw.io/)


# Contributing
We have some good knowledge on making this real, but of course we don't know anything
and we don't want to spend years making this perfect. So if you want to contribute, feel
free to contact us.

