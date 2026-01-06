# Cloud Access

BrewOS Cloud provides secure remote access to your machine from anywhere via a WebSocket relay service. This feature enables you to control and monitor your espresso machine from any location with internet access, making it perfect for starting your machine before you arrive home or monitoring it while away.

## Overview

Cloud access extends your local web interface to work over the internet:

- **Remote control** - Control machine from anywhere with internet
- **Secure authentication** - Google OAuth authentication ensures only you can access
- **WebSocket relay** - Real-time bidirectional communication through secure relay
- **Device pairing** - Easy device pairing and sharing with secure codes
- **Push notifications** - Receive alerts remotely even when interface isn't open
- **Multi-device access** - Access from multiple devices simultaneously
- **No port forwarding** - Works without router configuration

## How Cloud Access Works

### Architecture Overview

**Local Connection (Direct):**
```
Your Device ←→ WiFi Router ←→ ESP32 (in machine)
```
- Direct connection on local network
- Fastest, lowest latency
- No internet required

**Cloud Connection (Relay):**
```
Your Device ←→ Internet ←→ Cloud Service ←→ Internet ←→ ESP32 (in machine)
```
- Your device connects to cloud service
- Cloud service relays to your machine
- Both connections use encrypted WebSocket (WSS)
- Works from anywhere with internet

### Technical Details

**WebSocket Relay:**
- Both your device and machine maintain persistent WebSocket connections to cloud service
- Cloud service acts as a message relay (doesn't store data)
- Commands from your device → cloud → machine
- Status updates from machine → cloud → your device
- Real-time bidirectional communication maintained

**Security:**
- **Encryption**: All communication uses WSS (WebSocket Secure/TLS)
- **Authentication**: Google OAuth ensures only authorized users
- **Device pairing**: Secure pairing code prevents unauthorized access
- **Session management**: Secure session handling with tokens
- **No data storage**: Cloud service doesn't store your machine data

**Connection Flow:**
1. Machine connects to cloud service on startup (if enabled)
2. Maintains persistent WebSocket connection
3. You sign in to cloud.brewos.io with Google account
4. Cloud service verifies your account has access to machine
5. Cloud service establishes relay between your device and machine
6. All communication flows through encrypted relay

### Local vs Cloud Comparison

| Feature | Local Access | Cloud Access |
|---------|--------------|--------------|
| **Location** | Same network only | Anywhere with internet |
| **Speed** | Fastest (<50ms latency) | Slightly slower (100-500ms) |
| **Internet Required** | No | Yes (both ends) |
| **Setup Complexity** | Simple (just connect) | Requires pairing |
| **Privacy** | Maximum (local only) | Data passes through cloud |
| **Cost** | Free | Free (no subscription) |
| **Reliability** | Depends on local network | Depends on internet + cloud |
| **Use Case** | Home use | Remote access |

**When to Use Each:**
- **Local**: When at home, fastest response, maximum privacy
- **Cloud**: When away, remote monitoring, starting machine before arrival
- **Both**: Can use simultaneously on different devices

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

Device sharing allows you to grant access to your machine to family members, roommates, or trusted individuals without sharing your Google account credentials.

**How Sharing Works:**
1. **Enable sharing**:
   - Settings → Cloud → Sharing
   - Enable device sharing
   - Generate share link or pairing code
   - Set permission level

2. **Share access**:
   - Send share link or code to others
   - They use the code to pair with your machine
   - They can access your machine with their own Google account
   - You maintain control and can revoke access anytime

**Use Cases:**
- **Family members**: Spouse, roommates can control machine
- **Guests**: Temporary access for visitors
- **Multiple users**: Each person uses their own account
- **Access control**: You decide who can access and what they can do

### Permissions

**Full Access:**
- Complete control of machine
- Can change settings, temperatures, schedules
- Can start/stop brewing
- Can modify all configurations
- **Use for**: Trusted family members, primary users

**Read-Only:**
- View machine status and temperatures
- See statistics and shot history
- Cannot control machine or change settings
- Cannot start brewing or modify anything
- **Use for**: Monitoring only, guests, demonstration

**Limited Access:**
- Specific features only (configurable)
- Can view but limited control
- Can start brewing but not change settings
- Custom permission set
- **Use for**: Specific use cases, partial access needs

**Managing Shared Access:**
- View all users with access
- Revoke access at any time
- Change permission levels
- See access history (who accessed when)

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
