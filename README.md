# Addressable LED Strip Controller, POE Version
#### Rev 3 (see notes)

This is the repository for my LED strip controller. This LED controller is capable of controlling any addressable LED strip (1 or two data wires).

![Image of Controller](docs/controller_pic.jpg)

## Hardware Bugs

The following hardware bug exists with this version of the PCB, which will be addessed in the next revision:
- The LED data pin, IO35, is input only. Use IO32/CLK for now.
- The traces to IO16, IO17 are connected to something. Must have trace cut out.
- `E_INT` must be connected to GP0, and disconnected from IO18
- `E_RST` should be pulled down, not up
- `LED2` should have a dedicated pulldown resistor.
- The PHY chip will oscillate even if RESET is held low. Thus to turn on the strip, one must reset the ESP32 randomly until it boots

## Firmware

This controller uses the [WLED firmware](https://github.com/Aircoookie/WLED). Instructions to upload the firmware unto the board can be found on their webpage.

For this revision, there is a modified version of WLED to enable Ethernet. The diff is in [docs/rev3_patch.diff](docs/rev3_patch.diff), which is applied to commit `1dab26bcbcac051f2b7be47a2d5c757a9938bf1f`

Thru J2, you can connect an ESP32 programmer such as the ESP-Prog. You can also make your own "automatic downloader" (i.e not requiring to reset the device and selecting boot mode when uploading) circuit. Details of which can be found on Espressif's ESP-Prog docs on [Automatic Downloading Function](https://espressif-docs.readthedocs-hosted.com/projects/espressif-esp-iot-solution/en/latest/hw-reference/ESP-Prog_guide.html#automatic-downloading-function).

## Revisioning

This version was originally a continuation of my original LED controller, over at [https://github.com/Electro707/addressable_led_controller](https://github.com/Electro707/addressable_led_controller), where it was given a Rev 3 revision.

Since then, I have made another smaller non-POE controller, and thus decided to split this project into it's own repository. And thus Rev 1 and 2 does not exist for this variant, and everything starts from Rev 3.
