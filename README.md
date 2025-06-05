# ESP32 Wireless Stopwatch System

**Version:** 1.6.0  
**Author:** Miba212

## Overview

A flexible, wireless multi-trigger stopwatch system using ESP32 microcontrollers and ESP-NOW, with a live web interface for configuration and result display.

## Features

- **Main Unit**
  - Receives status from multiple trigger units (Start, Stop, Lap, etc.)
  - Displays live results and results history on a mobile-optimized web interface
  - Per-trigger status (live/online, battery, etc.) always visible
  - Prominent last result, formatted as mm:ss.ss or hh:mm:ss.ss if needed
  - Results history with line numbers and timestamps
  - Advanced config/details page for per-trigger editing and info
  - Sends time sync and config to triggers after power-up or upon trigger reset

- **Trigger Unit**
  - Responds to config/time sync from main unit
  - Sends status (battery, distance, ACK, etc.)
  - MAX7219 8x32 matrix display for showing result/distance
  - VL53L0X TOF sensor for distance measurement
  - Persistent config in ESP32 NVS

## Protocol

- ESP-NOW with compact binary packets
- Main→Trigger: Settings struct (with time sync)
- Trigger→Main: Status/ACK struct
- Time synchronization is performed after any trigger reset and after main unit power-on

## Web Interface

- Main page:  
  - Compact bar with live/online/battery status for all triggers (each links to config)
  - Large, bold last result (hh:mm:ss.ss if >1h)
  - Results history with timestamps and line numbers
  - "Config / Trigger Details" button links to advanced per-trigger config/details page
- Config page:  
  - Allows editing all trigger parameters and viewing detailed status

## Building

- PlatformIO multi-env setup (see `platformio.ini`)
- Main unit and trigger firmware are separate but managed in one project

## Hardware

- **MAX7219 8x32 matrix**:  
  - DIN (Data) = GPIO23  
  - CLK = GPIO18  
  - CS  = GPIO5  
- **VL53L0X TOF sensor**:  
  - SDA = GPIO21  
  - SCL = GPIO22  
- **Battery ADC**:  
  - Use a voltage divider to pin 34 (ADC1_CH6), adjust formula as needed.

---
