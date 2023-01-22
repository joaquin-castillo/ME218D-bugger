# ME218D-bugger
Design files and documentation for the ME 218 D-bugger. The D-bugger is a tool for ME 218 student students to monitor and visualize the Events and Services Framework.

## PCBA fabrication and assembly
### Fab House
We had [JLCPCB](https://jlcpcb.com/) fabricate the boards and assemble the bottom sides. We elected to solder the top sides ourselves because, in addition to the three thru-hole components, there are only four 1206 SMD components on the top sides, and having both sides assembled with have cost significantly more. 1206 SMD packages are not difficult to solder by hand with the right equipment. If you are new to SMD soldering, see this [Intro to Soldering](https://sites.google.com/stanford.edu/soldering-internal/learning?authuser=0) tutorial page to learn the basics and best practices of hand soldering. A lesson we learned was to avoid no-clean solder flux and opt for water-soluble solder flux instead. This can be cleaned with isopropyl alcohol (at least 90%) or water and will not leave the board sticky and goopy after soldering.

The fabrication files needed to place an order with JLC are listed below:
- *Intermediary_revC_fab_20221219.zip*
- *Intermediary_revC_jlc_bottom.csv*
- *Intermediary_revC_4layer-bottom-pos.csv*

If for any reason you need to regenerate the fab files, JLC has some tutorials on [How to generate Gerber and Drill files](https://support.jlcpcb.com/article/194-how-to-generate-gerber-and-drill-files-in-kicad-6) and [How to generate the BOM and Centroid file](https://support.jlcpcb.com/article/84-how-to-generate-the-bom-and-centroid-file-from-kicad) specifically for KiCAD. The BOM and centroid file (aka pick and place file) are used for component assembly. In our experience, getting the centroid file in the right position and orientation relative to the board preview in JLC's quoting tool was a little finicky. This doesn't have to be perfect as JLC will have an engineer look at your files and correct anything before you approve the order. Something else to note is that for assembly, JLC requires some non-plated tooling hole to be added to the board for their processes. These have already been added to the design, but in case you want to see their requirements, that can be found on this page: [How to add tooling holes for PCB assembly order](https://support.jlcpcb.com/article/92-how-to-add-tooling-holes-for-smt-assembly-order).

### In House
Upon receiving the board from the fab house, they will still require a few components to be hand soldered. This includes:
- DIP-28 Socket (for the PIC)
- 3-pin header
- USB C receptacle
- 1206 SMD Green LED
- 1206 SMD Blue LEDs x2
- 1206 SMD 620 Ohm resistor

These can be found in the *Intermediary_revC_BOM.xlsx* file with links for DigiKey. The image below shows all seven components to be hand soldered:

<img src="/assets/hand_soldering.jpg" alt="hand_soldering" style="width:300px">


Additionally, the boards must be configured at assembly to work with either the CP2102N serial bridge, or the PIC32's native USB. To do this, simply create solder bridges on the three jumper pads on the back side of the board as shown below:

<img src="/assets/solder_jumpers.png" alt="solder_jumpers" style="width:300px">

To reconfigure the boards in the future, simply wick away the solder bridges and resolder the opposite pads.

## Enclosure


## Firmware
### PIC32 Microcontroller
The PIC needs to be programmed with the latest version of the D-bugger firmware. The latest firmware can be found [here]. Using a breadboard or ZIF socket, program the PIC with the SNAP programmer through MPLAB.

### CP2102N Serial Bridge
Though the serial bridge will work out-of-the-box, it should be configured to enable the RX and TX toggle LEDs, which are disabled by default. These LEDs are helpful for troublshooting communications issues from the target or to the host.

To do this, you must download Silicon Lab [Simplicity Studio](https://www.silabs.com/developers/simplicity-studio) and install it on your computer. You may also be asked to create an account. Once installed, (to be continued...)
