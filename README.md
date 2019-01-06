# Local Marlin fork

This is a fork of the Marlin 3d printer firmware (see
https://github.com/MarlinFirmware/Marlin)

This fork includes some local changes:

## Multi power-supply support

The multi power-supply modification supports switching
of multiple power supplies - for example to switch an
extra power supply for a heated bed just when one needs
the heated bed. This modification supports multiple
PSUs via different I/O pins.

Normally it is controlled via three M-codes:

-M86 [n]: Switches the power supply [n] (numbering is done from A to Z) on
-M87 [n]: Switches the power supply [n] off
-M88 [n]: Returns the status for the power supply [n]

Additionally the extension can be configured to automatically
switch a power supply whenever a bed temperature larger than
zero is set and to disable the PSU again whenever bed temperature
is set to zero again.
