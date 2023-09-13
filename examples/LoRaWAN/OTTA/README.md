Setup for AU915 for Australia 


Before you build this please make sure you have Visual Studio Code with Platfomio Install and you have restarted VS Code.
Once this is done open this project OTTA as the root folder, then down the bottom please make sure you select the board type. I have been using the T3-16.
This will pull the correct libraries.

Using Platform IO and selecting the build for the board.
LilyGo-LoRa-Series/examples/LoRaWAN/OTTA/loramac.cpp update this file with the APPEUI, DEVEUI, APPKEY This is pulled from the setup in the Things Network Console.
Please make sure you check the Endianness as this is critical

LilyGo-LoRa-Series/examples/LoRaWAN/OTTA/utilities.h uncomment out the board you are using

This has already been done is this fork:
loramac.cpp Remove the all the spectrum specifications LMIC_setupChannel() 

This has been already done to get it to build.
```
build_flags = -D LILYGO_T3_V1_6 -D CFG_au915 -D LMIC_LORAWAN_SPEC_VERSION=LMIC_LORAWAN_SPEC_VERSION_1_0_3 -D CFG_sx1276_radio=1 -D hal_init=LMICHAL_init
```
explanation:
Sets the Region AU 915Mhz freq -D CFG_au915 
Sets the Lora spec version 1.0.3, that is what the library can cope with, -D LMIC_LORAWAN_SPEC_VERSION=LMIC_LORAWAN_SPEC_VERSION_1_0_3 
Sets the radio version -D CFG_sx1276_radio=1
Fixes a compilation error where an Arduino library was being overwritten by the library -D hal_init=LMICHAL_init

This is the base Lora Library its already been added to this fork
lib_deps = mcci-catena/MCCI LoRaWAN LMIC library

This is required to get this library to work correctly 
In the LilyGo-LoRa-Series/examples/LoRaWAN/OTTA/.pio/libdeps/t3-16/MCCI LoRaWAN LMIC library/project_config/lmic_project_config.h
Update this file to have the correct geo for "#define CFG_au915 1"


