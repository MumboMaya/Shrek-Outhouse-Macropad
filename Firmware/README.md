This repository contains the firmware for the Shrek Macropad, a 6-key macropad built using QMK with VIA support for remapping keys.

# Overview:
QMK is used to generate the firmware and VIA is used to remap the keys without re-flashing the macropad. One the macropad is flashed with the VIA-enabled firmware, the macropad keymap can be changed using https://www.usevia.app/ in a CHROMIUM BASED browser (it will not work in non-chromium based browsers due to lack of WebHID support). At this website you can see what browsers are supported: https://caniuse.com/?search=webhid. The VIA desktop app can also be used.

# Features:
- VIA-enabled dynamic keymaps
- EEPROM-based configuration storage so that keymaps are remembered between powercycles
- Bootmagic support for resetting
- Compatible with VIA web app and VIA desktop app

# Setup Instructions:
### Install QMK:
1. Run: python3 -m pip install qmk 
2. Then once in the qmk cli run: qmk setup


#### Add the ShrekMacroPad to QMK:
1. Navigate to your QMK firmware folder: qmk_firmware/keyboards
2. Copy the ShrekMacroPad firmware folder into the keyboards folder in QMK

#### Compile the firmware:
- Run in the QMK CLI: qmk compile -kb shrekmacropad -km via
- The output firmware file is located in the build directory.

#### Flash the firmware:
1. Hold down bootsel on the RPI pico and plug it into your computer. When the device shows up as a mass storage device, open it and drag the .uf2 file into the mass storage device. The device will disconnect from your computer and the - - RPI Pico will reset and attach itself as a HID device.


#### Connect the MacroPad to the VIA app website:
After plugging the macropad in, go to https://www.usevia.app on a supported browser (you can check what browsers are supported here: https://caniuse.com/?search=webhid), and click “Authorize device” and select the ShrekMacroPad in the window that pops up.

#### Define the layout in the VIA app website:
1. Go to settings
2. Enable Show Design Tab
3. Open Design Tab
4. Click Load
5. Upload the shrekmacropad_via.json file. This configures the VIA app with the layout of the shrek macropad

#### Remap keys:
- Click keys in VIA to remap them
- Changes are applied instantly
- No reflashing needed

# How the code/configuration works:
The firmware has two main parts: the keyboard definition and the keymap.

## keyboard.json
This file describes the hardware configuration, metadatam and setup for the Macropad.

It tells QMK:
- the keyboard name and maintainer
- which MCU the board uses
- which bootloader it uses
- which features are enabled
- how the switches are wired
- how the physical layout maps to the matrix
- the USB vendor and product IDs
- processor and bootloader tell QMK that this board is built around the RP2040 and uses the RP2040 bootloader.
- features enables optional QMK features such as Bootmagic, media keys, mouse keys, and NKRO.
- matrix_pins.direct tells QMK that the macropad uses a direct matrix instead of a traditional row/column scan. Each entry is a GPIO pin connected directly to a key.
- layouts tells QMK where the keys are physically placed
- usb defines the USB identity for the board

#### keymap.c
This file defines what each key does by default.
- keymaps is the array of all layers
- [0] is the default base layer
- LAYOUT[.....] places keys in the same order as defined in keyboard.json

#### keymaps/via/rules.mk
This enables VIA

#### keymaps/via/keymap.c
This is the default keymap that gets flashed with the VIA firmware.

Important detail: once VIA is used, the live keymap is stored in EEPROM on the keyboard. That means this file becomes the starting layout, but later changes are usually made through VIA instead of editing and reflashing the firmware itself.

