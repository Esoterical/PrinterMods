# Voron Trident Silicone Nozzle Park

![image](https://github.com/Esoterical/PrinterMods/assets/124253477/5fafd403-1bd9-4efd-8809-596815707b68)


This is a simple nozzle park that mounts to the rear gantry of a Trident. Just cut up a small bit of silicone (I used a common silicone wristband, but silicone egg ring or similar should work as well) and wedge it into the holder.

The mount is adjustable so it can both clear the bed and be at the correct hight for the nozzle.

There are options with just the nozzle park, or with a purge bucket mount that connects with 6x3 magnets. This purge bucket is still a work in progress.

I've also included my NOZZLE_PARK macro. It assumes the park location is at the very back of the printer (max Y travel) but you need to find the X position where you have mounted it where the nozzle is resting on the silicone then adjust the `park_x` variable to suit.

![image](https://github.com/Esoterical/PrinterMods/assets/124253477/4519a3b4-95c6-4b4c-aba0-942e97ccf15c)

![image](https://github.com/Esoterical/PrinterMods/assets/124253477/f349eca1-f59b-4e35-a3f3-a5d296f3b0c0)


## Appendum

The non-purge-bucket mount may also fit on a v2.4. I've only tested in CAD, not in person, but it looks like it should fit on the left side of the gantry (but not all the way to the left, it needs to be middle-ish so it clears the bed extrusion)

![image](https://github.com/Esoterical/PrinterMods/assets/124253477/143cd000-383a-46fa-bb43-e7f360c22f73)
