# My Custom Keyboard: Overview

This is a fully custom 53-key split mechanical keyboard built from scratch, from the PCB to the 3D-printed case, developed with the support of Hack Club Program Keeb. 
I came into this project with almost no knowledge of how a keyboard works or the parts it consisted of, and over this two-month journey, I learned how to make all the components to make a fully functional keyboard.

## Features
- Unique split keyboard layout
- Ergonomic ortholinear and column-staggered keys
- RJ45 socket connecting the two sides that supports hot-plugging
- 3D-printed top mount case with a base, plate, and top frame
- QMK firmware support with 3 custom layers

## Why I Built It

I've been wanting a split keyboard for a while after typing for hours on my laptop and experiencing hand pain and cramps. Mechanical keyboards have always appealed to me, and the Hack Club program Keeb was a great opportunity for me to build my own while learning the inner workings of a keyboard. I also liked the idea of how customizable my own keyboard would be as I could code what each key does instead of relying on the build-in funcitonality.

## What I Learned

Again, I came into this endeavor with no idea what a switch even was, so I most likely learned more from building this keyboard than in any of my year-long classes at school. 

I learned ...
- What a PCB actually does and its relation to a microcontroller
- How to make a PCB from scratch
- How to use Onshape and how to 3D-design with parametric modeling
- The different parts of a keyboard (switches, diodes, stabilizers, sockets, microcontroller, etc.)
- The software that makes your computer actually recognize and process keyboard input
- How to write the software and tailor it to my design
    - The relation between keymaps.c, keyboard.h, and info.json was particularly interesting; I didn't know that the matrix in info.json was based on the physical positioning of the switches

## Challenges

The biggest challenge was definitely getting used to the applications (KiCad and Onshape) and their workflow. Not understanding the right sequence and way to do things, even with the help of Keeb's guide, cost me many hours of redoing things and searching into the depths of the internet to fix.

  For KiCad, I didn't really finalize my layout on the schematic before moving onto the PCB editor and also put my left and right PCB on the same project, which goes against KiCad's method of designing PCBs.

  For Onshape, I had no idea how to properly constrain my sketches, and my first iterations were filled with haphazard lengths and angles. I probably redid my sketch 10 times while designing the case. I do feel proud now in how far I've come in CADing since the beginning, and my sketches are much cleaner now.

# Keyboard Overview

## Schematic
### Left schematic
<img src="photos/final left schematic.png" width="80%">

### Right schematic
<img src="photos/final right schematic.png" width="80%">

## PCB
<img src="photos/revised_left_pcb.png" width="80%">
<img src="photos/revised_right_pcb.png" width="80%">

### 3D view
|left view|right view|
| --- | --- | 
| <img src="photos/kicad left 3D viewer front.png"> | <img src="photos/kicad right 3D viewer front.png"> |


## Case
### Left Case

### Right Case

# Bill of Materials (BOM)

|Item|Name                        |Quantity|Notes                                             |Cost (USD)|
|----|----------------------------|--------|--------------------------------------------------|----------|
|1   |Raspberry Pi Pico           |2       |SC0916                                            |$7.82     |
|2   |Left PCB from JLCPCB        |1       |                                                  |$13.8     |
|3   |Right PCB from JLCPCB       |1       |                                                  |$13.8     |
|4   |Cherry MX Switches          |54      |70 count, Orange key switch.                      |$16.8     |
|5   |1N4148 Diodes               |54      |100 count                                         |$3.91     |
|6   |M3xD4.6xL3.0 heatset inserts|52      |100 count                                         |$5.18     |
|7   |M3x5mm screws               |7       |50 count                                          |$2.56     |
|8   |M3x14mm screws              |6       |50 count                                          |$3.54     |
|9   |RJ45 Shield Network Jack    |2       |Comes in pack of 2, RJHSE-XM80                    |$3.82     |
|10  |Micro USB to USB-A Cable    |1       |1m                                                |$2.6      |
|11  |USB-A to USB-C adapter      |1       |                                                  |$3.45     |
|12  |Rj45 Connector              |1       |0.5m                                              |$4.37     |
|13  |DSA Blank Custom Keycaps    |62      |85 pcs (any keycaps bigger than 1u counts as 2 pcs|$32.94    |
|14  |                            |        |                                                  |          |
|    |TOTAL                       |        |                                                  |$114.59   |

# Credits

This project was possible due to the numerous open-source projects and resources, especially the [the keyther by MagoSaronno](https://github.com/MagoSaronno/keyther/tree/main) as well as many other detailed in the journal. Finally, thank you to Hack Club Keeb for providing the guides and opportunity for me to build a keyboard!
