# Web Interface Guide

The BrewOS web interface is a Progressive Web App (PWA) that provides full control and monitoring of your espresso machine from any device. This guide explains how the interface works, the differences between local and cloud access, and how to get the most out of your BrewOS system.

## Understanding Local vs Cloud Access

BrewOS provides two ways to access your machine's web interface, each with different characteristics and use cases:

### Local Network Access (Direct Connection)

**How It Works:**
- The ESP32 microcontroller in your machine runs a web server directly
- When you connect to `brewos.local` or the machine's IP address, your device communicates directly with the ESP32
- All communication happens over your local WiFi network
- No internet connection required - works completely offline
- Data never leaves your local network

**Technical Details:**
- The ESP32 serves the web interface files (HTML, CSS, JavaScript) from its flash memory
- Real-time updates use WebSocket connections directly to the ESP32
- Communication is bidirectional: your device sends commands and receives status updates
- The ESP32 communicates with the Pico control board via high-speed UART (921600 baud) for machine control

**Advantages:**
- **Fastest response** - Direct connection means minimal latency
- **No internet required** - Works even if your internet is down
- **Privacy** - All data stays on your local network
- **No external dependencies** - Doesn't rely on cloud services
- **Free** - No cloud service fees or subscriptions

**Limitations:**
- **Same network only** - You must be on the same WiFi network as the machine
- **No remote access** - Can't control from outside your home
- **Network discovery** - Requires mDNS (Bonjour) or knowing the IP address

### Cloud Access (Remote Connection)

**How It Works:**
- Your machine connects to the BrewOS cloud service via secure WebSocket (WSS)
- The cloud service acts as a relay between your device and your machine
- When you access `https://cloud.brewos.io`, you connect to the cloud service
- The cloud service forwards your commands to your machine and relays status back
- Requires both your device and machine to have internet connectivity

**Technical Details:**
- Uses WebSocket Secure (WSS) for encrypted communication
- Google OAuth authentication ensures only authorized users can access your machine
- Device pairing uses a secure pairing code system
- The cloud service doesn't store your machine data - it only relays messages in real-time
- Supports multiple simultaneous connections (you can have the interface open on multiple devices)

**Advantages:**
- **Remote access** - Control your machine from anywhere with internet
- **Easy access** - No need to remember IP addresses or be on the same network
- **Secure** - Encrypted communication and authentication
- **Multi-device** - Access from phone, tablet, or computer anywhere
- **Push notifications** - Receive alerts even when away from home

**Limitations:**
- **Internet required** - Both your device and machine need internet
- **Slight latency** - Commands go through cloud relay (typically 100-500ms)
- **Cloud dependency** - Requires cloud service to be available
- **Privacy consideration** - Data passes through cloud service (though not stored)

### When to Use Each

**Use Local Access When:**
- You're at home on the same network
- You want the fastest possible response
- Your internet is down but WiFi still works
- You prefer maximum privacy
- You're doing initial setup or troubleshooting

**Use Cloud Access When:**
- You want to control the machine remotely
- You're away from home but want to start heating
- You want to receive notifications when away
- You're accessing from a different network
- You want the convenience of a single URL

**Both Can Work Together:**
- You can have local access open on one device and cloud access on another
- The interface automatically detects which connection method is available
- Local access is always preferred when available (faster)

## Accessing the Interface

### Local Network Access

1. **Find your machine**:

   - Use `http://brewos.local` (if mDNS is enabled) - This is the easiest method
   - Or use the ESP32 IP address (displayed on screen or in router)
   - Default: `http://192.168.1.x` (varies by network)
   - Check your router's device list to find the machine's IP

2. **Connect to same WiFi**:
   - Ensure your device is on the same network as the machine
   - 2.4GHz network required (ESP32 doesn't support 5GHz)
   - Both devices must be on the same subnet

3. **How mDNS Works:**
   - mDNS (multicast DNS) allows you to use `brewos.local` instead of an IP address
   - The ESP32 broadcasts its hostname on the local network
   - Your device resolves `brewos.local` to the machine's IP automatically
   - If mDNS doesn't work, use the IP address directly

### Cloud Access (Optional)

If cloud service is configured:

1. **Navigate to**: `https://cloud.brewos.io`
2. **Sign in** with Google account (OAuth authentication)
3. **Select your machine** from paired devices
4. **Control remotely** from anywhere with internet

**Initial Setup:**
- First, enable cloud access in your machine's settings
- Note the pairing code displayed
- Use this code to pair your machine with your cloud account
- Once paired, the machine appears in your device list

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

The interface uses WebSocket for real-time bidirectional communication:

**How WebSocket Works:**
- Unlike traditional HTTP (request/response), WebSocket maintains a persistent connection
- The ESP32 pushes updates to your device automatically without polling
- Your device can send commands instantly without waiting for page loads
- Updates happen in real-time with minimal latency (typically <100ms on local network)

**What Updates in Real-Time:**
- **Temperatures** - Brew, steam, and group head temperatures update every second
- **Pressure** - Pressure readings during brewing update multiple times per second
- **Machine state** - Status changes (heating, ready, brewing) reflect immediately
- **Power consumption** - Power meter readings update continuously
- **Scale weight** - Weight readings update in real-time during brewing
- **Connection status** - Shows when connected/disconnected

**Connection Management:**
- **Automatic reconnection** - If connection drops, the interface automatically reconnects
- **Connection status indicator** - Visual indicator shows connection health
- **Graceful degradation** - Interface works even with intermittent connectivity
- **Heartbeat** - Regular ping/pong messages keep connection alive

**Local vs Cloud WebSocket:**
- **Local**: Direct WebSocket connection to ESP32 (fastest, lowest latency)
- **Cloud**: WebSocket to cloud service, which relays to machine (slightly higher latency but works remotely)

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
