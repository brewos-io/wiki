# Initial Setup

This guide covers the first-time configuration of your BrewOS system after hardware installation and firmware flashing.

## Prerequisites

- ✅ Hardware installation complete
- ✅ Firmware flashed to both Pico and ESP32
- ✅ System powered on
- ✅ Computer or smartphone with WiFi

## Step 1: Connect to ESP32 Access Point

On first boot, the ESP32 creates a WiFi access point for initial configuration:

1. **Find the access point**:
   - SSID: `BrewOS-Setup`
   - Password: `brewoscoffee`
   - Password is also displayed on ESP32 screen (if display is connected)

2. **Connect your device**:
   - Open WiFi settings on your computer or smartphone
   - Connect to `BrewOS-Setup` network
   - Enter password: `brewoscoffee`

3. **Open web interface**:
   - Navigate to `http://192.168.4.1` in your web browser
   - You should see the BrewOS web interface

## Step 2: Complete First-Run Wizard

The first-run wizard will guide you through initial configuration:

### Machine Type Selection

Select your machine type:
- **Dual Boiler** - Separate brew and steam boilers
- **Single Boiler** - One boiler for both brewing and steaming
- **Heat Exchanger** - Steam boiler with HX for brew water

### Temperature Configuration

Set initial temperature setpoints:
- **Brew Temperature**: Typically 93-95°C (200-203°F)
- **Steam Temperature**: Typically 140-145°C (284-293°F)

**Note:** You can adjust these later in Settings.

### Timezone Configuration

Set your timezone:
- Select your timezone from the list
- This is important for scheduling features

### Network Configuration (WiFi)

Configure WiFi connection:

1. **Select your network** from the list of available networks
2. **Enter WiFi password**
3. **Optional**: Set static IP address (if needed)
4. **Save configuration**

The ESP32 will:
- Disconnect from access point mode
- Connect to your WiFi network
- Display new IP address on screen (if display connected)

### Verify Connection

After WiFi configuration:

1. **Note the IP address** displayed on screen or in web interface
2. **Reconnect to your WiFi** on your device
3. **Access web interface** at the new IP address
   - Or use `http://brewos.local` (if mDNS is enabled)

## Step 3: Verify System Status

Check that everything is working:

### Pico Communication

1. **Check Pico status**:
   - Should show "Connected" in web interface
   - If "Disconnected", check UART wiring

2. **Verify sensor readings**:
   - Temperature readings should be displayed
   - Pressure reading should be visible
   - Water level status should show

### Machine Functions

1. **Test power control**:
   - Turn machine on/off via web interface
   - Verify heaters activate (for dual boiler/HX)

2. **Check temperature control**:
   - Monitor temperature graphs
   - Verify PID is maintaining setpoints

3. **Test basic functions**:
   - Verify pump control works
   - Check solenoid activation
   - Test indicator lamp

## Step 4: Configure Additional Settings

### Temperature Settings

1. **Navigate to**: Settings → Temperature
2. **Adjust setpoints** as needed:
   - Brew temperature
   - Steam temperature
   - PID tuning (advanced)

### Network Settings

1. **Navigate to**: Settings → Network
2. **Configure**:
   - WiFi credentials (if changed)
   - Static IP (optional)
   - mDNS name (default: `brewos.local`)

### System Settings

1. **Navigate to**: Settings → System
2. **Configure**:
   - Machine name
   - Time settings
   - Display settings

## Step 5: Install as PWA (Optional)

The web interface can be installed as a Progressive Web App:

1. **Open web interface** in browser
2. **Look for install prompt** (browser-dependent)
3. **Or use browser menu**:
   - Chrome/Edge: Menu → "Install BrewOS"
   - Safari: Share → "Add to Home Screen"
   - Firefox: Menu → "Install"

4. **Launch from home screen** - App will work offline

## Troubleshooting

### Cannot Connect to Access Point

- **Check ESP32 power** - Ensure ESP32 is powered
- **Check WiFi** - Verify access point is broadcasting
- **Try different device** - Some devices have issues with AP mode
- **Reset ESP32** - Hold reset button, then reconfigure

### WiFi Connection Fails

- **Check credentials** - Verify WiFi password is correct
- **Check 2.4GHz** - ESP32 only supports 2.4GHz (not 5GHz)
- **Check signal strength** - Move closer to router
- **Try manual IP** - Set static IP if DHCP fails

### Pico Shows Disconnected

- **Check UART wiring** - Verify TX↔RX, RX↔TX, GND↔GND
- **Check baud rate** - Should be 921600
- **Check power** - Ensure Pico is powered
- **Review serial logs** - Check for error messages

### No Sensor Readings

- **Check sensor wiring** - Verify all connections
- **Check sensor types** - Ensure correct sensor types configured
- **Review diagnostics** - Check diagnostic logs for errors
- **Verify machine type** - Ensure correct machine type selected

### Web Interface Not Loading

- **Clear browser cache** - Old cached files may cause issues
- **Try different browser** - Some browsers have compatibility issues
- **Check IP address** - Verify you're using correct IP
- **Try incognito mode** - Rule out browser extensions

## Next Steps

After completing initial setup:

1. **Explore features**: See [Features](../04-Features/) section
2. **Configure integrations**: [Home Assistant](../04-Features/Home-Assistant.md), [MQTT](../04-Features/MQTT-Integration.md)
3. **Set up cloud access**: [Cloud Access](../04-Features/Cloud-Access.md) (optional)
4. **Read user manual**: [User Manual](../03-User-Manual/)

## Additional Resources

- [User Manual](../03-User-Manual/) - Complete guide to using BrewOS
- [Features](../04-Features/) - Detailed feature documentation
- [Troubleshooting](../06-Troubleshooting/) - Common issues and solutions

---

**Next:** [User Manual](../03-User-Manual/) or [Features](../04-Features/)

