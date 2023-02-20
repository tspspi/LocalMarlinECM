# Local Marlin fork

This is a fork of the Marlin 3d printer firmware (see
https://github.com/MarlinFirmware/Marlin)

This fork includes some local changes:

## Hotend-less operation with 5 steppers on RAMPS board

Since this fork is used for an ECM device there have been
modifications that lets one set the number of extruders
to zero. Additionally it's been configured for Dual X and
Dual Y axis as well as accelerations and calibration values
that match the used lead screws on the home built mini ECM
machine.

## Multi power-supply support

The multi power-supply modification supports switching
of multiple power supplies - for example to switch an
extra power supply for a heated bed just when one needs
the heated bed. This modification supports multiple
PSUs via different I/O pins.

Normally it is controlled via three M-codes:

- M86 [n]: Switches the power supply [n] (numbering is done from A to Z) on
- M87 [n]: Switches the power supply [n] off
- M88 [n]: Returns the status for the power supply [n]

Additionally the extension can be configured to automatically
switch a power supply whenever a bed temperature larger than
zero is set and to disable the PSU again whenever bed temperature
is set to zero again.

## How to build

Compiling code for the ATMega2560 on a RAMPS board

```
platformio run -e megaatmega2560
```

Flashing to the ATMega2560

```
avrdude -v -p atmega2560 -c wiring -P /dev/ttyU0 -b 115200 -D -U flash:w:.pio/build/megaatmega2560/firmware.hex:i
```

