# Dashboard Overview

The Dashboard is the main control and monitoring page of the BrewOS web interface. It provides an overview of your machine's status and quick access to common functions.

## Layout

The Dashboard is organized into several key areas:

### Header Section

- **Machine Status** - Current state (ON, OFF, HEATING, READY, etc.)
- **Connection Status** - Pico and ESP32 connection indicators
- **Quick Actions** - Power button, mode selector

### Temperature Section

**Brew Temperature Gauge**:
- Current temperature (large display)
- Setpoint (target temperature)
- Visual gauge showing temperature range
- Color coding (blue=cold, green=ready, red=hot)

**Steam Temperature Gauge**:
- Current steam boiler temperature
- Setpoint for steam
- Visual gauge
- Status indicator

**Group Head Temperature**:
- Real-time group head temperature
- Thermocouple reading
- Important for shot quality

### Machine Status Card

Shows current machine state:
- **Mode** - Standby, Ready, Heating, etc.
- **State** - Detailed state information
- **Uptime** - How long machine has been on
- **Last Shot** - Time since last shot

### Quick Stats

Summary cards showing:
- **Power Consumption** - Current power and daily usage
- **Water Tank** - Tank level indicator
- **Scale** - Connected scale weight (if available)
- **Maintenance** - Shots since last cleaning

### Pressure Card

(Shown during and after brewing)
- Real-time pressure reading
- Pressure graph during shot
- Peak pressure indicator

### Last Shot Card

Summary of most recent shot:
- Shot time
- Temperature at shot start
- Peak pressure
- Link to full shot details

## Key Features

### Real-Time Updates

The Dashboard uses WebSocket technology for real-time bidirectional communication:

**How Real-Time Updates Work:**
- **WebSocket Connection**: Persistent connection between your device and ESP32
- **Push Updates**: ESP32 pushes data to your device automatically (no polling)
- **Bidirectional**: Your device can send commands, ESP32 sends status updates
- **Low Latency**: Updates appear almost instantly (<100ms on local network)
- **Automatic Reconnection**: If connection drops, automatically reconnects

**Update Frequencies:**
- **Temperatures**: Update every 1 second (brew, steam, group head)
- **Pressure**: Updates multiple times per second during brewing (10-20 Hz)
- **Status changes**: Reflect immediately when machine state changes
- **Power meter**: Updates every 1 second (if installed)
- **Scale weight**: Updates in real-time during brewing (if connected)
- **Connection status**: Updates when connection state changes

**What Updates in Real-Time:**
- All temperature readings (brew, steam, group head)
- Machine state (standby, heating, ready, brewing, etc.)
- Pressure readings during brewing
- Power consumption and energy usage
- Scale weight during brewing
- Connection status indicators
- Shot timer and statistics

**No Page Refresh Needed:**
- Traditional web pages require refresh to see new data
- Dashboard uses WebSocket for live updates
- Data flows continuously without page reload
- Seamless user experience

### Temperature Monitoring

The Dashboard provides comprehensive temperature monitoring across all critical zones:

**Brew Boiler Temperature:**
- **Purpose**: Water temperature for espresso extraction
- **Control**: Precise PID control maintains setpoint within ±0.1°C
- **Typical Range**: 90-97°C (194-207°F) depending on coffee and preference
- **Display**: Large gauge shows current temperature and setpoint
- **Color Coding**: Blue (below), green (at setpoint), red (above)
- **Importance**: Critical for consistent espresso extraction

**Steam Boiler Temperature:**
- **Purpose**: Steam generation for milk frothing
- **Control**: Independent PID loop (separate from brew boiler)
- **Typical Range**: 140-145°C (284-293°F)
- **Display**: Separate gauge with setpoint indicator
- **Status**: Shows when steam is ready
- **Auto-fill**: Automatic water level management

**Group Head Temperature:**
- **Purpose**: Temperature at the point of extraction (most critical)
- **Monitoring**: K-type thermocouple measures group head temperature
- **No Control**: Group head is passive (monitored only, not controlled)
- **Display**: Real-time reading shown on dashboard
- **Importance**: Most important temperature for shot quality
- **Thermal Mass**: Group head temperature lags behind boiler temperature
- **Preheating**: Takes 15-20 minutes for group head to fully heat

**Understanding Temperature Relationships:**
- **Brew boiler** → **Group head**: Heat transfers from boiler to group head
- **Thermal lag**: Group head takes time to reach boiler temperature
- **Stability**: Group head temperature should stabilize before brewing
- **Recovery**: Group head cools slightly during shot, recovers between shots

### Power Monitoring

(If power meter is installed)
- **Current power** - Real-time consumption
- **Daily usage** - kWh consumed today
- **Voltage** - Line voltage reading

### Quick Actions

From the dashboard, you can:
- **Turn machine on/off** - Power button
- **Change mode** - Select heating strategy
- **Start brewing** - Quick brew button
- **View details** - Click cards for more info

## Understanding Status Indicators

### Machine States

- **STANDBY** - Machine is off
- **HEATING** - Boilers are heating up
- **READY** - At temperature, ready to brew
- **BREWING** - Actively pulling a shot
- **ECO** - Energy-saving mode
- **ERROR** - Fault condition (see logs)

### Connection Status

- **Pico: Connected** - Control board communicating
- **Pico: Disconnected** - Check UART wiring
- **ESP32: Connected** - WiFi connected
- **ESP32: Disconnected** - WiFi issue

### Temperature Indicators

- **Blue** - Below setpoint (heating)
- **Green** - At setpoint (ready)
- **Red** - Above setpoint (over-temperature)

## Using the Dashboard

### Daily Use

1. **Check status** - Verify machine is ready
2. **Monitor temperatures** - Ensure at setpoint
3. **Pull shot** - Use brew button or go to Brewing page
4. **Review stats** - Check power usage, shot count

### Monitoring

- **Watch temperature stability** - Should be within 0.1°C
- **Check power consumption** - Monitor energy usage
- **Review last shot** - Quick reference to shot details
- **Monitor maintenance** - Cleaning reminders

### Quick Actions

- **Power toggle** - Turn machine on/off quickly
- **Mode selection** - Change heating strategy
- **Brew start** - Quick access to brewing controls

## Customization

Some dashboard elements can be customized:

- **Temperature units** - Celsius or Fahrenheit (Settings)
- **Display preferences** - Show/hide certain cards
- **Layout** - Responsive to screen size

## Tips

1. **Monitor group head temp** - Important for shot quality
2. **Watch pressure during shot** - Should be 8-9 bar
3. **Check power usage** - Helps optimize schedules
4. **Review last shot** - Learn from each shot
5. **Use quick actions** - Faster workflow

## Troubleshooting

### No Data Showing

- Check connection status indicators
- Verify Pico is connected
- Review logs for errors
- Try refreshing page

### Temperatures Not Updating

- Check WebSocket connection
- Verify sensor readings in logs
- Check sensor wiring
- Review diagnostic information

### Pressure Not Showing

- Pressure card only shows during/after brewing
- Verify pressure sensor is installed
- Check sensor wiring
- Review diagnostics

## Next Steps

- **Control your machine**: [Machine Control](Machine-Control.md)
- **Configure settings**: [Settings Overview](Settings-Overview.md)
- **Learn features**: [Features](../04-Features/)

---

**Next:** [Machine Control](Machine-Control.md)

