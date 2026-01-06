# Machine Control

This guide covers basic machine operations using the BrewOS interface.

## Power Control

### Turning Machine On

1. **From Dashboard**:
   - Click the power button in header
   - Or use quick action button
   - Machine enters HEATING state

2. **Heating Process**:
   - Boilers begin heating
   - Temperature gauges show progress
   - Status changes to READY when at temperature

3. **Heating Strategies**:
   - **Sequential** - Brew first, then steam (default)
   - **Parallel** - Both boilers simultaneously
   - **Smart Stagger** - Power-aware intelligent heating
   - **Brew Only** - Heat only brew boiler

### Turning Machine Off

1. **From Dashboard**:
   - Click power button again
   - Confirm shutdown
   - Machine enters STANDBY state

2. **Auto Power-Off**:
   - Can be configured in Schedules
   - Automatically turns off after idle period
   - Prevents leaving machine on

## Brewing

### Starting a Shot

1. **Prepare**:
   - Ensure machine is READY (green status)
   - Grind and dose coffee
   - Lock portafilter

2. **Start Brewing**:
   - From Dashboard: Click brew button
   - From Brewing page: Click "Start Shot"
   - Or use physical brew lever (if configured)

3. **During Shot**:
   - Shot timer starts automatically
   - Pressure graph displays
   - Scale weight updates (if connected)
   - Temperature monitored

### Stopping a Shot

1. **Manual Stop**:
   - Click "Stop Shot" button
   - Or use physical lever
   - Shot timer stops

2. **Brew by Weight** (if configured):
   - Shot stops automatically at target weight
   - Scale signals when weight reached
   - Pump stops automatically

### Shot Timer

The shot timer provides:
- **Elapsed time** - How long shot has been running
- **Target time** - Your target shot time (if set)
- **Visual indicator** - Progress bar
- **Auto-start** - Starts when brewing begins

## Temperature Control

### Adjusting Setpoints

1. **From Dashboard**:
   - Click temperature gauge
   - Adjust setpoint slider
   - Changes apply immediately

2. **From Settings**:
   - Go to Settings → Temperature
   - Set brew and steam temperatures
   - Save changes

### Temperature Monitoring

Monitor temperatures in real-time:
- **Brew temperature** - Should be stable at setpoint
- **Steam temperature** - For steaming milk
- **Group head** - Important for shot quality

### PID Control

The system uses PID (Proportional-Integral-Derivative) control:
- **Automatic** - Maintains temperature automatically
- **Precise** - Within 0.1°C stability
- **Configurable** - PID parameters can be tuned (advanced)

## Steam Control

### Steaming Milk

1. **Ensure steam ready**:
   - Steam boiler at temperature (140-145°C)
   - Open steam wand
   - Purge briefly

2. **Steam**:
   - Use physical steam lever/knob
   - Monitor steam pressure
   - Steam until desired texture

3. **Auto-fill**:
   - Steam boiler auto-fills when needed
   - Level probe detects low water
   - Fills automatically (when not brewing)

## Mode Selection

### Available Modes

- **Standby** - Machine off
- **Ready** - At temperature, ready to use
- **Eco Mode** - Energy-saving idle mode
- **Brew Only** - Heat only brew boiler

### Changing Mode

1. **From Dashboard**:
   - Click mode selector
   - Choose desired mode
   - Machine adjusts accordingly

2. **Heating Strategy**:
   - Select heating strategy for power-on
   - Affects how boilers heat up
   - Can be changed anytime

## Water Management

### Water Tank

Monitor water level:
- **Tank indicator** - Shows level in dashboard
- **Low water warning** - Alerts when low
- **Auto-shutoff** - Prevents dry heating

### Steam Boiler Fill

Automatic filling:
- **Level probe** - Detects low water
- **Auto-fill** - Fills when needed
- **Brew priority** - Won't fill during brewing

## Safety Features

### Automatic Protections

- **Over-temperature** - Shuts off at 165°C
- **Water level** - Prevents dry heating
- **Watchdog** - Automatic shutdown on fault
- **Fail-safe** - Safe state on any error

### Error Handling

If an error occurs:
- **Error displayed** - Shows in status
- **Machine safe** - Enters safe state
- **Logs recorded** - Check logs for details
- **Manual reset** - May require power cycle

## Best Practices

### Daily Routine

1. **Morning**:
   - Turn machine on
   - Wait for READY status
   - Pull first shot
   - Monitor temperatures

2. **During Use**:
   - Monitor shot timer
   - Watch pressure during shot
   - Check temperatures
   - Review shot stats

3. **Evening**:
   - Last shot of day
   - Turn machine off
   - Or use auto power-off

### Temperature Management

- **Preheat time** - Allow 15-20 minutes for full heat
- **Group head** - Important for consistent shots
- **Stability** - Wait for stable temperature before brewing
- **Recovery** - Allow time between shots if needed

### Shot Quality

- **Consistent temperature** - Key to good shots
- **Proper pressure** - 8-9 bar during extraction
- **Shot time** - 25-30 seconds typical
- **Monitor group head** - Critical for quality

## Troubleshooting

### Machine Won't Turn On

- Check power connection
- Verify control board power
- Check for errors in logs
- Review safety interlocks

### Temperatures Not Reaching Setpoint

- Check heater connections
- Verify SSR triggers
- Check for errors
- Review PID settings

### Shot Not Starting

- Verify machine is READY
- Check for errors
- Verify pump connections
- Review logs

### Pressure Issues

- Check pressure sensor
- Verify sensor wiring
- Review pressure readings
- Check for blockages

## Next Steps

- **Configure settings**: [Settings Overview](Settings-Overview.md)
- **Learn features**: [Features](../04-Features/)
- **Review statistics**: See [Statistics](../04-Features/Statistics.md)

---

**Next:** [Settings Overview](Settings-Overview.md)

