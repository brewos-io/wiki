# Quick Start Guide

This guide provides a fast-track setup for experienced users who are familiar with electronics and firmware flashing. For detailed instructions, see the [Installation & Setup](../02-Installation-Setup/) section.

## Prerequisites

- ✅ BrewOS control board installed
- ✅ ESP32-S3 module connected
- ✅ All sensors wired and tested
- ✅ USB cable for firmware flashing
- ✅ Computer with web browser

## Step 1: Flash Firmware

### Pico Firmware

1. **Build or download firmware** for your machine type:

   - `brewos_dual_boiler.uf2` - For dual boiler machines
   - `brewos_single_boiler.uf2` - For single boiler machines
   - `brewos_heat_exchanger.uf2` - For HX machines

2. **Flash via USB**:
   - Hold BOOTSEL button on Pico
   - Connect USB cable
   - Release BOOTSEL
   - Copy `.uf2` file to RPI-RP2 drive

### ESP32 Firmware

1. **Build firmware** using PlatformIO:

   ```bash
   cd firmware/src/esp32
   pio run
   ```

2. **Upload firmware and web files**:

   ```bash
   pio run -t upload      # Firmware
   pio run -t uploadfs    # Web UI
   ```

   Or use the flash script:

   ```bash
   cd firmware/src/scripts
   ./flash_esp32.sh
   ```

## Step 2: Initial WiFi Setup

1. **Connect to ESP32 access point**:

   - SSID: `BrewOS-Setup`
   - Password: `brewoscoffee`

2. **Open web interface**:

   - Navigate to `http://192.168.4.1`

3. **Configure WiFi**:
   - Go to Settings → Network
   - Enter your WiFi credentials
   - Save and wait for connection

## Step 3: Configure Machine

1. **Access web interface**:

   - Find ESP32 IP address on your network
   - Or use `http://brewos.local` (if mDNS is enabled)

2. **Complete first-run wizard**:

   - Set machine type (dual boiler, single boiler, HX)
   - Configure temperature setpoints
   - Set timezone

3. **Verify communication**:
   - Check that Pico status shows "Connected"
   - Verify sensor readings are displayed
   - Test basic machine functions

## Step 4: Test Basic Functions

1. **Turn on machine**:

   - Use power button or web interface
   - Wait for boilers to reach temperature

2. **Verify temperature control**:

   - Check brew and steam temperatures
   - Verify PID is maintaining setpoints

3. **Test brewing**:
   - Pull a test shot
   - Verify shot timer works
   - Check pressure readings

## Common Issues

### Pico Not Connecting

- Check UART wiring (TX↔RX, RX↔TX, GND↔GND)
- Verify baud rate (921600)
- Check serial console for errors

### WiFi Not Connecting

- Verify credentials are correct
- Check 2.4GHz network (ESP32 doesn't support 5GHz)
- Try resetting ESP32 and reconfiguring

### No Sensor Readings

- Verify sensor wiring
- Check sensor types match configuration
- Review diagnostic logs

## Next Steps

- **Configure features**: See [Features](../04-Features/) section
- **Set up integrations**: [Home Assistant](../04-Features/Home-Assistant.md), [MQTT](../04-Features/MQTT-Integration.md)
- **Enable cloud access**: [Cloud Access](../04-Features/Cloud-Access.md)
- **Read user manual**: [User Manual](../03-User-Manual/)

## Detailed Guides

For step-by-step instructions with troubleshooting:

- [Hardware Installation](../02-Installation-Setup/Hardware-Installation.md)
- [Firmware Flashing](../02-Installation-Setup/Firmware-Flashing.md)
- [Initial Setup](../02-Installation-Setup/Initial-Setup.md)

---

**Next:** [Installation & Setup](../02-Installation-Setup/) for detailed instructions
