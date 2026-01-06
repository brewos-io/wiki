# Settings Overview

The Settings page provides comprehensive configuration options for your BrewOS system. This guide covers all available settings categories.

## Accessing Settings

1. **Navigate to Settings**:
   - Click "Settings" in navigation menu
   - Or go to Settings → [Category]

2. **Settings Categories**:
   - Temperature
   - Network
   - MQTT
   - Home Assistant
   - Cloud
   - Schedules
   - Power Meter
   - Scale
   - Push Notifications
   - Eco Mode
   - System
   - About

## Temperature Settings

Temperature control is the heart of espresso quality. These settings allow you to fine-tune your machine's temperature behavior for optimal extraction.

### Brew Temperature

**Setpoint:**
- **Purpose**: Target temperature for espresso extraction
- **Typical Range**: 93-95°C (200-203°F) for most coffees
- **Lower Temperatures** (90-92°C): Better for light roasts, brighter flavors, more acidity
- **Higher Temperatures** (95-97°C): Better for dark roasts, more extraction, less acidity
- **Adjustment**: Fine-tune based on your coffee and taste preferences
- **Stability**: PID maintains within ±0.1°C of setpoint

**Max Temperature:**
- **Safety Limit**: Maximum allowed temperature (prevents overheating)
- **Default**: 100°C (212°F) - boiling point of water
- **Safety**: Machine shuts down if temperature exceeds this limit
- **Protection**: Prevents damage to machine and safety hazards

**PID Tuning (Advanced):**
- **What is PID**: Proportional-Integral-Derivative control algorithm
- **Purpose**: Fine-tune how the system responds to temperature changes
- **P (Proportional)**: Responds to current error (how far from setpoint)
- **I (Integral)**: Eliminates steady-state error (long-term accuracy)
- **D (Derivative)**: Reduces overshoot (prevents temperature spikes)
- **Default Values**: Work well for most machines (don't change unless needed)
- **Expert Mode**: Only modify if you understand PID control
- **Warning**: Incorrect tuning can cause instability or poor control

### Steam Temperature

**Setpoint:**
- **Purpose**: Target temperature for steam generation
- **Typical Range**: 140-145°C (284-293°F)
- **Higher Temperature**: More steam pressure, faster frothing, more power
- **Lower Temperature**: More control, gentler steaming, less power consumption
- **Independent Control**: Separate from brew boiler (dual boiler machines)
- **Steam Quality**: Affects steam pressure and frothing capability

**Max Temperature:**
- **Safety Limit**: Maximum allowed steam temperature
- **Default**: 165°C (329°F) - safety shutdown threshold
- **Critical**: Exceeding this triggers automatic safety shutdown
- **Protection**: Prevents dangerous over-temperature conditions

### Group Head

**Thermocouple Configuration:**
- **Sensor Type**: K-type thermocouple (most common)
- **Location**: Installed in group head to measure extraction temperature
- **Purpose**: Monitor temperature at point of extraction (most critical)
- **Calibration**: May need calibration if readings seem inaccurate

**Temperature Offset:**
- **Purpose**: Calibrate group head temperature reading
- **When Needed**: If group head reading doesn't match known good thermometer
- **Adjustment**: Add/subtract offset to correct reading
- **Typical Range**: ±2°C adjustment usually sufficient
- **Calibration Process**: Compare to known good thermometer, adjust offset

### Units

**Temperature Units:**
- **Celsius**: Default, standard for espresso (recommended)
- **Fahrenheit**: Available for user preference
- **Conversion**: Automatic conversion in all displays
- **Note**: PID control always uses Celsius internally

**Pressure Units:**
- **Bar**: Default, standard for espresso (1 bar = atmospheric pressure)
- **PSI**: Pounds per square inch (alternative unit)
- **Typical Range**: 8-9 bar for espresso extraction
- **Conversion**: 1 bar ≈ 14.5 PSI

## Network Settings

Network settings configure how your machine connects to your local network and the internet. Proper network configuration is essential for web interface access, cloud features, and integrations.

### WiFi Configuration

**SSID (Network Name):**
- **Purpose**: WiFi network your machine connects to
- **Selection**: Choose from available networks (2.4GHz only)
- **Important**: ESP32 only supports 2.4GHz networks (not 5GHz)
- **Multiple Networks**: Can configure multiple networks (machine connects to strongest)
- **Hidden Networks**: Can connect to hidden networks by entering SSID manually

**Password:**
- **Security**: WPA2/WPA3 password for your WiFi network
- **Encryption**: Stored securely on ESP32
- **Multiple Networks**: Different password for each network if configured

**Static IP (Optional):**
- **Purpose**: Assign fixed IP address to machine
- **When to Use**: If you need consistent IP address (port forwarding, firewall rules)
- **Configuration**: IP address, subnet mask, gateway, DNS servers
- **Default**: DHCP (automatic IP assignment) - recommended for most users
- **Advantages**: Consistent address, easier for some network configurations
- **Disadvantages**: Must ensure IP doesn't conflict with other devices

**mDNS Name (Hostname):**
- **Purpose**: Easy-to-remember name for accessing machine
- **Default**: `brewos.local`
- **How It Works**: Multicast DNS allows you to use name instead of IP address
- **Access**: Use `http://brewos.local` instead of `http://192.168.1.x`
- **Requirements**: Your device must support mDNS (most modern devices do)
- **Customization**: Can change to custom name if desired

### Connection Status

**Current IP Address:**
- **Display**: Shows machine's current IP address on network
- **Use**: Use this IP to access web interface if mDNS doesn't work
- **DHCP**: Shows dynamically assigned IP (changes on reconnect)
- **Static**: Shows configured static IP (always the same)

**Signal Strength:**
- **Indicator**: WiFi signal quality (RSSI - Received Signal Strength Indicator)
- **Range**: -30 dBm (excellent) to -90 dBm (poor)
- **Typical**: -50 to -70 dBm is good signal
- **Factors**: Distance from router, obstacles, interference
- **Improvement**: Move machine closer to router, reduce obstacles

**Connection Status:**
- **Connected**: Machine is connected to WiFi and has IP address
- **Disconnected**: Not connected (check SSID, password, signal strength)
- **Connecting**: Attempting to connect (may take 30-60 seconds)
- **Error**: Connection failed (check settings, router, signal)

**Network Troubleshooting:**
- **Can't Connect**: Verify SSID and password, check 2.4GHz network, check signal strength
- **Weak Signal**: Move machine closer to router, check for interference
- **IP Issues**: Try DHCP first, use static IP only if needed
- **mDNS Not Working**: Use IP address directly, check device mDNS support

## MQTT Settings

### Broker Configuration

- **Enabled** - Enable/disable MQTT
- **Broker Address** - MQTT broker IP or hostname
- **Port** - MQTT port (default: 1883)
- **Username/Password** - Broker authentication
- **Topic Prefix** - Custom topic prefix

### Auto-Discovery

- **Home Assistant** - Enable HA auto-discovery
- **Discovery Prefix** - HA discovery topic prefix

See [MQTT Integration](../04-Features/MQTT-Integration.md) for details.

## Home Assistant Settings

### Integration Options

- **MQTT Auto-Discovery** - Automatic entity creation
- **Entity Configuration** - Customize entity names
- **Status Updates** - Update frequency

See [Home Assistant Integration](../04-Features/Home-Assistant.md) for details.

## Cloud Settings

### Cloud Access

- **Enabled** - Enable cloud remote access
- **Pairing Code** - Device pairing code
- **Device Name** - Name for cloud access
- **Sharing** - Share device with others

### Authentication

- **Google OAuth** - Sign in with Google
- **Account Management** - Manage cloud account

See [Cloud Access](../04-Features/Cloud-Access.md) for details.

## Schedule Settings

### Auto-On/Off Schedules

- **Add Schedule** - Create new schedule
- **Edit Schedule** - Modify existing schedule
- **Delete Schedule** - Remove schedule
- **Enable/Disable** - Toggle schedule

### Auto Power-Off

- **Enabled** - Enable auto power-off
- **Timeout** - Minutes of idle before power-off (5-480)

See [Scheduling](../04-Features/Scheduling.md) for details.

## Power Meter Settings

### PZEM-004T Configuration

- **Enabled** - Enable power metering
- **Address** - Modbus address (default: 1)
- **Calibration** - Voltage/current calibration

### Display Options

- **Show Power Card** - Display power in dashboard
- **Daily Usage** - Track daily consumption

See [Power Metering](../04-Features/Power-Metering.md) for details.

## Scale Settings

### Bluetooth Scale

- **Enabled** - Enable scale integration
- **Device Name** - Scale device name
- **Auto-Connect** - Automatically connect on boot
- **Battery Level** - Scale battery indicator

### Brew by Weight

- **Target Weight** - Default target weight
- **Tolerance** - Weight tolerance
- **Auto-Stop** - Stop at target weight

See [Brewing Features](../04-Features/Brewing-Features.md) for details.

## Push Notification Settings

### Configuration

- **Enabled** - Enable push notifications
- **Subscribe** - Subscribe to notifications
- **Notification Types** - Select which notifications to receive

### Notification Types

- **Machine Ready** - When machine reaches temperature
- **Low Water** - When water tank is low
- **Error Alerts** - When errors occur
- **Maintenance** - Cleaning reminders

See [Push Notifications](../04-Features/Push-Notifications.md) for details.

## Eco Mode Settings

### Configuration

- **Enabled** - Enable eco mode
- **Eco Temperature** - Target temperature in eco mode (50-90°C)
- **Auto-Eco After** - Minutes of idle before eco (0-480, 0=disabled)

### Behavior

- **Enter Eco** - Automatically after idle period
- **Exit Eco** - On any user activity
- **Power Savings** - Reduces power consumption significantly

See [Eco Mode](../04-Features/Eco-Mode.md) for details.

## System Settings

### Machine Configuration

- **Machine Type** - Dual boiler, single boiler, or HX
- **Machine Name** - Custom name for your machine
- **Time Zone** - System timezone

### Display Settings

- **Brightness** - Screen brightness (if display connected)
- **Theme** - Light or dark theme
- **Language** - Interface language

### Maintenance

- **Shot Counter** - Shots since last cleaning
- **Reset Counter** - Reset cleaning counter
- **Factory Reset** - Reset all settings (warning: erases all data)

## About

### System Information

- **Firmware Version** - Pico and ESP32 versions
- **App Version** - Web interface version
- **Machine Type** - Configured machine type
- **Uptime** - System uptime
- **Build Date** - Firmware build information

### Diagnostics

- **System Status** - Overall system health
- **Connection Status** - Pico and ESP32 status
- **Sensor Status** - All sensor readings
- **Error Log** - Recent errors

## Saving Settings

### Automatic Save

Most settings save automatically when changed:
- Temperature setpoints
- Network configuration
- MQTT settings
- Most other settings

### Manual Save

Some settings require explicit save:
- Network changes (may disconnect)
- System settings
- Factory reset

### Settings Persistence

- **Flash Storage** - Settings saved to flash
- **Survives Reboot** - All settings persist
- **Backup Recommended** - Document important settings

## Best Practices

### Configuration Order

1. **Basic Setup**:
   - Machine type
   - Temperature setpoints
   - Timezone

2. **Network**:
   - WiFi configuration
   - Static IP (if needed)

3. **Integrations**:
   - MQTT (if using)
   - Home Assistant (if using)
   - Cloud access (if using)

4. **Features**:
   - Schedules
   - Eco mode
   - Power meter
   - Scale

### Settings Backup

- **Document settings** - Write down important configurations
- **Take screenshots** - Visual reference
- **Export config** - If export feature available

### Troubleshooting Settings

- **Reset to defaults** - If settings cause issues
- **Check logs** - Review error messages
- **Verify connections** - Ensure hardware is connected
- **Factory reset** - Last resort (erases all data)

## Advanced Settings

### Expert Mode

Some settings are hidden by default:
- **PID Tuning** - Advanced temperature control
- **Serial Debug** - Debug output configuration
- **Hardware Configuration** - GPIO and sensor mapping

**Warning:** Advanced settings can affect system stability. Only modify if you understand the implications.

## Next Steps

- **Configure features**: See [Features](../04-Features/) section
- **Set up integrations**: [Home Assistant](../04-Features/Home-Assistant.md), [MQTT](../04-Features/MQTT-Integration.md)
- **Troubleshooting**: [Troubleshooting](../06-Troubleshooting/) if issues

---

**Related:**
- [Features](../04-Features/) - Detailed feature documentation
- [Machine Control](Machine-Control.md) - Using the machine
- [Dashboard Overview](Dashboard-Overview.md) - Interface overview

