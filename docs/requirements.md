## Parts List

| Part | Quantity | Price | MPN |
| --- | --- | --- | --- |
| **Weather Station** | | | |
| [ESP32-Devkit-M1](https://www.digikey.com/en/products/detail/espressif-systems/ESP32-DEVKITM-1/13532113) | 1 | $8.00 | 1965-ESP32-DEVKITM-1-ND |
| [BME280](https://www.digikey.com/en/products/detail/adafruit-industries-llc/2652/5604372) | 1 | $14.95 | 1528-1359-ND |
| [LoRa RYLR890](https://www.digikey.com/en/products/detail/reyax/RYLR896/22145027) | 2 | $16.00 | 5487-RYLR896-ND |
| [Red 5mmm LED](https://www.digikey.com/en/products/detail/kingbright/WP7113ID/1747663) | 1 | $0.29 | 754-1264-ND |
| [Photoresistor](https://www.digikey.com/en/products/detail/advanced-photonix/PDV-P8103/480610) | 1 | $0.70 | PDV-P8103-ND |
| [Aviation Connectors](https://www.amazon.com/Lsgoodcare-Thread-Aviation-Connector-Assortment/dp/B0CLHYC221/) | 1 | $19.99 | B0CLHYC221 |
| [Screw Terminals](https://www.amazon.com/Tnisesm-0-2inch-Terminal-Connector-Spliced/dp/B088LVP6ML/) | 1 | $8.99 | B088LVP6ML |
| [Proto Board Kit](https://www.amazon.com/ELEGOO-Prototype-Soldering-Compatible-Arduino/dp/B072Z7Y19F/) | 1 | $9.99 | B072Z7Y19F |
| [Water Level Sensor](https://www.digikey.com/en/products/detail/adafruit-industries-llc/4965/14302510) | 1 | $1.95 | 1528-4965-ND |
| [WQ-44 Enclosure](https://www.polycase.com/wq-44#WQ-44-03) | 1 | $28.30| WQ-44-03 |
| [PK-064A Pole Mount Kit](https://www.polycase.com/pk-064a) | 1 | $29.74| PK-064A |
| [UA-020 Hooked Vent](https://www.polycase.com/hooked-air-vent) | 1 | $5.37| UA-020 |
| [WP-44P-01 Panel For Enclosure](https://www.polycase.com/wq-44p#WQ-44P-01) | 1 | $3.12 | WQ-44P-01 |
| **Broker** | | | |
| [Raspberry Pi3b+](https://www.amazon.com/ELEMENT-Element14-Raspberry-Pi-Motherboard/dp/B07P4LSDYV/) | 1 | $48.91 | B07P4LSDYV |
| **Misc Parts** | | | |
| [Metric Hardware](https://www.amazon.com/Assortment-M2-M3-M4-M5/dp/B0BYZ1KK1V/) | 1 | $21.97 | BOBYZ1KK1V |
| | **TOTAL**: | $212.21 | |

## 3D Printed Parts

The ECE 398 Weather Station also has a few printed parts to go along with the off the shelf mechanical design. Below are the links to the OnShape documents of these parts.

| Part | Quantity |
| --- | -- |
| [Rain Sensor Mount](https://cad.onshape.com/documents/8db079748d105956ded01c1c/w/7652b640011f3c2622e7696a/e/40aadab448f56b4d99f2158a) | 1 |
| [Shroud](https://cad.onshape.com/documents/38c15368c41f2224b0adceca/w/e0d05cb6b75a73d47582f798/e/fc5c8805be871225fbb33687) | 2 |

## Required Software

The following software is required for the development/production of the weather station. Software under **Development** is just for development, while the software under the other sections is *required* for running the software suites.

### Development

* [VirtualBox](https://www.virtualbox.org/) - Virtual machine software
* [git](https://git-scm.com/) - Version control
* [GitHub](https://github.com/) - Hosting platform for git-based projects
* [OnShape](https://www.onshape.com/en/) - Online CAD platform
* [KiCad](https://www.kicad.org/) - EDA software used to design PCBs

!!! warning "Minimum Requirements"

    Both the Broker and the API / Website were tested on hosts using the Ubuntu Server 24.04 distribution.

### API & Website

The API is required to be ran on the same server as the redis database. It is recommended as well, to host the website on this same server. The current implementation of weather station uses a server through [Linode](https://www.linode.com/). Specifically, the Nanode plan.

The API requirements are:

| Param | Recommended |
| --- | --- |
| OS | Ubuntu 24.04 Server (Or other Debian-based systems) |
| Memory | 2GB |
| CPU | Anything, really |

!!! warning "Production Deployment"

    It is **STRONGLY** recommended to use both a firewall and http server to deploy the API and website. We recommend the [ufw firewall](https://wiki.ubuntu.com/UncomplicatedFirewall) and [nginx web server](https://nginx.org/en/).

!!! info "CPU Requirements"

    Almost any CPU will do for running the Website. Absolute minimum requirements have not been measured

### Broker

The broker has to be on-site, within range of the weather station's LoRa radio. It is recommended to run this on a Raspberry Pi 3B+, because that is what was tested and deployed in the initial design. The broker must be passed the device file which the RYLR896 radio UART is attached to.

| Param | Recommended |
| --- | --- |
| OS | Ubuntu 24.04 Server (Tested) |
| Memory | 1GB |

!!! info "CPU Requirements"

    Almost any CPU will do for running the Broker. Absolute minimum requirements have not been measured

### Firmware

To flash the firmware, it is recommended to build the firmware from source using the [PlatformIO](https://platformio.org/) extension with VsCode and flash.

There is also a good chance the [CP2102 USB-to-UART chip drivers](https://www.silabs.com/developer-tools/usb-to-uart-bridge-vcp-drivers?tab=downloads) will be needed to recognize the ESP32 and program it.