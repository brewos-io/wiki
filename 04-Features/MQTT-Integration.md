# MQTT Integration

BrewOS supports MQTT (Message Queuing Telemetry Transport) for home automation integration with Home Assistant, Node-RED, and other automation platforms.

## Overview

MQTT provides:
- **Lightweight messaging** - Efficient pub/sub protocol
- **Home automation** - Integrate with Home Assistant, Node-RED
- **Real-time updates** - Machine status published continuously
- **Command control** - Control machine via MQTT commands

## Setup

### Broker Configuration

1. **Install MQTT broker** (if needed):
   - **Mosquitto** - Popular open-source broker
   - **Home Assistant** - Built-in MQTT broker
   - **Cloud broker** - Various cloud MQTT services

2. **Configure in BrewOS**:
   - Go to Settings → MQTT
   - Enable MQTT
   - Enter broker address (IP or hostname)
   - Enter port (default: 1883)
   - Enter username/password (if required)
   - Save configuration

### Connection

After configuration:
- ESP32 connects to broker automatically
- Status published to MQTT topics
- Commands can be sent via MQTT
- Auto-discovery available for Home Assistant

## Topic Structure

All topics follow pattern: `{prefix}/{device_id}/{topic}`

Default prefix: `brewos`  
Device ID: Derived from MAC address

### Topics

| Topic | Direction | Description |
|-------|-----------|-------------|
| `brewos/{id}/availability` | Publish | Online/offline status (LWT) |
| `brewos/{id}/status` | Publish | Full machine status JSON |
| `brewos/{id}/power` | Publish | Power meter readings |
| `brewos/{id}/statistics` | Publish | Shot/energy statistics |
| `brewos/{id}/shot` | Publish | Shot data when brewing completes |
| `brewos/{id}/command` | Subscribe | Incoming commands |

## Status Messages

### Machine Status

Published every 1 second to `brewos/{id}/status`:

```json
{
  "state": "ready",
  "mode": "on",
  "heating_strategy": 1,
  "brew_temp": 93.5,
  "brew_setpoint": 94.0,
  "steam_temp": 145.2,
  "steam_setpoint": 145.0,
  "pressure": 9.1,
  "scale_weight": 0.0,
  "is_brewing": false,
  "is_heating": false,
  "water_low": false,
  "pico_connected": true,
  "wifi_connected": true
}
```

### Machine States

- `standby` - Machine off/idle
- `heating` - Heating to setpoint
- `ready` - At temperature, ready to brew
- `brewing` - Actively brewing
- `steaming` - Steam wand active
- `fault` - Error condition

## Commands

Send commands to `brewos/{id}/command`:

### Power Control

```json
{
  "cmd": "set_mode",
  "mode": "on"
}
```

```json
{
  "cmd": "set_mode",
  "mode": "standby"
}
```

### Temperature Control

```json
{
  "cmd": "set_temp",
  "brew": 94.0,
  "steam": 145.0
}
```

### Brewing

```json
{
  "cmd": "start_brew"
}
```

```json
{
  "cmd": "stop_brew"
}
```

### Eco Mode

```json
{
  "cmd": "enter_eco"
}
```

```json
{
  "cmd": "exit_eco"
}
```

## Home Assistant Auto-Discovery

### Enable Auto-Discovery

1. **Enable in settings**:
   - Settings → MQTT
   - Enable "Home Assistant Auto-Discovery"

2. **Automatic entities**:
   - Home Assistant discovers entities automatically
   - 35+ entities created automatically
   - No manual configuration needed

### Discovered Entities

- **Sensors**: Temperature, pressure, power, statistics
- **Switches**: Machine power, eco mode
- **Numbers**: Temperature setpoints
- **Selects**: Heating strategy, mode
- **Buttons**: Brew start/stop, various controls

See [Home Assistant Integration](Home-Assistant.md) for details.

## Usage Examples

### Home Assistant

```yaml
# Example automation
automation:
  - alias: "Morning Coffee"
    trigger:
      - platform: time
        at: "07:00:00"
    action:
      - service: switch.turn_on
        entity_id: switch.brewos_machine_power
```

### Node-RED

```javascript
// Example flow
msg.topic = "brewos/device123/command";
msg.payload = JSON.stringify({
  cmd: "set_mode",
  mode: "on"
});
return msg;
```

## Best Practices

### Broker Setup

- **Local broker** - Use local broker for reliability
- **Secure** - Use authentication (username/password)
- **TLS** - Enable TLS for security (if supported)
- **Persistence** - Enable message persistence

### Topic Management

- **Custom prefix** - Use custom topic prefix if needed
- **Device naming** - Meaningful device IDs
- **Organization** - Organize topics logically

### Automation

- **Status monitoring** - Monitor machine status
- **Automated control** - Use schedules via MQTT
- **Notifications** - Send alerts on state changes
- **Integration** - Integrate with other devices

## Troubleshooting

### Not Connecting to Broker

- **Check broker address** - Verify IP/hostname
- **Check port** - Verify port (default: 1883)
- **Check credentials** - Verify username/password
- **Check network** - Ensure broker is reachable
- **Check firewall** - Router may block MQTT port

### No Messages Published

- **Check connection** - Verify MQTT connection status
- **Check broker** - Verify broker is running
- **Check topics** - Verify topic structure
- **Review logs** - Check for MQTT errors

### Commands Not Working

- **Check topic** - Verify command topic is correct
- **Check format** - Verify JSON format
- **Check permissions** - Broker may restrict commands
- **Review logs** - Check for command errors

## Related Features

- [Home Assistant Integration](Home-Assistant.md) - Native HA integration
- [Cloud Access](Cloud-Access.md) - Remote access
- [Scheduling](Scheduling.md) - Automation

---

**Next:** [Home Assistant Integration](Home-Assistant.md) or [Cloud Access](Cloud-Access.md)

