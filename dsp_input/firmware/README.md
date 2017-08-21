# About
This is the STM32H7 firmware

# Technical
FW for master and slave should be the same.  
Idea is, to set a jumper so the STM knows
if its master or slave.  
This way we simplify FW update.

# Tools
We use STM32CubeMX generated Makefile project
and FreeRTOS.

# Checklist
- [ ] USB audio
- [ ] remote control
  - [ ] IR
  - [ ] radio
- [ ] SPDIF link to slave
  - [ ] audio link with 2 channels
  - [ ] data link
- [ ] handle I2S input
- [ ] DSP stuff
  - [ ] crossover with BiQuad IIRs
  - [ ] equalizing
- [ ] control volume control IC
- [ ] switch on delay
- [ ] temperature control

# Notes

