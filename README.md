# BBL-X1C_Gcode-Modifications

## Introduction 
This repository contains custom gcode for modifying behavior of BambuLab X1C 3D printer. 

The gcode was developed for use with OrcaSlicer. 

Use at your own risk.

## Machine Start Gcode 
Currently, I use the gcode contained in the files to manage chamber temperatures. 

### Chamber Heating 
For now, I am relying on heat from the print bed to increase chamber temperature, so gcode should be used after bed is pre-heated. 
This gcode essentially just turns on auxillary fan at full speed (while making sure chamber fan is off). Then there is a wait until the chamber reaches the target temperature set in the profile for the first filament.

Additional functionality:
- Conditional on bed temperature being greater than target chamber temperature. 
- Move nozzle to purge chute to prevent oozing on bed 
- Setting a message to X1C LCD while heating ("Paused by the user"")

### Heat-Soak
Adds a simple wait for heat-soaking printer after target chamber temperature is reached. To avoid doing this unneccesarily, I have the heat-soak performed conditionally when target chamber temperature is greater than 30ºC.

### Simple Nozzle Wipe
For wiping nozzle in case oozing occured during chamber heating or heat-soak. Included to ensure that nozzle is clean before proceeding to auto bed leveling. 


## Machine End Gcode 
### Cooldown 
Turns on auxillary fan until bed cools. Then also turns on exhaust fan until chamber cools. Then signals end of print. I often use high-temperature filaments so this functionality streamlines my workflow.
