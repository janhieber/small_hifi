<!-- vim-markdown-toc GFM -->
* [About](#about)
* [Checklist](#checklist)
        * [PCB routing](#pcb-routing)
        * [Power supply](#power-supply)
* [Technical](#technical)
        * [power supply](#power-supply-1)
        * [Input boards](#input-boards)
        * [STM32 (only STM32F412ZG/STM32F412VE have 5xI2S)](#stm32-only-stm32f412zgstm32f412ve-have-5xi2s)
        * [Out stage](#out-stage)
        * [Nice to have](#nice-to-have)
        * [I2C bus addresses](#i2c-bus-addresses)
* [Tools](#tools)
* [Notes](#notes)

<!-- vim-markdown-toc -->


# About
This is the DSP/control board.  

Hardware desig files are here, [firmware](firmware/) is
in subfolder.

The first step is to design a PCB for every IC
so we can test it with a STM32 dev board.  
The second step is to make a single PCB
when we know things work.

The audio input will be placed un extra PCBs.
We make some I2S + power connectors on the main PCB
and the sources like BT or analog can be conntected
to the main board. PCBs are the same for master and slave
except we don't connect the external audio source PCBs on slave.

# Checklist

### PCB routing

- [ ] STM32F7/H7
- [ ] input board: BT audio
- [ ] input board: analog audio
- [ ] DAC + volume control

### Power supply

We will need 3-5 V. So either we use a 5 V supply
or maybe better a 7-9 V supply with linear regulators
for the ICs.

We may use a toroidal core transformer here for
best supply quality.

Additionaly we may use a small switching supply to
make a power on circuit. Always running the transformator
would be power waste in stand-by mode.


# Technical

### power supply
Transformator 6V/12V [FP12-950](http://www.mouser.com/ds/2/410/media-1068242.pdf)

### Input boards
The input boards will have a unique connector, so
we can plug in the cards we need.  
Signals on the connector: GND, I2S, I2C, SPI, GPIO, UART, supply from trafo.

| Signal | Explanation                  |
|--------|------------------------------|
| I2S    | audio to STM32               |
| I2C    | for communication            |
| SPI    | for communication            |
| UART   | for communication            |
| 1 GPIO | to switch power of the board |

For GPIOs a board can use I2C port expander
[PCF8574](http://www.ti.com/lit/ds/symlink/pcf8574.pdf)

- Analog stereo input with 3.5 mm jack + good ADC
- Bluetooth audio: [Bluegiga WT32i](https://www.silabs.com/products/wireless/bluetooth/bluetooth-classic-modules/wt32i-bluetooth-audio-module)
- USB audio: [CP2615](https://www.silabs.com/documents/public/data-sheets/cp2615-datasheet.pdf)
- Small Linux board with WLAN could provide a Spotify client

### STM32 (only STM32F412ZG/STM32F412VE have 5xI2S)
- Should handle the digital inputs
- Acts as audio crossover for high and middle/low tone (BiQuad IIRs)
- Could do some equalizing etc...
- For analog volume control IC
- Some runtime config of DSP
- Remote control IR/radio: [IRMP](https://github.com/svn2github/irmp)
- Switch on delay to charge caps
- Temperature control

### Out stage
- DAC: [TI PCM5102](http://www.ti.com/lit/ds/symlink/pcm5101.pdf)
- Volume control: [TI PGA2311](http://www.ti.com/lit/ds/symlink/pga2311.pdf)

### Nice to have
This stuff is low prio!

Display: [Winstar OLED 64x32](http://www.winstar.com.tw/products/oled-module/graphic-oled-display/micro.html)  
Gesture sensor: [APDS-9960](https://cdn.sparkfun.com/datasheets/Sensors/Proximity/apds9960.pdf)

### I2C bus addresses

[I2C](http://www.ti.com/lit/ds/symlink/pcf8574.pdf) port expander has ``0100 xxx`` (0x21 - 0x27).

| Address | Device           |
|----------|-----------------|
| 0x21 | Analog stereo input |
| 0x22 | Bluetooth audio     |
| 0x23 | USB audio           |
| -    | Linux board         |

# Tools
The board should be designed with KiCAD.

KiCAD howtos: [http://kicad.txplore.com/?cat=1](http://kicad.txplore.com/?cat=1)
- [Create parts](http://kicad.txplore.com/?p=96): This is the schematic part, has nothing to do with the footprint.
- [Create footprints](http://kicad.txplore.com/?p=111): Footprint and part is matches by pin numbers.

We keep all parts/symbols in the library ``parts.lib``. Because it is a text file,
there should be no problem when merging.  
Keep in midn to first add the parts.lib to your KiCAD before beginning.

# Notes
[https://www.hobbyhifiladen.de/aktivmodule-dsp/sure-electronics/?p=4](https://www.hobbyhifiladen.de/aktivmodule-dsp/sure-electronics/?p=4)

