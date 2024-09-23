# Smart-Laptop-Cooler
This repository contains the firmware for a smart laptop cooling system that dynamically controls the speed of multiple fans based on temperature readings from connected sensors. The system is built using an ESP32 microcontroller and includes various features such as adjustable fan speed curves, manual fan speed control, and an OLED display for fan status visualization.

Features
Custom I2C Driver: Includes a custom software I2C driver written in C, which enables communication with an ADS1115 ADC module and an OLED display. Achieves reliable clock speeds up to 1MHz for fast, responsive communication.
PWM Fan Control: Utilizes the ESP32's LEDC PWM controller to adjust fan speeds based on either temperature curves or manually set power levels.
EEPROM Emulation: Fan speed and temperature curve settings are stored in non-volatile memory (EEPROM) using the ESP32's NVS (Non-Volatile Storage) to ensure that settings persist after a power cycle.
State Machine Menu System: A simple menu interface controlled by buttons and a potentiometer allows for easy configuration of fan modes and settings, viewable on the OLED display.
Temperature Sensor Integration: Temperature data is read from up to 4 sensors using the ADS1115 ADC. Fan speeds are adjusted dynamically based on user-configured curves or manual control.
Command Interface: Serial commands allow the user to set fan curves, fan speeds, and toggle between fan control modes (curve vs speed).
Hardware Requirements
ESP32: Used as the core microcontroller to control the fans, read temperature data, and manage the OLED display.
Fans: 4 fans controlled via PWM, with real-time feedback and adjustment.
Temperature Sensors: Connected to the ADS1115 ADC module to monitor the cooling system's environment.
ADS1115 ADC: Reads analog values from temperature sensors.
OLED Display: Provides a graphical interface to display fan settings and statuses.
Buttons & Potentiometer: Used to navigate the menu system and adjust fan configurations.
External Pull-up Resistors: 10k pull-up resistors for the I2C communication lines (SDA and SCL).
Software Features
Fan Control Modes
Curve Mode: Automatically adjusts the fan speed based on a temperature-to-speed curve. The user can configure and save the fan curve in EEPROM.
Speed Mode: The user can manually set the speed percentage of each fan, and the speed setting is stored in EEPROM for persistence.
OLED Display
The OLED display shows information such as fan temperatures, fan speeds, and menu options. The user can navigate through the menu to configure each fan's settings.

Menu System
The firmware includes a state machine to handle various menu screens:

Main Menu: Allows the user to navigate between "Fan Info" and "Fan Configuration".
Fan Info: Displays the temperature and fan speed for each fan.
Fan Configuration: Allows the user to configure individual fans' settings, including fan curve and power level.
Change Fan Curve: Allows the user to adjust the temperature-to-speed curve for each fan.
Commands
Commands can be sent over UART to control the fans programmatically:

SET_FAN_SPEED: Set the speed of a specific fan.
SET_FAN_MODE: Switch between fan control modes (curve or manual speed).
SET_CURVE: Set the temperature-to-speed curve for a specific fan.


