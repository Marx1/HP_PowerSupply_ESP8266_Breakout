# HP Power supply (up to 1200w) breakout board w/ ESP8266 
(I use ESPhome and that is the example included) to control the Power supply remotely. 

These are commonly used in the holiday lighting community (as I am on my show), so the features are geared towards this.

## Features include

- PSMBus control/management of the power supply
  -PS Temps (There are two sensors) monitoring (in Ferinheight)
  -AC Voltage, current (Amps) and power (watts) monitoring
  -DC Voltage, current (Amps) and power (watts) monitoring
  -PSU Fan speed monitoring and control.
  -PSU model detection (common PSU names pre-mapped in code)
- Analog mesurement of power (As a backup in the event the PSMBus is not working/incompatable)
- PSU Failure/Alarm support (There is no real use for this outside of a PSU fan failure)
- Local and remote power supply power control
- Case/Box fan control for up to 2a of fans using standard PC style 3/4 pin fans. Protected with Polyfuse, powered even with PSU is off.
- Enviromental monitoring option via BME280 (Or any other i2c sensor via a header)
- Wifi signal strength


## Some notes about this design

- There is no real feedback about PSU state outside of the PSU LED, I felt it wasn't needed on the board as you can usally see the PSU LED.
- There is no feedback on Case/Box Fan status, but you usally can see the fan operating or not; most users don't use this unless you're in the south or California.


The board is designed around ** 900w continous draw (75a) ** with a 1oz FR4 PCB, it *should* be ok with higher draws for VERY Short peroids (IE accidentally setting lights to all white). The 64 pin PSU Connector from TE is rated at 3 amps a pin, and there are 26 pins per +12v and Gnd, resulting in 78a, The traces are designed around a 25c temp rise, with the PSU fan sucking air over it all the time, this should be fine.

Each of the output connectors are rated at 32a, but 8awg is the max wire size, so its really 30a. You should use wire Furrels and torque the connectors to 5 in-lb at high currents. Over torqueing can break them.




The code for the common slot PS is forked from https://github.com/hitsword/csps_esphome