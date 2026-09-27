# Keeb journal of my development process (as a complete beginner)

## Section 1: Brainstorming (1 hour)

I first planned my layout for my approximately 60% split keyboard with two Raspberry Pi Picos. I was inspired by keyboards I saw online and wanted to include a trackball and an OLED screen, but later I gave up on the idea as I was a beginner who was already overwhelmed by this project.
I experimented with two different thumb clusters and decided eventually on the row shown in the left sketch.

| | |
| --- | --- |
| <img src="photos/first_keeb_sketch.jpeg" style="width: 90%; transform:rotate(90);"> | <img src="photos/second_keeb_sketch.jpeg"> |


## Section 2: Making the schematic (3 hours)
This took such a long time for something that is pretty simple. I was completely new to KiCad and didn't get the workflow from schematic to PCB editor, which came back 
to bite later. I thought that I had to arrange the switches and diodes in the schematic according to the physical layout of my keys. After finally watching a tutorial, I managed
to finish the schematic and route it the Pico. 

A big mistake I made was putting the left and right sides of my keyboard in the same project.
I thought I could use mouse bites to merge them into one PCB, but that ended in failure and I spent a very long time after trying to move the right keyboard into another project
(I had to redo the whole right side basically).

<img src="photos/left_side_schematic.png">
<img src="photos/right_side_schematic.png">

This is not the final version of the schematic. I had to make a few changes when it came to putting the RJ45 socket.

## Section 3: Making the PCB - the hardest part (10 hours: 6 hours for making the PCB and 4 hours for the errors)
Every step of the PCB process was filled with obstacles that I had to overcome. 

I first arranged the switches into my desired layout, but the switches weren't aligning perfectly with just Shift+M, and it took me a couple of Google Searches to discover Shift+G.
Even then, it was still difficult to get the perfect spacing since I had to rotate the column of switches first and then move them next the previous column, and Shift+G didn't really help with that since once rotated, the switches didn't align with the grid.

<img src="photos/screenshot for keeb -- kicad keyboard layout.png">
<br>

I put the diodes next to the switches (Shift+G was very useful for this) as well as the Raspberry Pi Pico.

<img src="photos/keeb - added diodes.png">
<br>

The process for the edge cuts was painstakingly long because of my key layout. I experimented with different shapes but eventually just decided to follow the shape of the switches.
Also, I know now that the Raspberry Pi Pico position is wrong, I later fixed it so the pink USB Cable area was outside the edge cut.

<img src="photos/kicad_edge_cut.png">
<br>

I added mouse bites to connect the sides, which ended up causing a lot of errors and not being used in the final version.

<img src="photos/keeb - added mousebites.png">
<br>

Routing was surprisingly fun and satisfying to do, even though I had to redo all of them later.

<img src="photos/keeb - finished routing both parts.png"> 
<br>

Ground filling was pretty tedious because I had to match the border to my complicated edge cut.
I also had a lot of errors related to this because of isolated copper islands.

<img src="photos/keeb - ground filling.png">

I'm not sure if this was just an issue I was too inexperienced to fix, but I couldn't ground fill with the schematic symbol that 
the Keeb docs recommended because not all the GPIO pins were shown. I tried to modify the symbol, but eventually I just found a new
symbol off of Github that had all the pins.

<img src="photos/new Pico symbol.png">
<br>

I wish I took a screenshot at the time, but when it came to running the DRC, I had so many errors (186 to be exact) and many more warnings.
It took many KiCad forum and Reddit rabitholes to fix these errors (thermal spokes, Gnd zones, unconnected tracks).

The achievement I'm most proud of in this whole project: having no errors!
| | |
| --- | --- |
| <img src="photos/left DRC.png"> | <img src="photos/right DRC.png"> |

This was also the time I realized my big mistake of not making two separate projects for the left and right PCBs.
I had to make many backup versions and restart KiCad a lot to somehow separate the two PCBs without losing all my progress.
Unfortunately, when I redid my schematic editor and updated my PCB in the PCB editor, the whole layout was lost and I basically had to redo it (you will see that redoing things will be a continuity throughout the development of this keyboard).

Final version of schematics:
### // screenshots of final schematic

## Section 4: Making the PCB Part 2 - Connecting the PCBs (6 hours: 1.5 hours for research and 4.5 hours for editing the PCB and schematic)

Most split keyboards used a TRRS cable to connect the two sides, and I was going to use that too until I discovered that if you
unplugged a TRRS cable accidentally while the keyboard is connected to the computer (hot plugging), you could severely damage the microcontroller.
Knowing me, I would definitely accidentally unplug the cable, so I opted for an RJ45 even though it made my 3D case a big uglier.

It took me a while to figure out how to route the RJ45, and because specific GPIO pins supported Tx and Rx, I had to move some of my columns and rows around in the schematic,
resulting in having to redo all the routing.

### // screenshots of RJ45
<br>

Final versions of PCB:
<img src="photos/revised_left_pcb.png">
<img src="photos/revised_right_pcb.png">
