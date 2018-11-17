# Altium Designer Notes and PCB Design Guidelines
How to design a standard PCB layout using Altium Designer
<br />**This document is currently in a work in progress.**

<p align="center"> 
<img src="https://www.altium.com/altium-designer-coming-soon/theme/images/AD_FirstScreen_X2_black.png">
</p>

## Table of Contents
- General Information
- [Shortcut Keys](#shortcut-keys)
- Components
- [Schematics](#schematics)
- [Setup Before Layout](#setup-before-layout)
  - [Rules](#rules)
  - [Stackup](#stackup)
  - [Set Net Colors](#set-net-colors)
- Placement
- Layout
- High Speed Tips

## Shortcut Keys

All Altium Designer Shortcut Keys [[Download](http://valhalla.altium.com/Learning-Guides/Legacy/GU0104%20Shortcut%20Keys.PDF)]
### Schematic Designer
- **General**
   - `Ctrl + M`: Measure.
   - `C + C`: Compile the active project.
   - `D + U`: Update the PCB with any schematic changes.
   - `D + O`: Open the “Document Options” window.
   - `Q`: Toggle the measurement unit system between metric and imperial.
   - `T + C`: Cross-probe a net, pin or component between the schematic and the PCB.
- **Schematic Routing**
   - `P + W`: Start placing wires.
- **Component Placement**
   - `J + C`: Jump to component.
   - `J + N`: Jump to net.
   - `T + A + A`: Open the “Annotate” window.
   - `T + A + U` Open the “Quick Annotate” window.
### PCB Designer
- **General**
   - `D + I`: Import changes from schematic to PCB.
   - `T + D + R`: Run DRC (Design Rule Checks).
   - `Q`: Toggle the measurement unit system between metric and imperial.
   - `T + C`: Cross-probe a net, pin or component between the schematic and the PCB.
- **Routing**
   - `P + T`: Begin routing a track. 
   - `Tab` (while routing): Brings up routing options/properties windows.
   - `Shift + Space`: Change the track routing style (e.g. from straight to 45 to curved and back again).
   - `Shift + W`: Set the track width to something from the predefined track width list.
   - `T + G + A`: Repour all polygons.
- **Component Placement**
   - `L`: Flip a component.
   - `Spacebar`: Rotate object by 90°.
   - `J + C`: Jump to component.
   - `Ctrl + Shift + C`: Align horizontal centers.
   - `Ctrl + Shift + T`: Align horizontal tops.
   - `Ctrl + Shift + B`: Align horizontal bottoms.
   - `Ctrl + Shift + V`: Align vertical centers.
   - `Ctrl + Shift + L`: Align vertical lefts.
   - `Ctrl + Shift + R`: Align vertical rights.
   - `E, M, M`: Move component (useful for when you can’t select it because it’s ontop of other components).
- **Visualisation**
   - `Shift + S`: Hide all but selected layer.
   - `V + B`: Flip board.
   - `MouseScroll`: Move up/down.
   - `Shift + MouseScroll`: Move left/right.
   - `Ctrl + MouseScroll`: Zoom in/out.
   - `Ctrl + M`: Measure.
   - `+`/`-`: Increment/Decrement through the enabled layers.
   - `*`: Increment/Decrement through routing layers only.
   - `S + S` or `Ctrl + H`: Enables you to select a section of connected copper. Stops the selection at a via, pad or intersection.
   - `D + T + <letter>`: Select a view configuration. These views and their key shortcuts are user configurable.
     - `D + T + U`: Selects the “up” configuration (all top layers).
     - `D + T + D`: Selects the “down” configuration (all bottom layers).
   - `D + O`: Open Board Options window.
   - `Ctrl + G`: Open the Grid Editor window.
   - `L`: Show the Layers dialog box to adjust the visible layers and/or enable/disable layers.
   - `G`: Cycle through the predefined grids.

## Schematics

- Draw circuits from **left to right** and **top to bottom**.
- Draw circuits in functional block and use **Net Labels** for connecting blocks to each other.
- Use **standard designators**:
   - IC: IC or U
   - Resistor: R
   - Capacitor: C
   - Inductor: L
   - Transistor: Q or T
   - Diode/LED: D
   - Crystal: Y/XTAL
   - Pin headers: J
   - Jumper: JP
   - Fuse: F
   - Ferrite Bead: FB
   - Fiducial: FD
   - Test point: TP
- Add the **Cover Page** to the schematic:
   - Project name
   - Date
   - Re/version number
   - All the names of schematics
   - Notes legend
   - Company information
   - Schematic status with date (Draft, Preliminary, Checked, Released)
      - Draft: Blocks, just the structure of the schematic.
      - Preliminary: Connections done, Quiet close to final.
      - Checked: No mistakes in schematic.
      - Released: PCB sent for fab.
- Don't connect 4 wires at one junction.
- Place all labels, designators, pins, text etc. **horizontally**.
- **Don't fill up** the whole sheet.
- Name schematics with **clear** and **short** name.
    - For example: Use CPU_HDMI and CPU_LVDS instead of CPU1 and CPU2.
- Use "**+...V...**" for power nets
    - **Never use "VCC" as net name!**
    - For example: +12V, +5V, +3V3, +2V5, and etc.  
- **Fill information** in Title block.
- Use **distinctly** and **clear** names for schematics.
- Add useful **Design Notes** on the schematic.
- If you suspect that there are parts in the circuit, place them. If you do not need them, you can remove them later!
- **Double check** RX & TX pins.
    - **Never use "TX" & "RX" as net name alone!**
    - For example: Use MCU_TX or GPS_RX instead of TX or RX alone!
- Put enough and useful Test Points (TPs) for circuit debugging.
- Place components in the schematic **close to the pins** where they should be located on PCB.
    - For example: bypass capacitors.
- Generate **PDF** of the completed schematic.

## Setup Before Layout

### Rules
- **Clearance**
   - `D + R > Design Rules > Electrical > Clearance`
   - Clearance = 0.2 mm  
- **Routing**
   - `D + R > Design Rules > Routing > Width`
   - Min Width = 0.3 mm
   - Preferred Width = 0.3 mm
   - Max Width = 0.5 mm
   - `D + R > Design Rules > Routing > Width_PWR`
   - Min Width (PWR) = 0.4 mm
   - Preferred Width (PWR) = 0.4 mm
   - Max Width (PWR) = 4 mm
   - `D + R > Design Rules > Routing > Routing Via Style`
   - Via Diameter = 0.6 mm
   - Via Hole Size = 0.3 mm
- **Mask**
   - `D + R > Design Rules > Mask > Solder Mask Expansion`
   - Solder Mask Expansion = 0.1 mm
- **Manufacturing**
   - `D + R > Design Rules > Manufacturing > Hole To Hole Clearance`
   - Hole to Hole Clearance = 0.3 mm
   - `D + R > Design Rules > Manufacturing > Minimum Solder Mask Silver`
   - Minimum Solder Mask Silver = 0.3 mm
   - `D + R > Design Rules > Manufacturing > Silk to Solder Mask Clearance`
   - Silk to Solder Mask Clearance = 0.1 mm
   - `D + R > Design Rules > Manufacturing > Silk to Silk Clearance`
   - Silk to Silk Clearance = 0.1 mm
- **Placement**
   - `D + R > Design Rules > Placement > Component Clearance`
   - Component Clearance (Vertical) = 0.2 mm
   - Component Clearance (Horizontal) = 0.2 mm
- **Via** 
  - `DXP > Prefs > PCB Editor > Defaults > Via`
  - Via Diameter = 0.6 mm
  - Via Hole Size = 0.3 mm

### Stackup
- `Design > Layer Stack Manager`
- Change Layer Names to L1 and L2, and etc.
- Thickness of Dielectric (PCB Thickness) = 1.6 mm

### Set Net Colors
- `View > Panels > PCB`
- `PCB Panel > "Net Name" > Right-Click > Change Net Color`
- `PCB Panel > "Net Name" > Right-Click > Display Override > Selected ON`
- Net Color for GND = Blue (236)
- Net Color for +5V = Orange (4)
- Net Color for +3V3 = Pink (1)
- `F5` = Toggle Net Colors


