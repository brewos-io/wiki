# Firmware Flashing

This guide covers flashing firmware to both the Pico RP2350 and ESP32-S3 microcontrollers.

## Overview

BrewOS consists of two separate firmware images:

1. **Pico Firmware** - Real-time machine control (PID, safety, sensors)
2. **ESP32 Firmware** - Connectivity and web interface

Both must be flashed for the system to function.

## Prerequisites

- ✅ Hardware installation complete
- ✅ USB cable for flashing
- ✅ Computer with web browser
- ✅ Firmware files (`.uf2` for Pico, built firmware for ESP32)

## Flashing Pico Firmware

### Method 1: USB (Recommended for First Time)

1. **Disconnect power** - Ensure Pico is not powered via control board
2. **Hold BOOTSEL button** - Press and hold the BOOTSEL button on the Pico
3. **Connect USB cable** - While holding BOOTSEL, connect USB cable to Pico
4. **Release BOOTSEL** - Pico should appear as "RPI-RP2" drive
5. **Copy firmware** - Copy the appropriate `.uf2` file to the drive:
   - `brewos_dual_boiler.uf2` - For dual boiler machines
   - `brewos_single_boiler.uf2` - For single boiler machines
   - `brewos_heat_exchanger.uf2` - For HX machines
6. **Wait for reboot** - Pico will automatically reboot when flashing completes

### Method 2: OTA via ESP32 (After Initial Setup)

Once ESP32 is configured and connected:

1. **Connect to ESP32** - Access web interface at `http://brewos.local` or ESP32 IP
2. **Navigate to Firmware Update** - Go to Settings → Firmware Update
3. **Select firmware file** - Choose the appropriate `.uf2` file
4. **Upload** - Click "Upload" and wait for upload to complete
5. **Flash to Pico** - Click "Flash Pico" button
6. **Verify** - Check that Pico status shows "Connected"

**Note:** OTA flashing requires UART connection between ESP32 and Pico.

### Verifying Pico Firmware

After flashing:

1. **Check serial output** (optional):
   ```bash
   # macOS/Linux
   screen /dev/tty.usbmodem* 115200
   
   # Windows
   # Use PuTTY or similar, connect to COM port at 115200 baud
   ```

2. **Look for boot messages**:
   - "BrewOS Pico Firmware"
   - "Machine type: DUAL_BOILER" (or your machine type)
   - "Pico ready"

## Flashing ESP32 Firmware

### Using PlatformIO (Recommended)

1. **Install PlatformIO**:
   - Install [Visual Studio Code](https://code.visualstudio.com/)
   - Install [PlatformIO extension](https://platformio.org/install/ide?install=vscode)

2. **Open project**:
   ```bash
   cd firmware/src/esp32
   # Open in VS Code with PlatformIO extension
   ```

3. **Build firmware**:
   ```bash
   pio run
   ```

4. **Upload firmware**:
   ```bash
   pio run -t upload      # Upload firmware
   pio run -t uploadfs    # Upload web UI files
   ```

5. **Or use flash script**:
   ```bash
   cd firmware/src/scripts
   ./flash_esp32.sh
   ```

### Using Arduino IDE

1. **Install Arduino IDE 2.x**
2. **Add ESP32 board support** via Board Manager
3. **Install required libraries** (see `platformio.ini` for list)
4. **Open firmware** in Arduino IDE
5. **Select board**: ESP32-S3 Dev Module
6. **Upload** firmware

### Verifying ESP32 Firmware

After flashing:

1. **Check serial output**:
   ```bash
   pio device monitor
   # or
   screen /dev/tty.usbserial-* 115200
   ```

2. **Look for boot messages**:
   - "BrewOS ESP32 Firmware"
   - "WiFi AP: BrewOS-Setup"
   - "Web server started"

3. **Connect to access point**:
   - SSID: `BrewOS-Setup`
   - Password: `brewoscoffee`
   - Navigate to `http://192.168.4.1`

## Building Firmware from Source

### Pico Firmware

1. **Install prerequisites**:
   - Pico SDK (v1.5.0+)
   - ARM GCC toolchain
   - CMake 3.13+

2. **Build**:
   ```bash
   cd firmware/src/pico
   mkdir build && cd build
   
   # For your machine type:
   cmake -DMACHINE_TYPE=DUAL_BOILER ..      # Dual boiler
   cmake -DMACHINE_TYPE=SINGLE_BOILER ..    # Single boiler
   cmake -DMACHINE_TYPE=HEAT_EXCHANGER ..   # HX
   
   # Or build all:
   cmake -DBUILD_ALL_MACHINES=ON ..
   
   make -j4
   ```

3. **Output**: `brewos_*.uf2` files in `build/` directory

### ESP32 Firmware

1. **Install PlatformIO** (see above)

2. **Build**:
   ```bash
   cd firmware/src/esp32
   pio run
   ```

3. **Output**: Firmware binary in `.pio/build/` directory

## Firmware Versions

### Checking Installed Version

**Pico:**
- Check serial output on boot
- Or via web interface: Settings → About

**ESP32:**
- Web interface: Settings → About
- Or serial output on boot

### Updating Firmware

See [OTA Updates](../04-Features/OTA-Updates.md) for updating firmware wirelessly after initial setup.

## Troubleshooting

### Pico Not Recognized

- **Check USB cable** - Must support data, not just charging
- **Try different USB port** - Some ports may not provide enough power
- **Hold BOOTSEL longer** - Some Picos need longer hold time
- **Check drivers** - macOS/Linux usually work automatically, Windows may need drivers

### ESP32 Won't Upload

- **Check USB cable** - Must support data
- **Try holding BOOT button** during upload
- **Check COM port** - Verify correct port in PlatformIO/Arduino IDE
- **Check drivers** - Install CP210x or CH340 drivers if needed

### Firmware Upload Fails

- **Check connections** - Verify USB cable is connected
- **Try different cable** - Some cables are charge-only
- **Restart device** - Unplug and replug USB
- **Check permissions** - Linux may need udev rules for USB access

### Pico Not Booting After Flash

- **Check firmware file** - Ensure correct machine type
- **Try reflashing** - Sometimes first flash doesn't take
- **Check serial output** - Look for error messages
- **Verify hardware** - Ensure control board is properly powered

### ESP32 Web Interface Not Loading

- **Check web files uploaded** - Run `pio run -t uploadfs`
- **Clear browser cache** - Old cached files may cause issues
- **Try different browser** - Some browsers cache aggressively
- **Check LittleFS** - Verify filesystem is mounted correctly

## Next Steps

After successfully flashing both firmwares:

1. **Power on system** - Connect power to control board
2. **Verify communication** - Check that Pico and ESP32 are communicating
3. **Proceed to**: [Initial Setup](Initial-Setup.md)

---

**Next:** [Initial Setup](Initial-Setup.md)

