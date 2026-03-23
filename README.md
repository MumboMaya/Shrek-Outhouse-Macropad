# Shrek--Outhouse-Macropad
The  Shrek's Outhouse Macropad is a 2x3 Macropad that looks like Shrek’s outhouse. It was made to make everyday tasks, such as switching tabs, easier. It is also designed to be used as a device that can be set to do anything, for example, starting a recording in OBS.

# Features
- 6 programmable keys
- USB-C support
- Modelled after Shrek’s outhouse with its features, such as the crescent moon 

# CAD Model
Everything fits together using X4 M3x18 Bolts and x4 M3 nuts

My CAD Model has 3 different 3D printable parts. After putting together the bottom and middle part you pust then insert the PCB and then wire all your components. Once that is finished, you can place the top cover.  This Macropad holds 6 differenrt programable keys. 

![CAD](./images/CAD.jpeg)
![CAD](./images/CAD-Construction.jpeg)


# PCB
Here is my PCB, it was made using Kicad!

Schematic:

![Schematic](https://github.com/user-attachments/assets/64e60fb1-c5e6-4fd6-90ad-42f65683e301)


PCB:

![PCB](https://github.com/user-attachments/assets/187f7447-1bfa-44f2-85ed-bc6b744c3ae3)


# Firmware Overview
*A short description of the keyboard/project*

* Hardware Supported: *The PCBs, controllers supported*
* Hardware Availability: *Links to where you can find this hardware*

Make example for this keyboard (after setting up your build environment):

    make shrekmacropad:default

Flashing example for this keyboard:

    make shrekmacropad:default:flash

See the [build environment setup](https://docs.qmk.fm/#/getting_started_build_tools) and the [make instructions](https://docs.qmk.fm/#/getting_started_make_guide) for more information. Brand new to QMK? Start with our [Complete Newbs Guide](https://docs.qmk.fm/#/newbs).

## Bootloader

Enter the bootloader in 3 ways:

* **Bootmagic reset**: Hold down the key at (0,0) in the matrix (usually the top left key or Escape) and plug in the keyboard
* **Physical reset button**: Briefly press the button on the back of the PCB - some may have pads you must short instead
* **Keycode in layout**: Press the key mapped to `QK_BOOT` if it is available

# BOM
Here is everything you will need to make this macropad!

- X6 DSA Keycaps
- X6 Cherry MX Switches
- X4 M3x18 bolts
- X4 M3 nuts
- X1 RaspberryPI-Pico
  






