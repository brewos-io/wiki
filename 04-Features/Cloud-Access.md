# Cloud Access

BrewOS Cloud provides secure remote access to your machine from anywhere via a WebSocket relay service.

## Overview

Cloud access features:

- **Remote control** - Control machine from anywhere
- **Secure authentication** - Google OAuth authentication
- **WebSocket relay** - Real-time bidirectional communication
- **Device pairing** - Easy device pairing and sharing
- **Push notifications** - Receive alerts remotely

## Setup

### Prerequisites

- **Cloud service** - Access to BrewOS cloud service
- **Google account** - For authentication
- **WiFi connection** - Machine must be connected to internet

### Enable Cloud Access

1. **In BrewOS settings**:

   - Go to Settings → Cloud
   - Enable "Cloud Access"
   - Note pairing code displayed

2. **Pair device**:
   - Go to `https://cloud.brewos.io`
   - Sign in with Google account
   - Enter pairing code
   - Device appears in your devices list

### Configuration

- **Device name** - Custom name for your machine
- **Sharing** - Share device with others (optional)
- **Notifications** - Enable push notifications

## Using Cloud Access

### Accessing Your Machine

1. **Sign in**:

   - Go to `https://cloud.brewos.io`
   - Sign in with Google account
   - Select your machine from devices list

2. **Control machine**:
   - Full web interface available
   - All features accessible remotely
   - Real-time updates via WebSocket

### Features Available

- **Dashboard** - Full dashboard access
- **Brewing** - Start/stop shots remotely
- **Temperature control** - Adjust setpoints
- **Statistics** - View shot history
- **Settings** - Configure machine settings
- **Logs** - View system logs

## Device Sharing

### Share with Others

1. **Enable sharing**:

   - Settings → Cloud → Sharing
   - Enable device sharing
   - Generate share link or code

2. **Share link**:
   - Send share link to others
   - They can access your machine
   - Permissions can be limited

### Permissions

- **Full access** - Complete control
- **Read-only** - View only, no control
- **Limited** - Specific features only

## Push Notifications

### Setup

1. **Enable notifications**:

   - Settings → Push Notifications
   - Subscribe to notifications
   - Grant browser permissions

2. **Configure**:
   - Select notification types
   - Machine ready alerts
   - Low water warnings
   - Error notifications

### Notification Types

- **Machine ready** - When machine reaches temperature
- **Low water** - When water tank is low
- **Error alerts** - When errors occur
- **Maintenance** - Cleaning reminders

See [Push Notifications](Push-Notifications.md) for details.

## Security

### Authentication

- **Google OAuth** - Secure Google authentication
- **Device pairing** - Secure pairing process
- **Session management** - Secure session handling

### Data Protection

- **Encrypted communication** - WSS (WebSocket Secure)
- **No data storage** - Cloud doesn't store machine data
- **Privacy** - Your data stays private

## Troubleshooting

### Cannot Connect

- **Check internet** - Verify machine has internet
- **Check cloud service** - Verify cloud service is available
- **Check pairing** - Verify device is paired
- **Try re-pairing** - Unpair and re-pair device

### Connection Drops

- **Check internet** - Verify stable internet connection
- **Check firewall** - Router may block WebSocket
- **Check cloud service** - Service may be temporarily unavailable
- **Reconnect** - Connection should auto-reconnect

### Notifications Not Working

- **Check permissions** - Verify browser notification permissions
- **Check subscription** - Verify notifications are subscribed
- **Check browser** - Some browsers have notification limitations
- **Try different browser** - Test with different browser

## Best Practices

### Security

- **Strong Google account** - Use strong Google password
- **Two-factor auth** - Enable 2FA on Google account
- **Device sharing** - Only share with trusted users
- **Regular review** - Review shared devices regularly

### Usage

- **Bookmark** - Bookmark cloud access URL
- **Install PWA** - Install as Progressive Web App
- **Notifications** - Enable for important alerts
- **Monitor** - Check connection status regularly

## Related Features

- [Push Notifications](Push-Notifications.md) - Remote alerts
- [WiFi Connectivity](WiFi-Connectivity.md) - Local network
- [Home Assistant Integration](Home-Assistant.md) - Smart home

---

**Next:** [Push Notifications](Push-Notifications.md) or [Power Metering](Power-Metering.md)
