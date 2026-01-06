# Troubleshooting Installation

Common issues encountered during BrewOS installation and how to resolve them.

## Hardware Issues

### Control Board Not Powering On

**Symptoms:**
- No LED indicators
- No response from system

**Solutions:**
1. **Check power input**:
   - Verify mains power is connected
   - Check fuse is installed and not blown
   - Verify L, N, PE connections

2. **Check power supply**:
   - Verify 5V and 3.3V outputs
   - Check for shorts on power rails
   - Verify isolation between HV and LV

3. **Check connections**:
   - Verify all connections are secure
   - Check for loose wires
   - Verify ground connections

### Sensors Not Reading

**Symptoms:**
- Temperature readings show 0°C or invalid values
- Pressure reading is 0
- Water level not detected

**Solutions:**
1. **Check sensor wiring**:
   - Verify sensor connections to control board
   - Check for loose connections
   - Verify correct terminals

2. **Check sensor types**:
   - Ensure NTC thermistors match configuration (100K vs 50K)
   - Verify thermocouple type (K-type)
   - Check pressure transducer range (0-16 bar)

3. **Check sensor installation**:
   - Verify sensors are properly installed
   - Check thermal paste on temperature sensors
   - Verify pressure transducer is connected to brew path

### Relays Not Activating

**Symptoms:**
- Pump doesn't start
- Solenoid doesn't activate
- Indicator lamp doesn't turn on

**Solutions:**
1. **Check relay outputs**:
   - Verify connections to relay outputs
   - Check relay coil connections
   - Verify common connections

2. **Check load connections**:
   - Verify pump/solenoid/lamp are connected
   - Check for shorts in load wiring
   - Verify load ratings match relay capacity

3. **Test relays**:
   - Use multimeter to check relay continuity
   - Verify relay activation via web interface
   - Check for damaged relays

### Heaters Not Heating

**Symptoms:**
- Boilers not heating
- Temperature not rising

**Solutions:**
1. **Check SSR connections**:
   - Verify SSR trigger connections
   - Check SSR power connections (mains)
   - Verify SSR is receiving trigger signal

2. **Check heater connections**:
   - Verify heaters are connected to SSR outputs
   - Check for loose connections
   - Verify heater power ratings

3. **Test SSRs**:
   - Check SSR trigger signal with multimeter
   - Verify SSR is switching (check output voltage)
   - Check for damaged SSRs

## Firmware Issues

### Pico Not Booting

**Symptoms:**
- No serial output
- No response from Pico

**Solutions:**
1. **Check firmware**:
   - Verify correct firmware file for machine type
   - Try reflashing firmware
   - Check firmware file is not corrupted

2. **Check power**:
   - Verify Pico is receiving power
   - Check 3.3V power supply
   - Verify power sequencing

3. **Check connections**:
   - Verify USB connection (if using USB)
   - Check power connections
   - Verify no shorts on power rails

### ESP32 Not Booting

**Symptoms:**
- No WiFi access point
- No web interface
- No serial output

**Solutions:**
1. **Check firmware**:
   - Verify firmware was uploaded correctly
   - Check web files were uploaded (`uploadfs`)
   - Try reflashing firmware

2. **Check power**:
   - Verify ESP32 is receiving 5V power
   - Check power consumption (may need more current)
   - Verify power supply capacity

3. **Check connections**:
   - Verify J15 connector is properly connected
   - Check for loose connections
   - Verify UART wiring

### Firmware Upload Fails

**Symptoms:**
- Upload process fails
- Device not recognized
- Upload timeout

**Solutions:**
1. **Check USB connection**:
   - Try different USB cable
   - Check USB port (try different port)
   - Verify cable supports data (not charge-only)

2. **Check drivers**:
   - Install CP210x or CH340 drivers (Windows)
   - Check USB permissions (Linux)
   - Verify device is recognized in system

3. **Try different method**:
   - Use PlatformIO instead of Arduino IDE
   - Try OTA update (if ESP32 is already configured)
   - Use different computer

## Communication Issues

### Pico and ESP32 Not Communicating

**Symptoms:**
- Pico status shows "Disconnected"
- No sensor data in web interface
- Communication errors in logs

**Solutions:**
1. **Check UART wiring**:
   - Verify TX↔RX crossover (ESP32 TX → Pico RX, ESP32 RX ← Pico TX)
   - Check GND connection (common ground required)
   - Verify connections are secure

2. **Check baud rate**:
   - Verify baud rate is 921600
   - Check firmware configuration matches
   - Try lower baud rate for testing

3. **Check power sequencing**:
   - Ensure control board powers on before ESP32
   - Verify power sequencing is correct
   - Check for power-related issues

### WiFi Connection Issues

**Symptoms:**
- Cannot connect to access point
- WiFi connection drops
- Cannot access web interface

**Solutions:**
1. **Check access point**:
   - Verify SSID is `BrewOS-Setup`
   - Check password is `brewoscoffee`
   - Try different device to connect

2. **Check WiFi configuration**:
   - Verify WiFi credentials are correct
   - Check 2.4GHz network (ESP32 doesn't support 5GHz)
   - Check signal strength

3. **Check network settings**:
   - Verify IP address configuration
   - Check for IP conflicts
   - Try static IP address

## Configuration Issues

### First-Run Wizard Not Appearing

**Symptoms:**
- Web interface loads but no wizard
- Cannot complete initial setup

**Solutions:**
1. **Clear browser cache**:
   - Clear browser cache and cookies
   - Try incognito/private mode
   - Try different browser

2. **Check LittleFS**:
   - Verify filesystem is mounted
   - Check for file system errors
   - Try reflashing web files

3. **Manual configuration**:
   - Access settings directly
   - Configure WiFi manually
   - Set machine type in settings

### Settings Not Saving

**Symptoms:**
- Changes don't persist after reboot
- Settings reset to defaults

**Solutions:**
1. **Check filesystem**:
   - Verify LittleFS is working
   - Check for filesystem errors
   - Verify free space

2. **Check write permissions**:
   - Verify filesystem is writable
   - Check for file system corruption
   - Try reformatting filesystem

3. **Check configuration**:
   - Verify settings are being saved
   - Check configuration files
   - Review serial logs for errors

## Getting Additional Help

If you've tried the solutions above and still have issues:

1. **Check logs**:
   - Review serial output for errors
   - Check web interface diagnostics
   - Review error messages

2. **Document the issue**:
   - Note exact symptoms
   - Document what you've tried
   - Take photos if helpful

3. **Get help**:
   - See [Getting Help](../06-Troubleshooting/Getting-Help.md)
   - Check [Common Issues](../06-Troubleshooting/Common-Issues.md)
   - Review [Error Codes](../06-Troubleshooting/Error-Codes.md)

## Prevention Tips

To avoid installation issues:

1. **Follow instructions carefully** - Don't skip steps
2. **Verify connections** - Double-check all wiring
3. **Test incrementally** - Test each component as you install
4. **Document wiring** - Take photos before disconnecting factory board
5. **Use proper tools** - Quality tools make a difference
6. **Work safely** - Always disconnect power before making changes

---

**Related:**
- [Common Issues](../06-Troubleshooting/Common-Issues.md)
- [Error Codes](../06-Troubleshooting/Error-Codes.md)
- [Getting Help](../06-Troubleshooting/Getting-Help.md)

