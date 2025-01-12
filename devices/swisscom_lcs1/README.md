## Swisscom LCS1 Smart Switch

Thanks to Patrick Frey for sponsoring me the Swisscom Smart Switch :-)

![Swisscom Smart Switch](images/Swisscom_Smart_Switch.jpg)

The Swisscom Smart Switch can be thought of as the little brother, the myStrom WLAN Switch which uses an ESP32 chip.
But instead of the ESP32 soldered chip the Swisscom Smart Switch uses an ESP-WROOM-02D module and has no temperature sensor and no circuit for measuring the power consumption.

### Opening the case

For opening the case it is best to use a Torx T10 screw driver where three edges have been grinded off to match the triangle shape of the screws. When putting it back together remember that the longer screws are at the bottom of the WLAN switch:

![Swisscom Smart Switch](images/Screws.jpg)

### Main PCB

The main PCB contains the pwoer supply curcuit for delivering 5V for the relay and 3V3 for the ESP-WROMM-02D module. Also soldered is a push button at the side and two small LEDs (red/white) at the bottom of the PCB. The ESP_WROOM-02D module itself is soldered onto a small PCB which then is soldered through a slot onto the main PCB.

The pinout looks like:

    3V3
    GND
    LED white
    LED red
    Relay
    Psuh button

![Swisscom Smart Switch Pinout](images/PCB_Pinout.jpg)

### ESP-Wroom-02D module

Gladly the ESP-WROOM-02 module PCB contains headers for flashing. You could either use an isolated 230V AC transformer for powering during flashing or pwoer the ESP-WROOM-02D externally from a 3V3 power supply. But beware that most 3V3 UART adapters can't handle the required current for flashing.

![Swisscom Smart Switch Pinout](images/Wroom_Pinout.jpg)

Flashing with a cheap 3V3 UART FTDI adapter:

![Swisscom Smart Switch Pinout](images/Flashing.jpg)

    TxD = RxD FTDI (yellow)
    RxD = TxD FTDI (orange)
    GND = GND FTDI (black)
    +3.3V = +3.3V FTDI (red)

GPIO0 and GND shorten during power on 

### ESPHome file

Attached is the lcs1.yaml file for compiling ESPHome and has the follwoing fcuntionalities:

    Remotely toggle relay
    Toggle relay with push button
    Red LED toggles according to relay state
    White LED switches on when device is connected to WLAN

But feel free to change the file to your needs.

Happy ESPHoming ;-)

