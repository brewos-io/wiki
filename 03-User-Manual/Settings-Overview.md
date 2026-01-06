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

### Brew Temperature

- **Setpoint** - Target brew temperature (typically 93-95°C)
- **Max Temperature** - Maximum allowed temperature
- **PID Tuning** - Advanced PID parameters (expert mode)

### Steam Temperature

- **Setpoint** - Target steam temperature (typically 140-145°C)
- **Max Temperature** - Maximum allowed temperature

### Group Head

- **Thermocouple** - Group head sensor configuration
- **Offset** - Temperature offset calibration

### Units

- **Temperature** - Celsius or Fahrenheit
- **Pressure** - Bar or PSI

## Network Settings

### WiFi Configuration

- **SSID** - WiFi network name
- **Password** - WiFi password
- **Static IP** - Optional static IP configuration
- **mDNS Name** - Hostname for local access (default: `brewos.local`)

### Connection Status

- **Current IP** - Shows current IP address
- **Signal Strength** - WiFi signal quality
- **Connection Status** - Connected/disconnected indicator

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

