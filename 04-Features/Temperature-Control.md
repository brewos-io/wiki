# Temperature Control

BrewOS provides precise PID (Proportional-Integral-Derivative) temperature control for consistent espresso extraction.

## Overview

Temperature control is critical for espresso quality. BrewOS uses advanced PID control algorithms to maintain temperature within 0.1°C of your setpoint, ensuring consistent shots every time.

## Features

### Dual Boiler Control

For dual boiler machines:
- **Independent control** - Separate PID loops for brew and steam boilers
- **Independent setpoints** - Set brew and steam temperatures separately
- **No interference** - Brewing doesn't affect steam temperature

### Single Boiler Control

For single boiler machines:
- **Single PID loop** - Controls one boiler
- **Temperature surfing** - Manual temperature management required
- **Brew/steam switching** - Switch between brew and steam modes

### Heat Exchanger Control

For HX machines:
- **Steam boiler control** - PID controls steam boiler
- **Group head monitoring** - Thermocouple monitors group head temperature
- **HX management** - Automatic HX temperature management

## PID Control

### How It Works

PID control uses three components:
- **Proportional (P)** - Responds to current error
- **Integral (I)** - Eliminates steady-state error
- **Derivative (D)** - Reduces overshoot

### Temperature Stability

- **Target stability**: ±0.1°C
- **Response time**: Fast response to setpoint changes
- **Overshoot protection**: Minimal overshoot on startup

### PID Tuning

Default PID parameters work well for most machines. Advanced users can tune:
- **P value** - Proportional gain
- **I value** - Integral gain
- **D value** - Derivative gain

**Warning:** Incorrect PID tuning can cause instability. Only modify if you understand PID control.

## Temperature Zones

### Brew Boiler

- **Typical setpoint**: 93-95°C (200-203°F)
- **Control**: PID maintains setpoint
- **Monitoring**: Real-time temperature display
- **Stability**: ±0.1°C

### Steam Boiler

- **Typical setpoint**: 140-145°C (284-293°F)
- **Control**: Independent PID loop
- **Monitoring**: Real-time temperature display
- **Auto-fill**: Automatic water level management

### Group Head

- **Monitoring**: K-type thermocouple
- **Real-time display**: Group head temperature shown
- **Shot quality**: Critical for consistent extraction
- **No control**: Group head is passive (monitored only)

## Configuration

### Setting Temperatures

1. **From Dashboard**:
   - Click temperature gauge
   - Adjust setpoint slider
   - Changes apply immediately

2. **From Settings**:
   - Go to Settings → Temperature
   - Set brew and steam temperatures
   - Save changes

### Temperature Units

- **Celsius** - Default, standard for espresso
- **Fahrenheit** - Available in settings
- **Conversion** - Automatic conversion in display

### Max Temperatures

Safety limits:
- **Brew max**: 100°C (212°F)
- **Steam max**: 165°C (329°F) - Safety shutdown
- **Over-temperature protection**: Automatic shutdown at 165°C

## Heating Strategies

### Sequential (Default)

- **Brew first** - Heat brew boiler to setpoint
- **Then steam** - Heat steam boiler after brew ready
- **Power efficient** - Lower peak power consumption
- **Faster brew ready** - Brew temperature reached first

### Parallel

- **Both simultaneously** - Heat both boilers at once
- **Faster overall** - Both ready sooner
- **Higher power** - Requires more electrical capacity
- **Circuit breaker** - May trip on some circuits

### Smart Stagger

- **Intelligent** - Power-aware staggered heating
- **Optimized** - Balances speed and power
- **Adaptive** - Adjusts based on conditions
- **Recommended** - Best balance of speed and efficiency

### Brew Only

- **Brew boiler only** - Heat only brew boiler
- **Energy saving** - Lower power consumption
- **No steam** - Steam not available
- **Use case** - When only brewing espresso

## Monitoring

### Real-Time Display

- **Dashboard gauges** - Visual temperature display
- **Color coding** - Blue (cold), green (ready), red (hot)
- **Setpoint indicator** - Shows target temperature
- **Current reading** - Real-time temperature value

### Temperature Graphs

- **Historical view** - See temperature over time
- **Shot analysis** - Temperature during shot
- **Stability check** - Verify PID performance
- **Troubleshooting** - Identify temperature issues

## Best Practices

### Temperature Selection

- **Brew temperature**: 93-95°C typical
  - Lower (90-92°C): Lighter roasts, brighter flavors
  - Higher (95-97°C): Darker roasts, more extraction
- **Steam temperature**: 140-145°C typical
  - Higher: Faster steaming, more power
  - Lower: More control, gentler steaming

### Preheating

- **Allow time** - 15-20 minutes for full heat
- **Group head** - Important for consistent shots
- **Stability** - Wait for stable temperature
- **Schedules** - Use auto-on for morning routine

### Shot Quality

- **Consistent temperature** - Key to good shots
- **Group head monitoring** - Critical for quality
- **Recovery time** - Allow time between shots
- **Temperature stability** - Monitor for drift

## Troubleshooting

### Temperature Not Reaching Setpoint

- **Check heater connections** - Verify SSR triggers
- **Check power** - Verify adequate electrical supply
- **Check PID tuning** - May need adjustment
- **Review logs** - Check for errors

### Temperature Unstable

- **Check PID parameters** - May need tuning
- **Check sensor** - Verify sensor is working
- **Check wiring** - Loose connections cause issues
- **Review diagnostics** - Check for problems

### Over-Temperature

- **Safety shutdown** - Automatic at 165°C
- **Check SSR** - May be stuck on
- **Check sensor** - Verify sensor reading
- **Review logs** - Check for errors

## Advanced Topics

### PID Tuning

For advanced users:
1. **Start with defaults** - Default values work for most machines
2. **Make small changes** - Adjust one parameter at a time
3. **Test thoroughly** - Verify stability after changes
4. **Document changes** - Keep notes on what works

### Sensor Calibration

If temperatures seem inaccurate:
1. **Verify sensor type** - Ensure correct sensor type configured
2. **Check installation** - Proper thermal contact required
3. **Compare readings** - Use known good thermometer
4. **Adjust offset** - Use temperature offset if needed

## Related Features

- [Brewing Features](Brewing-Features.md) - Shot timer and brewing
- [Statistics](Statistics.md) - Temperature history
- [Scheduling](Scheduling.md) - Auto-on for preheating

---

**Next:** [Brewing Features](Brewing-Features.md)

