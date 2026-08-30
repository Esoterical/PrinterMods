## Nozzle Clean Macro

This is a fairly simple macro (well, group of macros) designed to help do a proper spotless nozzle clean so nozzle-based probing actions (ie. Voron TAP, Beacon Contact, Cartographer Touch, Eddy tap, etc.) are
much more likely to be true to life.

It accomplishes this by heating the nozzle up past the print/molten temperature of the filament you have loaded (default is 270 but you can change this with parameters) and then repeatedly scrubbing *while* 
cooling the nozzle down to below molten (default 100, again configurable). This makes sure that any ooze is easily scrubbed away while molten but there is no chance for ooze to re-occur afterwards.

I've been using this macro for over a year now and had nothing but success with it on multiple printers.

The main configuration needed are the variables at the top of the NOZZLE_BRUSH macro.

<img width="417" height="137" alt="image" src="https://github.com/user-attachments/assets/60b94cce-7636-4e09-9bdd-668c24418207" />

these dictate the size of your brush (the left side and the right side) and the Y position needed.
There is also the option for Z if you have the brush mounted somewhere that needs the toolhead to move up or down to meet it, but honestly it's probably better to mount your brush on your gantry somewhere so no Z movement is needed.
A bunch of this first NOZZLE_BRUSH macro was copied from somewhere (sorry whomever it was, I can't remember. If you know where this was from reach out so I can add attribution) so I've never actually tested the Z movement.

If you call the NOZZLE_BRUSH macro directly it will just move to your brush and do a scrub. You can use the LAPS= parameter to change how many iterations of the brush action it does.

For the actual nozzle cleaning use the CLEAN_NOZZLE macro. You can use the BRUSH_TEMP= parameter to set what temperature you want to start at (default 270) and the FINAL_TEMP= parameter to set what your end target temp will be
(default of 0 which turns the heater fully off, but it will stop brushing once the temp gets lower than 100).

For example, in my START_PRINT macros before I do any nozzle touch based probing I run 

`CLEAN_NOZZLE BRUSH_TEMP=270 FINAL_TEMP=150` 

which is hot enough for the filaments I use and 150 is cold enough for probing.
