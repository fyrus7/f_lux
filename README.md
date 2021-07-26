Original by https://github.com/PhotoChemicals/f_lux

I did some "reverse engineering" so anyone can easily build this. I saw some lightmeters similar to this going from 150USD up. My guess is that its something really similar to this.

# Hardware:
- Arduino UNO ( or nano or any other AtMega328P arduino formfactor)
- I^2C OLED 128x64px
- Rotary encoder with switch/button
- Adafruit TSL2591 light sensor - https://www.adafruit.com/product/1980 

[DO NOT BUY TSL2561!! Only the model from link above or from aliexpress. There is a different driver software and it is no longer made]


# How to connect:

OLED:
- VCC to 5V
- GND to GND
- SCL to A5
- SDA to A4

Rotary encoder:
- VCC to 5V
- GND to GND
- SW to Digital pin 3
- DT to A1
- CLK to A0

TSL2591 sensor:
- VCC to 5V
- GND to GND
- SCL to A5
- SDA to A4
- (do not connect remaining pins)

# Software changes:
There is no need to change anything for rotary encoder and the light sensor.

For OLED you may need to change the address on line 508  of the main sketch. Address for 128x64 OLED should be 0x3D, however for me it was 0x3C which is still set in the sketch.

# Libraries:

All libraries are now included as zip in this repository. No need to download anything off the library manager. 
~~[Download Adafruit_GFX from library manager say yes to download other support libraries.]~~

Rest of the libraries are included as ZIP files in this repository. Install them. There is change in one of them to make it work (for me at least).

# SCREEN NOT WORKING RIGHT?
For whatever reason when I connected the screen, it would treat it as 128x32 and would leave every second row blank. That resulted in seeing only half of the screen UI. Change is in library Adafruit_SSD1306.h. On line 28 I enabled #define SSD1306_128_64 and on line 29 I disabled //#define SSD1306_128_32. If you have some sort of problem and cant see images on screen in the correct aspect ratio try to switch it back. Also make sure you really have 128x64px display and you have the correct address set!!

# Case
Planing to print one and Ill add the STL when Im done.


# Thats it!
Enjoy your lightmeter.



# ƒLUX
Arduino Light Meter

This is my Arduino light meter project. The goal was to build a portable, low-power light meter for photography and cinematography.

I used an Adafruit TSL2591 High Dynamic Range Light Sensor (https://www.adafruit.com/product/1980), an Arduino Pro Mini, a 128x64 I2c OLED Display, a push-button a rotary encoder, and three AAA batteries.

Here's a video: https://www.youtube.com/watch?v=WcZG9v7m2E0
