# Web Interface Guide

The BrewOS web interface is a Progressive Web App (PWA) that provides full control and monitoring of your espresso machine from any device.

## Accessing the Interface

### Local Network Access

1. **Find your machine**:

   - Use `http://brewos.local` (if mDNS is enabled)
   - Or use the ESP32 IP address (displayed on screen or in router)
   - Default: `http://192.168.1.x` (varies by network)

2. **Connect to same WiFi**:
   - Ensure your device is on the same network as the machine
   - 2.4GHz network required (ESP32 doesn't support 5GHz)

### Cloud Access (Optional)

If cloud service is configured:

1. **Navigate to**: `https://cloud.brewos.io`
2. **Sign in** with Google account
3. **Select your machine** from paired devices
4. **Control remotely** from anywhere

## Installing as PWA

The web interface can be installed as a Progressive Web App for an app-like experience:

### Installation Steps

1. **Open web interface** in browser
2. **Look for install prompt**:

   - Chrome/Edge: Install banner at top
   - Safari: Share button → "Add to Home Screen"
   - Firefox: Menu → "Install"

3. **Install**:
   - Click install button/prompt
   - App icon appears on home screen
   - Launch like a native app

### PWA Benefits

- **Offline support** - Works without internet (local access)
- **App-like experience** - Full screen, no browser UI
- **Home screen access** - Quick launch from home screen
- **Push notifications** - Receive alerts (if configured)

## Interface Overview

### Navigation

The interface uses a sidebar navigation (desktop) or bottom navigation (mobile):

- **Dashboard** - Main control and monitoring
- **Brewing** - Shot timer and brew controls
- **Statistics** - Shot history and graphs
- **Schedules** - Auto-on/off scheduling
- **Settings** - Configuration options
- **Logs** - System diagnostics

### Main Areas

1. **Header**:

   - Machine status indicator
   - Connection status
   - Quick actions menu

2. **Content Area**:

   - Page-specific content
   - Real-time data updates
   - Control buttons

3. **Footer** (mobile):
   - Quick navigation
   - Status indicators

## Pages Overview

### Dashboard

Main control and monitoring page:

- Temperature gauges
- Machine status
- Quick stats
- Power monitoring
- Last shot summary

See [Dashboard Overview](Dashboard-Overview.md) for details.

### Brewing

Shot timer and brew controls:

- Shot timer
- Pressure graph
- Scale integration
- Brew controls

### Statistics

Shot history and analytics:

- Shot list with details
- Temperature graphs
- Pressure profiles
- Statistics summary

### Schedules

Automation and scheduling:

- Auto-on/off schedules
- Daily routines
- Auto power-off settings

### Settings

Configuration options:

- Temperature settings
- Network configuration
- MQTT setup
- Home Assistant
- Cloud access
- System settings

See [Settings Overview](Settings-Overview.md) for details.

### Logs

System diagnostics:

- Real-time logs
- Error messages
- System events
- Debug information

## Real-Time Updates

The interface uses WebSocket for real-time updates:

- **Automatic updates** - No page refresh needed
- **Live data** - Temperatures, pressure, status update instantly
- **Connection status** - Shows when connected/disconnected
- **Reconnection** - Automatically reconnects if connection drops

## Responsive Design

The interface adapts to different screen sizes:

- **Desktop** - Full sidebar navigation, large graphs
- **Tablet** - Optimized layout, touch-friendly
- **Mobile** - Bottom navigation, compact layout

## Browser Compatibility

Supported browsers:

- **Chrome/Edge** (recommended) - Full PWA support
- **Firefox** - Full functionality
- **Safari** - Full functionality (iOS 11.3+)
- **Opera** - Full functionality

## Keyboard Shortcuts

- **Space** - Toggle machine power (when focused)
- **B** - Start/stop brewing (when focused)
- **Esc** - Close modals/dialogs

## Tips and Best Practices

1. **Bookmark the interface** - Easy access from any device
2. **Install as PWA** - Better experience, offline support
3. **Use cloud access** - Control from anywhere
4. **Check connection status** - Ensure real-time updates are working
5. **Clear cache if needed** - If interface seems outdated

## Troubleshooting

### Interface Not Loading

- **Check connection** - Verify you're on same network
- **Try different browser** - Some browsers cache aggressively
- **Clear cache** - Clear browser cache and cookies
- **Check IP address** - Verify correct IP or hostname

### No Real-Time Updates

- **Check WebSocket** - Look for connection status indicator
- **Refresh page** - Sometimes reconnection needed
- **Check network** - Verify network connectivity
- **Review logs** - Check for connection errors

### PWA Not Installing

- **Check browser** - Ensure browser supports PWA
- **Check HTTPS** - PWA requires HTTPS (or localhost)
- **Try manual install** - Use browser menu option
- **Check permissions** - Ensure browser has necessary permissions

## Next Steps

- **Learn the dashboard**: [Dashboard Overview](Dashboard-Overview.md)
- **Control your machine**: [Machine Control](Machine-Control.md)
- **Configure settings**: [Settings Overview](Settings-Overview.md)

---

**Next:** [Dashboard Overview](Dashboard-Overview.md)
