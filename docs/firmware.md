# Overview

The firmware is written in C++, using the PlatformIO IDE within VsCode, and using the Arduino framework. The firmware currently targets the ESP32 microcontroller.

The firmware, which runs on the ESP32 controller, is responsible for reading data from all of the attached sensors, and then sending that data through the on-board radio and out to the API.