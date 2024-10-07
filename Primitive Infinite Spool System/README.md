# Primitive Infinite Spool System (PISS)

**This is a work in progress, stuff will change or get added/removed at random**

I wanted an infinite spool system, but didn't want to buy all the stuff for an ERCF or Tradrack or whatever. So I used stuff I arleady had on hand.

I also wanted to use HappyHare to control it, but at the moment (March 2024) this hardware configuration isn't supported.

So I went on a journey to cobble together the hardware I had and create an all-macro-based system (no plugins) for Klipper to enable a basic Infinite Spool system using two spools.

In total, this system uses:

- Two extra "pre-feed" extruders, one for each spool. You can use whichever type of extruder you like, it doesn't matter as long as it can push filament
- Four basic filament sensors, one each above the pre-feed steppers and one each below the pre-feed steppers
- A speed control system to keep the currently in use pre-feed stepper in sync with the main extruder. Something like the [Annex Belay](https://github.com/Annex-Engineering/Belay) can work, though the controls are now built in to the P.I.S.S. macros so you don't need the Belay plugin.
- An optional encoder_sensor filament sensor. This isn't strictly needed but it's always nice to have something that will detect a jam. Also usefull for detecting when a spool has reached the end but the end of the filament is snagged on the spool itself.
- An extruder with integrated pre-and-post gear filament sensors (or just a post-gear sensor and adding a seperate filament sensor as close as possible to the extruder)

What you use for this stuff is up to you. HartK has a [Dual-Nightwatch](<https://github.com/hartk1213/MISC/tree/main/Voron%20Mods/Extruders/Dual_Nightwatch>) design that incorporates pre-and-post stepper sensors which works really well, and I've designed a combined [Y-Splitter and Binky encoder and speed controller](./STL/BinkaY) unit which combines a [Binky encoder](<https://github.com/mneuhaus/EnragedRabbitProject/tree/main/usermods/Binky>), a Y-splitter, and a speed controller (inspired by the Belay functionality).
I've also got a small collection of [dual-filament-sensor extruder designes](<https://github.com/Esoterical/PrinterMods/tree/main/Filament%20Sensor%20Extruders>) as well as CAD model you can use to add a filament sensor to almost anything.

But no reason you can use standalone "just a microswitch" filament sensors placed at spots along the bowden path. Even with the final extruder the system should work fine with only a "pre-extruder" sensor which can be another standalone one just stuck on the bowden.

For the encoder_sensor, something like a BTT SFS or the ERCF encoder sensors would work (I use the [ERCFv1 encoder sensor](https://www.printables.com/model/389504-ercf-smart-filament-motion-sensor) or a Binky would work), but again you can omit this entirely if you like. You just lose "jam" detection.

![image](https://github.com/Esoterical/PrinterMods/assets/124253477/c60e5484-5af5-461d-abd2-52978d4fe428)
