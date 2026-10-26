---
title: "Custom Keyboard"
github: "[Link to your Github Repo](https://github.com/jijiaceness/custom-keyboard)"
description: "A fully custom 55-key split mechanical keyboard built from scratch, featuring ortholinear keys and an RJ45 socket that supports hot-plugging"
created_at: "2026-08-10"
---

# August 10: Brainstorming my keyboard

I first planned my layout for my approximately 60% split keyboard with two Raspberry Pi Picos. I was inspired by keyboards I saw online and wanted to include a trackball and an OLED screen, but later I gave up on the idea as I was a beginner who was already overwhelmed by this project.
I experimented with two different thumb clusters and decided eventually on the row shown in the left sketch.

| | |
| --- | --- |
| <img src="photos/first_keeb_sketch.jpeg" style="width: 90%; transform:rotate(90);"> | <img src="photos/second_keeb_sketch.jpeg"> |


**Total time spent: 1 h**

---

# August 10: Making the schematic

This took such a long time for something that is pretty simple. I was completely new to KiCad and didn't get the workflow from schematic to PCB editor, which came back 
to bite later. I thought that I had to arrange the switches and diodes in the schematic according to the physical layout of my keys. After finally watching a tutorial, I managed
to finish the schematic and route it the Pico. 

A big mistake I made was putting the left and right sides of my keyboard in the same project.
I thought I could use mouse bites to merge them into one PCB, but that ended in failure and I spent a very long time after trying to move the right keyboard into another project
(I had to redo the whole right side basically).

<img src="photos/left_side_schematic.png">
<img src="photos/right_side_schematic.png">

This is not the final version of the schematic. I had to make a few changes when it came to putting the RJ45 socket.

**Total time spent: 3 h**

---

# August 15: Creating the configuration in the PCB Editor

Even though I struggled a lot with the schematic, making the PCB itself turned out to be much harder.

I first arranged the switches into my desired layout, but the switches weren't aligning perfectly with just Shift+M, and it took me a couple of Google Searches to discover Shift+G.
Even then, it was still difficult to get the perfect spacing since I had to rotate the column of switches first and then move them next the previous column, and Shift+G didn't really help with that since once rotated, the switches didn't align with the grid.

<img src="photos/screenshot for keeb -- kicad keyboard layout.png">
<br>

I put the diodes next to the switches (Shift+G was very useful for this) as well as the Raspberry Pi Pico.

<img src="photos/keeb - added diodes.png">
<br>

**Total time spent: 2 h**

---

# August 15: Adding the edge cut and mousebite

The process for the edge cuts was painstakingly long because of my key layout. I experimented with different shapes but eventually just decided to follow the shape of the switches.
Also, I know now that the Raspberry Pi Pico position is wrong, I later fixed it so the pink USB Cable area was outside the edge cut.

<img src="photos/kicad_edge_cut.png">
<br>

I added mouse bites to connect the sides, which ended up causing a lot of errors and not being used in the final version.

<img src="photos/keeb - added mousebites.png">
<br>

**Total time spent: 1 h 30 m**

---

# August 16: Routing and ground filling

Routing was surprisingly fun and satisfying to do, even though I had to redo all of them later after deciding to use the RJ45.

<img src="photos/keeb - finished routing both parts.png"> 
<br>

Ground filling was pretty tedious because I had to match the border to my complicated edge cut.

<img src="photos/keeb - ground filling.png">

I'm not sure if this was just an issue I was too inexperienced to fix, but I couldn't ground fill with the schematic symbol that the Keeb docs recommended because not all the GPIO pins were shown. I tried to modify the symbol, but eventually I just found a new symbol off of Github that had all the pins.

<img src="photos/new Pico symbol.png" width="30%">
<br>

**Total time spent: 3 h**

---

# August 23: Fixing the many errors from DRC

When I ran the DRC, I had so many errors (186 to be exact) and many more warnings (I'm sorry I forgot to take a screenshot).
It took many KiCad forum and Reddit rabbitholes to fix these errors (thermal spokes, Gnd zones, unconnected tracks).

The achievement I'm most proud of in this whole project: having no errors!
(warnings were all related to silkscreen due to positioning of Pico and mounting holes, which I didn't want to move)
|Left DRC|Right DRC|
| --- | --- |
| <img src="photos/left DRC.png"> | <img src="photos/right DRC.png"> |

This was also the time I realized my big mistake of not making two separate projects for the left and right PCBs.
I had to make many backup versions and restart KiCad a lot to somehow separate the two PCBs without losing all my progress.
Unfortunately, when I redid my schematic editor and updated my PCB in the PCB editor, the whole layout was lost and I basically had to redo it.

**Total time spent: Time spent (Formatting: 1 h 30m or 1 hour or 30 minutes)**

---

# September 6: Connecting the PCBs

Most split keyboards used a TRRS cable to connect the two sides, and I was going to use that too until I discovered that if you unplugged a TRRS cable accidentally while the keyboard is connected to the computer (hot plugging), you could severely damage the microcontroller.
Knowing me, I would definitely accidentally unplug the cable, so I opted for an RJ45 even though it made my 3D case a big uglier.

It took me a while to figure out how to route the RJ45, and because specific GPIO pins supported Tx and Rx, I had to move some of my columns and rows around in the schematic, resulting in having to redo all the routing.

|left RJ45|right RJ45|
| --- | --- |
| <img src="photos/left RJ45 socket layout.png"> | <img src="photos/right RJ45 layout.png"> |
<br>
I wanted to thank and credit MagoSaronno (https://github.com/MagoSaronno) who made the Keyther (https://github.com/MagoSaronno/keyther). It was really helpful seeing a public project that used the same socket, RJ45, that I wanted to use.

### Final version of schematics:
<img src="photos/final left schematic.png" width="80%">
<img src="photos/final right schematic.png" width="80%">

### Final versions of PCB:
<img src="photos/revised_left_pcb.png" width="80%">
<img src="photos/revised_right_pcb.png" width="80%">

### 3D view of PCB:
|left view|right view|
| --- | --- | 
| <img src="photos/kicad left 3D viewer front.png"> <img src="photos/kicad left 3D viewer side view.png">| <img src="photos/kicad right 3D viewer front.png"> <img src="photos/kicad right 3D viewer side view.png">|


**Total time spent: 3 h 30 m**

---

# September 10: Starting the right 3D case

It took a while for me to get used to Onshape's interface as I was completely new to CAD.
My sketches at the beginning were a mess and I had to redo them many times. Here is my final sketch, which still looks pretty complicated because of the complex shape.
<img src="photos/right base sketch.png" width="70%">
<br>

I also had issues with importing my PCB and the attached 3D models because there were too many parts. I had to manually delete most of the parts so Onshape wouldn't take a minute to load every edit I made.
<img src="photos/right PCB model onshape.png" width="70%">
<br>

**Total time spent: 2 h**

---

# September 12: Making the case and plate

I extruded my sketches and made the top plate. I didn't include the RJ45 socket in the creation of the top plate because I wasn't sure what I wanted the final case to look like with the socket as it was quite bulky.

The right case with the base and plate done:
<img src="photos/right_side_with_top_plate.png">
<br>

**Total time spent: 2 h 30 m**

---

# September 18: Starting the left 3D case

The left side was so much easier because I had ironed out all of the difficult parts when developing the right case. I was also much more experienced with using Onshape, and that sped up the process even more.
|base sketch|PCB after deleting parts|
| --- | --- |
| <img src="photos/left base sketch.png"> | <img src="photos/left PCB model onshape.png"> |
<br>

I realized that in order for my keyboard to connect to each other, all the space around the RJ45 had to be open, so I removed parts on all my case layers. That way the ethernet cable will actually be able to plug in. 

The left case with the base and plate done:
<img src="photos/left_model_in_progress.png">
<br>

**Total time spent: 2 h**

---

# September 20: Adding mounting holes

I realized that I forgot to add mounting holes, but when I tried to sketch them, I realized that my case walls were way to thin. I had to edit the base, plate, and the top to accommodate for the extra width

**Total time spent: 2 h**

---

# September 25: Outlining firmware functionality

Planning the layers I wanted for my keyboard was pretty fun. I was pretty ambitious in what I wanted my keyboard to be capable of so hopefully they will be useful when I flash my PCB and actually make use of the layers.

<img src="photos/layers_sketch.jpeg" width="60%">
<br>

**Total time spent: 30 m**

---

# September 25: Writing the Firmware in QMK

I thought this section might take a long time as well, but surprisingly, I finished writing the firmware pretty quickly. I'll definitely have to troubleshoot it when I actually get my board, but I do at least have a base to start with.

The most difficult part of writing the firmware was integrating QMK into VSCode. For some reason, the keymaps.c file kept giving errors when they weren't supposed to because VSCode didn't recognize the syntax. Somehow, I managed to get my files to work, I'm honestly still not sure what exactly was the problem. I think the extensions I installed for QMK might've been clashing with VSCodes's native syntax checker.

<img src="photos/QMK working files.png" width="30%">
<br>

Anyways, I made my project under the Lily58 directory because their keyboard seemed the most similar to mine. They used a json instead of a c file for their keymap however, so I had to look up some tutorials and other keyboards to write mine in C. This guide (https://vikasraj.dev/blog/qmk-pi-pico-rp2040) and the QMK docs were also extremely helpful for coding the connection between split keyboards with RP2040. I spent a lot of time reading the docs to understand how the info.json, layouts.h, and keymaps worked in relation to each other.

Info.json

<img src="photos/info.json_in_progress.png" width="70%">
<br>

keyboard.h

<img src="photos/keyboard.h_in_progress.png" width="70%">
<br>

Making the keymaps:

<img src="photos/keymaps_in_progress.png" width="70%">


**Total time spent: 4 h**

---

# September 27: Finalizing for Submission

I made the BOM and README all at once since I was in a bit of a time crunch (the program ends very soon at the time I'm writing this).

<img src="photos/BOM_sheet.png" width="60%">
<br>

**Finally submitted!!**

<img src="photos/submission_screenshot.png" width="40%">

**Total time spent: 3 h**

---

