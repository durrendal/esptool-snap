A snap package for the esp microntroller tool, [esptool](https://github.com/espressif/esptool).

# Usage:

The following top level commands are exported as part of the snap.
```
espressif-esptool.esptool
espressif-esptool.espefuse
espressif-esptool.espsecure
```

These can be aliased to more friendly names using the following alias commands:
```
snap alias espressif-esptool.esptool esptool
snap alias espressif-esptool.espefuse espefuse
snap alias espressif-esptool.espsecure espsecure
```

The `raw-usb` `serial` and `removable-media` plugs are not automatically connected due to snap's design. These need to be manually connected before you can interact with your esp devices.

To check the connections of your snap:
```
~|>> snap connections espressif-esptool
Interface        Plug                               Slot      Notes
home             espressif-esptool:home             :home     -
network          espressif-esptool:network          :network  -
raw-usb          espressif-esptool:raw-usb          -         -
removable-media  espressif-esptool:removable-media  -         -
serial-port      espressif-esptool:serial-port      -         -
```

To connect the plugs manually:
```
~|>> sudo snap connect espressif-esptool:raw-usb
~|>> snap connections espressif-esptool
Interface        Plug                               Slot      Notes
home             espressif-esptool:home             :home     -
network          espressif-esptool:network          :network  -
raw-usb          espressif-esptool:raw-usb          :raw-usb  manual
removable-media  espressif-esptool:removable-media  -         -
serial-port      espressif-esptool:serial-port      -         -
```

After connecting the `raw-usb` or serial plug you should be able to work with your esp device as expected.
```
~|>> sudo esptool -c esp8266 -p /dev/ttyUSB0 chip-id
esptool v5.1.0
Connected to ESP8266 on /dev/ttyUSB0:
Chip type:          ESP8266EX
Features:           Wi-Fi, 160MHz
Crystal frequency:  26MHz
MAC:                48:55:19:00:93:e0

Stub flasher running.

Chip ID: 0x000093e0

Hard resetting via RTS pin...
```
