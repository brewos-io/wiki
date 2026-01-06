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

All data updates automatically via WebSocket:
- Temperatures update every second
- Pressure updates during brewing
- Status changes reflect immediately
- No page refresh needed

### Temperature Monitoring

Monitor all temperature zones:
- **Brew boiler** - Precise PID control
- **Steam boiler** - Steam temperature
- **Group head** - Shot temperature

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

