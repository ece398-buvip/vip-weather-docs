This tutorial describes how to build the software suite for the weather station. Make sure the target system(s) have the required software as described in the previous section.

## Clone the Repository

Before building any software, you must have the most recent stable release of the weather station software suite located at our [GitHub Repository](https://github.com/ImtiazAtBradley/VIP_Weather/tree/main). All target devices must have the software needed to build the various services.

!!! info "Transferring Source to Other Computers"

    Because each target needs software (broker/api/firmware/website), it is recommended to get the repository on some development computer that will be able to "deploy" that software to those targets. For example, using a laptop to ssh into the server running the broker, or the api and website and copying the files over that connection. A great GUI tool for Windows to do this is [WinSCP](https://winscp.net/eng/index.php).

## Broker

* TODO: Complete after merge into `main` with broker changes.

## API & Website

* Firewall
* Nginx

## Firmware 

* directory
* cp2102 drivers
* pinout

Ensure that an ESP32-DevkitM1 board is attached to your computer through a USB cable before attempting to flash firmware. 

!!! warning "CP2102 Device Drivers"

    The ESP32-DevkitM1 board uses a CP2102 USB-to-UART chip to communicate between the connected USB device and the microcontroller. It is **very important** on Windows, that you have installed the [CP2102 device drivers](https://www.silabs.com/developer-tools/usb-to-uart-bridge-vcp-drivers?tab=downloads), otherwise the ESP32 cannot communicate with the attached computer. Other operating systems have not been tested.

Navigate to the `/firmware` directory in the repository, and open it in VsCode and ensure the PlatformIO extension is installed. When the project opens, make sure that PlatformIO is started, and recognizes the project, otherwise the following commands will not work.

With the project open, run the `TODO: BUILD COMMAND HERE` to build the firmware project, and then the `TODO: UPLOAD COMMAND` to upload the firmware to the attached device. The attached ESP32 should now be running the weather station firmware.

!!! info "Verify Firmware"

    To ensure that firmware is working, put the development board back in the weather station and ensure the status LED is operating.