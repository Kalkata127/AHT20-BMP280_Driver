# STM32 AHT20 & BMP280 Sensor Driver
A lightweight C driver for the AHT20 (Humidity/Temperature) and BMP280 (Pressure/Temperature) sensors using the STM32 HAL (I2C).
## Project Status: Work in Progress
This project is currently in the development phase. The goal is to implement a robust, non-blocking I2C driver that handles calibration, raw data conversion, and error management for both sensors on a single bus.
## Planned Architecture
The driver is designed to follow a "Request-Wait-Read" flow to ensure the STM32 isn't stalled during sensor conversion times.
1. Initialization & Calibration
2. Measurement Cycle
The driver will interact with the device registers to move through these states:<br/>
    1) Trigger: Send the Start Measurement command to the specific sensor address.
    2) Wait: Observe the "Busy" flag in the status register or implement a non-blocking delay.
    3) Read: Perform a multi-byte I2C read of the data registers.
3. Data Processing <br/> Raw data from the registers is meaningless without the manufacturer's formulas. This driver implements the fixed-point/floating-point math defined in the datasheets:\n
## References:
[AHT20 Datasheet](https://files.seeedstudio.com/wiki/Grove-AHT20_I2C_Industrial_Grade_Temperature_and_Humidity_Sensor/AHT20-datasheet-2020-4-16.pdf)<br/>
[BMP280 Datasheet (Bosch Sensortec)](https://www.bosch-sensortec.com/media/boschsensortec/downloads/datasheets/bst-bmp280-ds001.pdf)
