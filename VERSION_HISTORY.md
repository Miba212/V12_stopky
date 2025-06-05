## Version History

### v1.6.0 (2025-06-05)
- **Main web UI:** Last result now formatted as mm:ss.ss or hh:mm:ss.ss and displayed large and bold; results history is numbered and timestamped; top bar shows trigger status and battery; "Config / Trigger Details" button links to config page. Config page allows editing all per-trigger parameters.
- **Time synchronization:** Main unit now sends time sync to all triggers after each trigger reset and after main unit power-on (as part of config check-in).
- Protocol updated to include time sync field in main-to-trigger packets.
- **Trigger:** Real code for MAX7219 (8x32), VL53L0X, and ESP32 NVS config.

### v1.5.0 (2025-06-05)
- Per-trigger config via web interface, persistent settings, settings sync logic, live status/ACK display, mobile-ready web UI
- Triggers: Receive/apply config, persistent NVS, status/ACK packets, TOF sensor support, modular display
- Protocol: Settings and status structs, versioned, future-ready

### v1.2.0 (2025-06-04)
- Main: Web interface with trigger status, automatic trigger pairing, protocol struct, SSD1327 OLED, battery monitor
- Triggers: Modular SSD1306/MAX7219/headless, protocol versioning, battery monitor

### v1.1.0 (2025-06-03)
- SSD1306 OLED, battery monitor, modular code, basic ESP-NOW