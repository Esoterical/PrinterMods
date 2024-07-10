# Extruders with Filament Sensors

This is just a collection of extruders I've modified to add simple filament sensors for use with ERCF/Other multi-material system, or just for simple runout detection or whatever.

## Filament Cutter

The main tool used to create these is a "cutter" model I've made that is the correct shape to be able to use a 5.5mm ball bearing and simple microswitch to do filament detection.

![image](https://github.com/Esoterical/PrinterMods/assets/124253477/a6760154-a336-4851-b159-1ea4b31b7223)

This model is included in the CAD file. To use it, simply align the **Pivot** (the yellow ball thing) with the center of the filament path. This will make sure the ball bearing
cutout will be exactly in the middle of the filament path longitudinally, and with the correct spacing laterally so it will trigger without jamming the filament.

The **Pivot** has faces on its surface that you can use to rotate the entire cutter component around the proper center axis. As long as you only rotate the cutter around these
pivot points then the switch-bearing-filament distances will always stay perfect.

![image](https://github.com/Esoterical/PrinterMods/assets/124253477/a4fd19f7-b41e-4a4e-9634-e747ab86a79f)

The cutout where the ball bearing will locate has a single green face. Rotate this section so the green face is "up" when printing. These flat faces are there to help with 
avoiding sags when printing to ensure the ball bearing doesn't catch/jam on loose filament.

![image](https://github.com/Esoterical/PrinterMods/assets/124253477/27c1b960-5928-44ea-b423-9155eac35215)

The hexagonal shaft is the optimal shape for both filament feeding and sensor triggering. You don't *have* to have the filament path shaped this way, but I've found it helps.
To cut this shape to an existing extruder model, I've found it easiest to just make sure the existing filament path/tube is shrunk to 2mm diameter or so (so it is smaller than the
hex size) and then align the hex shaft to the filament path (via the **pivot**) and then just extrude one of the hex faces to cut out this new hexagonal shape all along the 
existing filament path tube.

For the Switch cutout, you can align it however fits best. There are some included bridging features in case the screw holes happen to be on a "ceiling" in terms of printing 
orientation. As long as you always rotate/move it using the **pivot** then it'll all work out.

## Included Models

So far I have uploaded:

**G2E Dual Sensor**

Modified from https://github.com/JaredC01/Galileo2

![image](https://github.com/Esoterical/PrinterMods/assets/124253477/b7d69241-3f29-4449-8192-8877770913dc)

![image](https://github.com/Esoterical/PrinterMods/assets/124253477/24b7ef14-7792-46f6-9fc0-1551c54a8712)


**Clockwork 2 Dual Sensor**

Modified from https://github.com/VoronDesign/Voron-Stealthburner

(The CW2 also has a thread for a PC4M6 fitting in the top, I don't like the default option of no bowden retention mechanism. Modified Latch to clear the PC4M6 is also included)

![image](https://github.com/Esoterical/PrinterMods/assets/124253477/18bae1cb-3361-49fe-a25a-0d1569e96099)

![image](https://github.com/Esoterical/PrinterMods/assets/124253477/0c758979-ab86-4a89-8c56-679e6f5b6dfd)
