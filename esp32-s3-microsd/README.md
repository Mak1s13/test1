# ESP32-S3 microSD Card SPI Interface

A complete KiCad schematic design for interfacing an ESP32-S3-WROOM-2 microcontroller with a microSD card in SPI mode.

## Overview

This project provides a production-ready schematic for reliable microSD card communication with the ESP32-S3 using the SPI protocol. It includes all necessary decoupling capacitors, pull-up resistors, and proper signal routing.

## Hardware Components

- **MCU**: ESP32-S3-WROOM-2
- **Storage**: Micro SD Card Socket (SPI mode)
- **Capacitors**: 
  - C1: 100nF (decoupling, close to socket)
  - C2: 10µF (bulk decoupling, close to socket)
- **Resistors**: 
  - R1, R2, R3: 47kΩ (pull-ups on SPI lines)

## Pin Assignment (ESP32-S3 VSPI)

| Signal | ESP32 GPIO | microSD Pin | Function |
|--------|-----------|-------------|----------|
| CLK    | GPIO18    | 5           | Clock    |
| MOSI   | GPIO23    | 3 (CMD)     | Command  |
| MISO   | GPIO19    | 7 (DAT0)    | Data In  |
| CS     | GPIO5     | 2 (DAT3)    | Chip Select |
| VDD    | +3.3V     | 4           | Power    |
| VSS    | GND       | 6           | Ground   |
| NC     | -         | 1, 8        | Not Connected |
| Shield | -         | SH          | Ground   |

## Schematic Features

✅ **Power Distribution**: Clean 3.3V supply with dual-stage decoupling  
✅ **Pull-up Resistors**: 47kΩ on CS, MOSI, MISO for stable operation  
✅ **Proper Net Naming**: Clear signal labels (SD_CLK, SD_MOSI, SD_MISO, SD_CS)  
✅ **Ground Plane Ready**: Shield connected to ground  
✅ **Production Ready**: Suitable for PCB layout and manufacturing  

## Design Notes

- All pull-up resistors should be placed close to the MCU for best signal integrity
- Decoupling capacitors (especially the 100nF) must be placed as close as possible to the microSD socket
- For long interconnects (>5cm), consider adding 22-47Ω series resistors on SPI lines
- The card-detect (CD) function on pin 2 is not used in SPI mode; DAT3 serves as CS instead

## Files Included

- `esp32-s3-microsd.kicad_sch` - Main schematic file
- `esp32-s3-microsd.kicad_pcb` - PCB layout file (ready for design)
- `esp32-s3-microsd.kicad_pro` - KiCad project configuration

## Getting Started

1. Install KiCad (version 6.0 or later recommended)
2. Open `esp32-s3-microsd.kicad_pro`
3. View the schematic in the Schematic Editor
4. Design your PCB layout in the PCB Editor

## License

Open source - feel free to use and modify for your projects.