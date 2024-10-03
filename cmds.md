# USB2244 SCSI commands for EEPROM read/write

Gathered by observing the USB traffic of the [USB Drive Manager](https://www.microchip.com/content/dam/mchp/softwarelibrary/obj-files-for-usb224x/USB224X%20+%20USB225X%20v68%20Release%20Package.zip) with Wireshark.

`sg_raw` is part of [sg3_utils](https://sg.danny.cz/sg/sg3_utils.html)

## Read 

```
sudo sg_raw -r 1k /dev/sdx cf 54 03 00 40 00 00
                                    ^  ^
                                    |  |
                                    |  +- length
                                    +---- offset
```

## Write

```
sudo sg_raw -s 512 /dev/sdx cf 54 04 00 00 00 00 < eeprom.bin 
```
