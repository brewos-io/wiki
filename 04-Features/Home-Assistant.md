# Home Assistant Integration

BrewOS provides native Home Assistant integration with automatic entity discovery and a custom Lovelace card. This integration allows you to control your espresso machine as part of your smart home ecosystem, create automations, and integrate with other smart devices.

## Overview

Home Assistant integration transforms your espresso machine into a smart home device:

- **MQTT Auto-Discovery** - Automatic entity creation (no manual configuration)
- **35+ Entities** - Comprehensive sensors, switches, numbers, selects, buttons
- **Custom Lovelace Card** - Beautiful machine control card for dashboards
- **Example Automations** - Sample automations and dashboards to get started
- **Real-time Updates** - Live status updates via MQTT
- **Full Control** - Complete machine control from Home Assistant

## How the Integration Works

### Integration Methods

BrewOS supports two methods for Home Assistant integration:

**Method 1: MQTT Auto-Discovery (Recommended)**
- BrewOS publishes Home Assistant discovery messages via MQTT
- Home Assistant automatically discovers and creates entities
- No manual configuration required
- Works with Home Assistant's built-in MQTT integration
- Entities appear automatically in Home Assistant

**Method 2: Native Integration (HACS)**
- Custom Home Assistant integration installed via HACS
- Provides additional features and tighter integration
- Custom Lovelace card included
- More advanced functionality
- Requires HACS installation

### MQTT Auto-Discovery Explained

**How Auto-Discovery Works:**
1. BrewOS connects to your MQTT broker (Home Assistant's or external)
2. BrewOS publishes discovery messages to `homeassistant/` topic
3. Home Assistant's MQTT integration listens for discovery messages
4. When discovery message received, Home Assistant creates entity automatically
5. Entity appears in Home Assistant with proper device, name, and state
6. Updates flow automatically via MQTT topics

**Discovery Message Format:**
- Published to: `homeassistant/{component}/{device_id}/{entity_id}/config`
- Contains: Entity configuration, device info, availability topic, state topic, command topic
- Home Assistant reads this and creates entity automatically
- No manual YAML configuration needed

**Advantages:**
- **Zero configuration** - Entities appear automatically
- **Standard method** - Uses Home Assistant's standard MQTT discovery
- **Easy setup** - Just enable in BrewOS settings
- **Automatic updates** - New entities appear automatically if firmware adds them

### Communication Flow

**Status Updates (Machine → Home Assistant):**
```
ESP32 → MQTT Broker → Home Assistant
```
- Machine publishes status to MQTT topics
- Home Assistant subscribes to these topics
- Status updates flow automatically
- Real-time updates (typically 1 second intervals)

**Commands (Home Assistant → Machine):**
```
Home Assistant → MQTT Broker → ESP32 → Pico
```
- You control entity in Home Assistant
- Home Assistant publishes command to MQTT
- ESP32 receives command and processes it
- ESP32 sends command to Pico for execution
- Status update confirms command executed

## Setup

### Method 1: MQTT Auto-Discovery (Recommended)

1. **Enable MQTT in BrewOS**:
   - Settings → MQTT
   - Enable MQTT
   - Configure broker (Home Assistant MQTT broker)
   - Enable "Home Assistant Auto-Discovery"

2. **Home Assistant**:
   - Auto-discovers entities automatically
   - No manual configuration needed
   - Entities appear in Home Assistant

### Method 2: Native Integration

1. **Install HACS** (if not already installed)

2. **Add repository**:
   - HACS → Integrations → Custom Repositories
   - Add: `https://github.com/brewos-io/homeassistant`

3. **Install integration**:
   - HACS → Integrations
   - Search "BrewOS"
   - Install and restart Home Assistant

4. **Configure**:
   - Settings → Devices & Services
   - Add BrewOS integration
   - Enter device information

## Discovered Entities

### Sensors

- **Temperature sensors**: Brew, steam, group head
- **Pressure sensor**: Brew pressure
- **Power sensors**: Current power, daily usage, voltage
- **Statistics**: Shots today, total shots, energy
- **Status sensors**: Machine state, connection status

### Switches

- **Machine power**: Turn machine on/off
- **Eco mode**: Enable/disable eco mode

### Numbers

- **Temperature setpoints**: Brew and steam setpoints
- **Target weight**: Brew-by-weight target

### Selects

- **Heating strategy**: Sequential, parallel, smart stagger
- **Machine mode**: Standby, on, eco

### Buttons

- **Brew control**: Start/stop brewing
- **Tare scale**: Zero scale
- **Various controls**: Additional machine controls

## Custom Lovelace Card

### Installation

1. **Install via HACS**:
   - HACS → Frontend
   - Search "BrewOS Card"
   - Install

2. **Add to dashboard**:
   - Edit dashboard
   - Add card
   - Select "BrewOS Card"
   - Configure entity

### Features

- **Temperature gauges** - Visual temperature display
- **Machine status** - Current state and mode
- **Quick controls** - Power, brewing, mode selection
- **Statistics** - Shot count, power usage
- **Real-time updates** - Live data updates

## Example Automations

### Morning Coffee

```yaml
automation:
  - alias: "Morning Coffee"
    trigger:
      - platform: time
        at: "07:00:00"
    action:
      - service: switch.turn_on
        entity_id: switch.brewos_machine_power
      - delay: "00:20:00"  # Wait for heat-up
      - service: notify.mobile_app
        data:
          message: "Coffee machine is ready!"
```

### Auto Power-Off

```yaml
automation:
  - alias: "Auto Power-Off After Idle"
    trigger:
      - platform: state
        entity_id: sensor.brewos_machine_state
        to: "ready"
        for: "01:00:00"  # 1 hour idle
    action:
      - service: switch.turn_off
        entity_id: switch.brewos_machine_power
```

### Low Water Alert

```yaml
automation:
  - alias: "Low Water Alert"
    trigger:
      - platform: state
        entity_id: binary_sensor.brewos_water_low
        to: "on"
    action:
      - service: notify.mobile_app
        data:
          message: "Water tank is low!"
```

## Dashboard Examples

See [homeassistant/examples/](../homeassistant/examples/) for complete dashboard and automation examples.

## Best Practices

### Entity Organization

- **Group entities** - Create groups for easy access
- **Custom names** - Rename entities for clarity
- **Room assignment** - Assign to appropriate room

### Automations

- **Schedules** - Use for daily routines
- **Notifications** - Alert on important events
- **Integration** - Integrate with other devices
- **Testing** - Test automations before relying on them

## Troubleshooting

### Entities Not Appearing

- **Check MQTT** - Verify MQTT is enabled and connected
- **Check auto-discovery** - Verify auto-discovery is enabled
- **Check broker** - Verify Home Assistant MQTT broker is configured
- **Restart HA** - May need to restart Home Assistant

### Card Not Displaying

- **Check installation** - Verify card is installed
- **Check entity** - Verify entity ID is correct
- **Check browser** - Clear browser cache
- **Check logs** - Review Home Assistant logs

### No Updates

- **Check MQTT** - Verify MQTT connection
- **Check topics** - Verify topic structure
- **Check broker** - Verify broker is running
- **Review logs** - Check for MQTT errors

## Related Documentation

- [MQTT Integration](MQTT-Integration.md) - MQTT setup
- [Home Assistant Repository](https://github.com/brewos-io/homeassistant) - Complete integration docs

---

**Next:** [Cloud Access](Cloud-Access.md) or [Push Notifications](Push-Notifications.md)

