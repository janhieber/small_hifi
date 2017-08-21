# About
This is the DSP/control board.  

# Technical
- Audio source and switching:
  - Analog stereo input with 3.5 mm jack + good ADC
  - USB audio
  - Bluetooth audio
  - A switch to handle the different inputs
  
- STM32F7 as DSP
  - Should handle the digital signal from the switch
  - Acts as audio crossover for high and middle/low tone (BiQuad IIRs)
  - Could do some equalizing etc...
  - For analog volume control IC
  - Some runtime config of DSP
  - Remote control IR/radio?
  - Switch on delay to charge caps
  - Temperature control

- DAC for feeding the class D amps
  - WM8804/WM8524 ???
  - We anslo need a IC for analog volume control here


[https://www.hobbyhifiladen.de/aktivmodule-dsp/sure-electronics/?p=4](https://www.hobbyhifiladen.de/aktivmodule-dsp/sure-electronics/?p=4)

# Tools
The board should be designed with KiCAD.

# Notes

