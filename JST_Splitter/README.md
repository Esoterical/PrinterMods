# A simple 1 to 2 JST splitter for dual-part-fan toolheads

This is a splitter that turns one fan header into two. It makes it much simpler for wiring up toolheads that have two part cooling fans (Dragonburner, Xol, etc).

There are two types of the main body. One designed to fit in the space on an EBB36 CAN board where the PT100/1000 DIP switches would be for the boards that *don't* have the MAX31865 chip, and one designed to sit to the side for boards that *do* have the MAX31865 chip and DIP switches/port.

Non-MAX31865 version:

![image](https://github.com/Esoterical/PrinterMods/assets/124253477/4bc72cfb-f552-431e-94dd-9f8764c90bf4)

MAX31865 version:

![image](https://github.com/Esoterical/PrinterMods/assets/124253477/1c847791-8f76-44ff-91db-8d2f34b091aa)

Both versions use the same inserts, and there are  2 insert options either for JST-XH (2.54mm pitch) or JST-PH (2mm pitch)

![image](https://github.com/Esoterical/PrinterMods/assets/124253477/c67ac6f3-aa1e-491f-b440-45a6a607c099)

Simply slide the two JST headers into the insert, then solder wires to the connectors and crimp a JST-XH onto the end of this wire to then connect to the EBB board header.

I then use a glob of hot glue to secure the JST "insert" into the main body.

![image](https://github.com/Esoterical/PrinterMods/assets/124253477/ea7fdd76-5e53-4b18-8a90-4a2689ba64e0)
