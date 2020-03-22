---
layout: post
title: TTGO LoRa node connected to TTN 
date: 2020-03-03
published: false
---

<small><i>Table of contents</i></small>
* Table of contents
{:toc}

# /brief
On this project a TTGO LoRa32 module is used to log BME280 sensor data to TTN (The Things Network). 

# Motivation
* Monitor temperature, pressure and humidity data;
* Make the sensor payload available to TN using LoRa
* Server side application using NodeRED

# Hardware
* [LILY TTGO LoRa32 module](https://www.banggood.com/2Pcs-LILYGO-TTGO-LORA32-868Mhz-ESP32-LoRa-OLED-0_96-Inch-Blue-Display-bluetooth-WIFI-ESP-32-Development-Board-Module-With-Antenna-p-1507044.html?gmcCountry=CH&currency=CHF&cur_warehouse=CN&createTmp=1&utm_source=googleshopping&utm_medium=cpc_bgs&utm_content=xibei&utm_campaign=xibei-ssc-ch-en-all-1221&gclid=Cj0KCQjwmdzzBRC7ARIsANdqRRloX4zMT19MDiMRmwDUTs464G_B-Qzm2nYS19v-sgOSTIjvI-gJ47IaArarEALw_wcB);
* [BME280 sensor](https://www.banggood.com/CJMCU-280E-BME280-High-Precision-Atmospheric-Pressure-Sensor-p-1103115.html?rmmds=search&cur_warehouse=CN)

# Arduino IDE set-up
The HW module used on this project contains the ESP32 chip from espressif. One can flash this board using the Arduino IDE. The following libraries and boards need to be installed:
## >> Board
Install the **esp32** board under Arduino: With the Arduino IDE opened, go to File > Preferences. Under "Additional Boards Manager URLs" add the following line:
<p>&nbsp;</p>
```
https://dl.espressif.com/dl/package_esp32_index.json, http://arduino.esp8266.com/stable/package_esp8266com_index.json 
```
<p>&nbsp;</p>
Next go to Tools > Board > Boards Manager. Search for esp32 and install the one from espressif. Restart the Arduino IDE. 

## >> Libraries
* [OLED SSD1306 Library](https://github.com/adafruit/Adafruit_SSD1306) : drivers for the OLED display based on SSD1306 chip. 
To install it download as a .ZIP file from Github and go to Sketch > Include Library > Add .ZIP library. Install also the [GFX](https://github.com/adafruit/Adafruit-GFX-Library) drivers. 
* [LoRa SX1276 Library by sandeep](https://github.com/sandeepmistry/arduino-LoRa) : LoRa transceiver drivers.
* [Arduino-LMIC Library](https://github.com/matthijskooijman/arduino-lmic) :  IBM LMIC (LoraMAC-in-C) library, slightly modified to run in the Arduino environment, allowing using the SX1272, SX1276 transceivers and compatible modules (such as some HopeRF RFM9x modules).

<p>&nbsp;</p>
After installing the libraries restart the Arduino IDE.

