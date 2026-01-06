# API Reference

REST API and WebSocket API reference for automating and integrating BrewOS.

## Overview

BrewOS provides APIs for:

- **REST API**: HTTP-based API for control and status
- **WebSocket API**: Real-time bidirectional communication
- **MQTT API**: MQTT-based automation (see [MQTT Integration](../04-Features/MQTT-Integration.md))

## REST API

### Base URL

- **Local**: `http://brewos.local` or `http://<ip-address>`
- **Cloud**: `https://cloud.brewos.io`

### Authentication

- **Local**: No authentication required (on local network)
- **Cloud**: Google OAuth authentication required

### Endpoints

#### Get Status

```
GET /api/status
```

Returns current machine status.

**Response:**

```json
{
  "state": "ready",
  "mode": "on",
  "brew_temp": 93.5,
  "steam_temp": 145.2,
  "pressure": 9.1,
  "is_brewing": false
}
```

#### Set Temperature

```
POST /api/temperature
Content-Type: application/json

{
  "brew": 94.0,
  "steam": 145.0
}
```

#### Control Machine

```
POST /api/control
Content-Type: application/json

{
  "mode": "on"  // or "standby", "eco"
}
```

#### Start/Stop Brewing

```
POST /api/brew
Content-Type: application/json

{
  "action": "start"  // or "stop"
}
```

## WebSocket API

### Connection

```
WS ws://brewos.local/ws
```

### Message Format

**Status Updates** (from machine):

```json
{
  "type": "status",
  "data": {
    "state": "ready",
    "brew_temp": 93.5,
    "steam_temp": 145.2
  }
}
```

**Commands** (to machine):

```json
{
  "type": "command",
  "cmd": "set_mode",
  "mode": "on"
}
```

### Commands

- `set_mode` - Set machine mode (on, standby, eco)
- `set_temp` - Set temperature setpoints
- `start_brew` - Start brewing
- `stop_brew` - Stop brewing
- `enter_eco` - Enter eco mode
- `exit_eco` - Exit eco mode

## Usage Examples

### Python Example

```python
import requests

# Get status
response = requests.get('http://brewos.local/api/status')
status = response.json()
print(f"Temperature: {status['brew_temp']}°C")

# Set temperature
requests.post('http://brewos.local/api/temperature', json={
    'brew': 94.0,
    'steam': 145.0
})
```

### JavaScript Example

```javascript
// WebSocket connection
const ws = new WebSocket("ws://brewos.local/ws");

ws.onmessage = (event) => {
  const message = JSON.parse(event.data);
  if (message.type === "status") {
    console.log("Temperature:", message.data.brew_temp);
  }
};

// Send command
ws.send(
  JSON.stringify({
    type: "command",
    cmd: "set_mode",
    mode: "on",
  })
);
```

## Best Practices

### API Usage

- **Rate limiting**: Don't send commands too frequently
- **Error handling**: Handle errors gracefully
- **Connection management**: Manage connections properly
- **Security**: Use HTTPS/WSS in production

### Automation

- **Status monitoring**: Monitor machine status
- **Conditional control**: Control based on conditions
- **Error handling**: Handle errors and timeouts
- **Logging**: Log important events

## Related Documentation

- [MQTT Integration](../04-Features/MQTT-Integration.md) - MQTT API
- [Home Assistant Integration](../04-Features/Home-Assistant.md) - HA integration
- [Cloud Access](../04-Features/Cloud-Access.md) - Cloud API

---

**Next:** [Hardware Modifications](Hardware-Modifications.md)
