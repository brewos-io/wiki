# WiFi Connectivity

BrewOS provides WiFi connectivity for local network access and remote monitoring.

## Overview

WiFi features include:
- **Access point mode** - Initial setup and fallback
- **Station mode** - Connect to your WiFi network
- **Web interface** - Access via browser
- **mDNS** - Easy access via `brewos.local`

## Initial Setup

### Access Point Mode

On first boot, ESP32 creates an access point:

1. **Find network**:
   - SSID: `BrewOS-Setup`
   - Password: `brewoscoffee`
   - Password also shown on display (if connected)

2. **Connect device**:
   - Connect to `BrewOS-Setup` network
   - Enter password: `brewoscoffee`

3. **Access interface**:
   - Navigate to `http://192.168.4.1`
   - Complete initial setup wizard

### WiFi Configuration

1. **Select network**:
   - Choose your WiFi network from list
   - Enter WiFi password
   - Save configuration

2. **Connection**:
   - ESP32 disconnects from AP mode
   - Connects to your WiFi
   - Shows new IP address

3. **Access**:
   - Note IP address displayed
   - Reconnect device to your WiFi
   - Access at new IP or `brewos.local`

## Network Configuration

### Settings

Configure WiFi in Settings → Network:

- **SSID** - WiFi network name
- **Password** - WiFi password
- **Static IP** - Optional static IP configuration
- **mDNS Name** - Hostname (default: `brewos.local`)

### Static IP (Optional)

Set static IP if needed:
- **IP Address** - Desired IP address
- **Subnet Mask** - Network subnet mask
- **Gateway** - Router IP address
- **DNS** - DNS server address

### mDNS

mDNS allows easy access:
- **Hostname** - `brewos.local` (default)
- **Automatic** - Works on most networks
- **Access** - Use `http://brewos.local` instead of IP

## Connection Status

### Monitoring

Check connection status:
- **Dashboard** - Shows WiFi status
- **Settings** - Network settings page
- **Display** - Shows IP address (if display connected)

### Status Indicators

- **Connected** - WiFi connected, IP assigned
- **Disconnected** - Not connected to network
- **AP Mode** - In access point mode
- **Signal Strength** - WiFi signal quality

## Troubleshooting

### Cannot Connect to Access Point

- **Check ESP32 power** - Ensure ESP32 is powered
- **Check WiFi** - Verify access point is broadcasting
- **Try different device** - Some devices have AP mode issues
- **Reset ESP32** - Hold reset button, reconfigure

### WiFi Connection Fails

- **Check credentials** - Verify WiFi password is correct
- **Check 2.4GHz** - ESP32 only supports 2.4GHz (not 5GHz)
- **Check signal** - Move closer to router
- **Try manual IP** - Set static IP if DHCP fails
- **Check router** - Some routers block new devices

### Cannot Access Web Interface

- **Check IP address** - Verify correct IP
- **Check network** - Ensure on same network
- **Try mDNS** - Use `http://brewos.local`
- **Check firewall** - Router firewall may block access
- **Try different device** - Rule out device issues

### Connection Drops

- **Check signal strength** - Weak signal causes drops
- **Check router** - Router may have issues
- **Check interference** - Other devices may interfere
- **Try different channel** - Change router WiFi channel
- **Check power** - ESP32 power supply may be insufficient

### mDNS Not Working

- **Check router** - Some routers don't support mDNS
- **Use IP address** - Fall back to IP address
- **Check network** - Ensure on same network
- **Try different device** - Some devices don't support mDNS

## Best Practices

### Network Setup

- **2.4GHz network** - ESP32 requires 2.4GHz
- **Good signal** - Ensure strong WiFi signal
- **Stable router** - Use reliable router
- **Dedicated network** - Consider IoT network

### Security

- **Strong password** - Use strong WiFi password
- **WPA2/WPA3** - Use secure WiFi encryption
- **Network isolation** - Consider IoT network isolation
- **Regular updates** - Keep firmware updated

### Access

- **Bookmark IP** - Bookmark for easy access
- **Use mDNS** - Use `brewos.local` if available
- **Install PWA** - Install as Progressive Web App
- **Cloud access** - Consider cloud for remote access

## Related Features

- [Cloud Access](Cloud-Access.md) - Remote access via cloud
- [Home Assistant Integration](Home-Assistant.md) - Smart home integration
- [MQTT Integration](MQTT-Integration.md) - Automation protocol

---

**Next:** [Cloud Access](Cloud-Access.md) or [MQTT Integration](MQTT-Integration.md)

