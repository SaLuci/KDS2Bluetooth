# KDS2Bluetooth
Kawasaki/Suzuki Diagnostic Service Reader via Bluetooth

Using an ESP32 to read parameter from a Kawasaki/Suzuki motorcycle by it´s diagnostic system.
Requests can be submittet via bluetooth, by any ELM327 compatible device/application. Such as Android App [Torque Lite](https://play.google.com/store/apps/details?id=org.prowl.torque&hl=de), [Car Scanner ELM OBD2](https://play.google.com/store/apps/details?id=com.ovz.carscanner&hl=de), 
action cameras like "Garmin Virb X / XE" or other solutions, which are able to communicate with an OBD II Bluetooth Adapter.
For racetrack usage, I can recommend [Racechrono](https://racechrono.com/)

### Repository
* [Bike_Diagnostic_System](https://github.com/SaLuci/KDS2Bluetooth/tree/master/Bike_Diagnostic_System)    - Arduino Sketch -> Full solution (new)


### Protocol:
KDS Bus via K-LINE (*Diagnostic plug*).
In my case KWP2000 (*ISO-14230*)

### Hardware:
* ESP32
* L9637D
* Ceramic-Capacitor 10 nF 50 V/DC
* 510Ohm Resistor




### Software:
This has to be splitted into three parts:

#### AT-Communication:
Nearly all bluetooth OBD dongles are using an ELM327 chip, or a similar, cheap china clone.
This is controlled/setup via "AT"-commands. They describe the format how data is transmitted, timing, reset the device or return protocol information.

#### KDS-Communication:
Connection to the kawasaki diagnostic system. How the Arduino speaks to the Bike.
Based on the great work of Tom Mitchell (*[Kawaduino](https://bitbucket.org/tomnz/kawaduino/overview)*).

#### Translations:
Every ELM327 compatible device is using the stock [OBD II protocol](https://en.wikipedia.org/wiki/OBD-II_PIDs) and its Protocol ID´s (*PID*).
The bike is also using a similar communication. But the PID´s doesn´t mean the same, nor is the calcualtion equal.
In that conclusion, the requested PID has to be translated into the according pendant and the result has to be calculated,
to fit into the OBD ranges.


### The most influential Tutorials/sources:
[KDS Protocol](https://web.archive.org/web/20201202041417/https://ecuhacking.activeboard.com/t56234221/kds-protocol/) (inactive ecuhacking.activeboard via archive.org)

[Kawaduino](https://github.com/tomnz/kawaduino)

[ELM327 AT Commands](https://www.elmelectronics.com/wp-content/uploads/2016/07/ELM327DS.pdf)

[OBDuino](https://en.wikipedia.org/wiki/OBDuino)

[Original KDS2Bluetooth](https://github.com/HerrRiebmann/KDS2Bluetooth) (by [TriB](https://github.com/HerrRiebmann))



