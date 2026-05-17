# Logic Design Project

> HCMUT — Semester 241 · Smart-home IoT prototype on YoloUno (ESP32-S3) with FreeRTOS, MQTT and a mini web server.

## Project scope

1. **YoloUno with Arduino IDE** — FreeRTOS tasks, MQTT publishing, mini web server.
2. **PlatformIO on VS Code** — same firmware ported to PlatformIO with proper project layout.
3. **Exploring new hardware** — new I/O devices (RFID, AC sensor, OLED, ultrasonic, 7-segment) and new MCUs on PlatformIO.
4. **Final report** — challenges, wiring diagrams, performance notes (see [`docs/reports/`](../docs/reports/)).

## Hardware

| Component | Interface | Purpose |
|---|---|---|
| YoloUno board (ESP32-S3, 8 MB flash) | — | Main MCU |
| DHT20 | I²C | Temperature & humidity |
| LiquidCrystal I²C (16×2) | I²C | Local display |
| Adafruit NeoPixel ×4 | GPIO D5 | Status LEDs |
| Soil moisture sensor | Analog A0 | Plant monitoring |
| Light sensor | Analog A1 | Ambient light |
| Relay module | GPIO D3 | Pump / actuator |
| HC-SR04, TM1637 (Task 3) | GPIO | Distance + 7-seg display |

Default I²C pins: `SDA = 11`, `SCL = 12`. Wi-Fi credentials and the Adafruit IO key are read from `#define`s at the top of each entry file — replace before flashing.

## Build & flash

### Task 1 — Arduino IDE

1. Install the Arduino IDE and add the YoloUno board package via Boards Manager.
2. Install libraries: `Adafruit NeoPixel`, `DHT20`, `LiquidCrystal_I2C`, `Adafruit MQTT Library`.
3. Open `Task1_Arduino/main.ino`, set `WLAN_SSID`, `WLAN_PASS`, `AIO_KEY`, then upload.

### Task 2 & Task 3 — PlatformIO

```bash
cd Task2_PlatformIO    # or Task3_NewHardware
pio run -t upload      # build + flash
pio device monitor     # serial logs
```

VS Code with the PlatformIO extension works the same way through the GUI. The upload port is pinned to `COM8` in `Task2_PlatformIO/platformio.ini`; change it to match your machine.

## Reports

Final reports are kept outside the repo in [`../docs/reports/`](../docs/reports/) on the team drive. Move them into the repo if you want them versioned alongside the code.
