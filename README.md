[![Join the chat at https://gitter.im/small_hifi/Lobby](https://badges.gitter.im/small_hifi/Lobby.svg)](https://gitter.im/small_hifi/Lobby?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)

# About
This project is about creating a small HiFi audio system.

We intend to build a two way stereo system (2 boxes, each 2 speakers)
with small size (front not bigger then DIN A4 paper).

The systems purpose is providing good audio quality in small rooms.  
The speakers can be places on a desk besides the computer screen for example.

# System design and architecture
Master box:
- DSP audio crossover with various input cards
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
- [Controlboard](controlboard/)
  - Input electronics (USB, BT, analog, ...)
  - STM32 controller (for DSP and other stuff)
  - DAC and volume control
  - Small high quality power supply
- [Amplifier](amplifier/)
  - Class D amplifier
  - High power (switching?) supply
- [Box](box/)
  - Mid-range driver
  - Tweeter
  - Chassis

# Tools
We try to use free tools when possible.

- ECAD/EDA: [KiCAD](http://kicad.org/)
- CAD: [FreeCAD](https://www.freecadweb.org/) or OpenSCAD
- Drawings/charts: [draw.io](https://www.draw.io/)

# Contributing
Most small things may be done in master branche.  
For change/redesign use a dedicated branch!

Example, if you develop a new input board, you can do this on master.
But if you decide to redesign a board or part of a board, make a branch
for it and merge it to master when its finished and proven.

If you are tired of merging in master you can always make a branch for yourself
and merge your work into master when finshed.

We have some good knowledge on making this real, but of course we don't know everything
and we don't want to spend years making this perfect. So if you want to contribute, feel
free to contact us.

