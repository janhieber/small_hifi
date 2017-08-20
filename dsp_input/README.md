# About
This is the DSP input boards.  
It should handle 4 things:

# Technical
- Audio source and switching:
  - Analog stereo input with 3.5 mm jack + good ADC
  - USB audio
  - Bluetooth audio
  - A switch to handle the different inputs
- DSP chip, maybe Analog Devices?
  - Should handle the digital signal from the switch
  - Acts as audio crossover for high and middle/low tone
  - Could do some equalizing etc...
  - Should be easy programmable (not C, but some software with blocks etc)
- DAC for feeding the class D amps
  - WM8804/WM8524 ???
  - We anslo need a IC for analog volume control here
- Microcontroller (some small STM32F3/4)
  - For analog volume control IC
  - Some runtime config of DSP
  - Remote control IR/radio?
  - Switch on delay to charge caps
  - Temperature control

[https://www.hobbyhifiladen.de/aktivmodule-dsp/sure-electronics/?p=4](https://www.hobbyhifiladen.de/aktivmodule-dsp/sure-electronics/?p=4)

# Tools
The board should be designed with KiCAD.

# Notes
Maybe we need a µC too on the board. But we should only use
it if needed. The input switching can be done with normal switches
and a switch IC.
