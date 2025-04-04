# HP Power supply (up to 1200w*) breakout board w/ ESP8266 
(I use ESPhome and that is the example included) to control the Power supply remotely. 

**WARNING: This code is designed to use custom components with ESPhome, a feature that was removed. I do not have a work around for this at this time.**


These are commonly used in the holiday lighting community (as I am on my show), so the features are geared towards this.

## Features include

- PSMBus control/management of the power supply
  - PS Temps (There are two sensors) monitoring (in Fahrenheit)
  - AC Voltage, current (Amps) and power (watts) monitoring
  - DC Voltage, current (Amps) and power (watts) monitoring
  - PSU Fan speed monitoring and control.
  - PSU model detection (common PSU names pre-mapped in code)
- Analog measurement of power (As a backup in the event the PSMBus is not working/incompatible)
- PSU Failure/Alarm support (There is no real use for this outside of a PSU fan failure)
- Local and remote power supply power control
- Case/Box fan control for up to 2a of fans using standard PC style 3/4 pin fans. Protected with Polyfuse, powered even with PSU is off.
- Environmental monitoring option via BME280 (Or any other i2c sensor via a header)
- Wifi signal strength


## Some notes about this design

- There is no real feedback about PSU state outside of the PSU LED, I felt it wasn't needed on the board as you can usually see the PSU LED.
- There is no feedback on Case/Box Fan status, but you usually can see the fan operating or not; most users don't use this unless you're in the south or California.
- There is a 900W (75a) power limit.  This is designed around a 1200w ps running on 120v.*
- 30a max per output connector
- 10awg max size per output connector
- Wire ferrules are recommend
- Torque output connector to 5 in-lbs.

### Technical bits and bobs around the notes
* The board has a power limit of **900w continuous draw (75a)** it *should* be ok with higher draws for VERY Short periods (IE accidentally setting lights to all white). This is because the 64 pin PSU Connector from TE is rated at 3 amps a pin, and there are 26 pins per +12v and Gnd, resulting in 78a, The traces are designed around a 25c temp rise, with the PSU fan sucking air over it all the time, this should be fine. I'm sourcing real TE high-power connectors, HP may have some proprietary connectors that can handle more power, but a 1200w power supply requires 240v to output it's full power - and most people don't do that.

Each of the output connectors are rated at 32a, but 10awg is the max wire size, so its really 30a. You should use wire Ferrules and torque the connectors to 5 in-lb at high currents. Over torquing can break them.




The code for the common slot PS is forked from https://github.com/hitsword/csps_esphome
