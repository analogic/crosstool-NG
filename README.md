# CrossTool-NG

![ESP8266 Module](https://mcuoneclipse.files.wordpress.com/2014/10/esp8266-module.png?w=584&h=552)
 
ESP8266 is a complete and self-contained Wi-Fi network solutions that can carry software applications, or through Another application processor uninstall all Wi-Fi networking capabilities. ESP8266 when the device is mounted and as the only application of the application processor, the flash memory can be started directly from an external Move. Built-in cache memory will help improve system performance and reduce memory requirements. Another situation is when wireless Internet access assume the task of Wi-Fi adapter, you can add it to any microcontroller-based design, the connection is simple, just by SPI / SDIO interface or central processor AHB bridge interface. Processing and storage capacity on ESP8266 powerful piece, it can be integrated via GPIO ports sensors and other applications specific equipment to achieve the lowest early in the development and operation of at least occupy system resources. The ESP8266 highly integrated chip, including antenna switch balun, power management converter, so with minimal external circuitry, and includes front-end module, including the entire solution designed to minimize the space occupied by PCB. The system is equipped with ESP8266 manifested leading features are: energy saving VoIP quickly switch between the sleep / wake patterns, with low-power operation adaptive radio bias, front-end signal processing functions, troubleshooting and radio systems coexist characteristics eliminate cellular / Bluetooth / DDR / LVDS / LCD interference.

Online community http://www.esp8266.com and https://nurdspace.nl/ESP8266 supporting all aspects of the ESP8266 and ESP8266EX. For more info see the wiki https://github.com/esp8266/esp8266-wiki/wiki

This is a prebuild toolchain with every step from:
 * https://github.com/esp8266/esp8266-wiki/wiki/Toolchain
 * https://github.com/esp8266/esp8266-wiki/wiki/Building
 * https://github.com/esp8266/esp8266-wiki/wiki/Uploading
 * https://github.com/nodemcu/nodemcu-firmware

To start this image simply use:

```
$ docker run -ti --privileged marcelmaatkamp/esp8266-crosstool-ng:latest /bin/bash
```

Then test your setup by uploading the example code:

```
$ cd /opt/Espressif/source-code-examples/blinky
$ make ESPPORT=/dev/ttyUSB0 flash
```

The nodemcu firmware can be found in:

```
/opt/Espressif/nodemcu-firmware$ find . -name '*.bin'

./pre_build/0.9.2/512k-flash/nodemcu_512k_20141212.bin
./pre_build/0.9.2/512k-flash/nodemcu_512k_20141219.bin
./pre_build/0.9.2/512k-flash/blank512k.bin
./pre_build/0.9.2/1M-flash/nodemcu_1M_20141219.bin
./pre_build/0.9.2/4M-flash/esp_init_data_default.bin
./pre_build/0.9.2/4M-flash/eagle.app.v6.flash.bin
./pre_build/0.9.2/4M-flash/blank.bin
./pre_build/0.9.2/4M-flash/eagle.app.v6.irom0text.bin
./pre_build/0.9.2/2M-flash/esp_init_data_default.bin
./pre_build/0.9.2/2M-flash/eagle.app.v6.flash.bin
./pre_build/0.9.2/2M-flash/nodemcu_2M_20141219.bin
./pre_build/0.9.2/2M-flash/blank.bin
./pre_build/0.9.2/2M-flash/eagle.app.v6.irom0text.bin
./pre_build/0.9.4/512k-flash/nodemcu_512k_20141222.bin
./pre_build/0.9.4/512k-flash/blank512k.bin
```

To flash the firmware into the ESP8266 module via USB2Serial:

```
$ ./esptool.py --port /dev/ttyUSB0 write_flash 0x00000 0.9.4/512k-flash/nodemcu_512k_20141222.bin
```

To validate, connect with the ESP8266 via serial and send commands:

```
miniterm.py /dev/ttyUSB0 9600

>> node.restart();
NodeMcu 0.9.4 build 20141222  powered by Lua 5.1.4
>>
```
