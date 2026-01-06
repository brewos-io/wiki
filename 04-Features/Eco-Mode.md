# Eco Mode

Eco Mode is an energy-saving feature that automatically reduces the brew boiler temperature when the machine is idle, significantly reducing power consumption while keeping the machine in a semi-ready state.

## Overview

Eco Mode provides:

- **Automatic activation** - Enters eco mode after idle period
- **Reduced temperature** - Lowers brew boiler to eco temperature
- **Quick recovery** - Fast return to brewing temperature
- **Energy savings** - Significant power reduction

## How It Works

### Understanding Temperature and Energy

To understand eco mode, it's important to know how espresso machines consume energy:

**Heat Loss Physics:**
- Heat loss is proportional to the temperature difference between the boiler and ambient air
- The larger the temperature difference, the more energy is required to maintain it
- At 95°C, the machine loses heat rapidly to a 20°C room (75°C difference)
- At 80°C, the temperature difference is only 60°C, reducing heat loss by approximately 20%
- Heat loss also occurs through conduction (metal parts) and convection (air movement)

**Power Consumption:**
- When at setpoint, the heater cycles on/off to maintain temperature
- Higher setpoint = more frequent heating cycles = more energy
- Lower setpoint = fewer heating cycles = less energy
- The PID controller adjusts heater duty cycle based on temperature difference

### Automatic Activation

1. **Idle detection** - Machine detects when idle (not brewing, no activity)
   - No brewing activity for the timeout period
   - No user interactions (button presses, encoder rotation, web interface commands)
   - Machine must be in READY state (at temperature)
   
2. **Timeout** - After configured timeout (default: 30 minutes)
   - Timer starts when machine reaches READY state
   - Any activity resets the timer
   - Timer only counts when machine is idle and ready
   
3. **Enter eco** - Brew boiler temperature lowered to eco setpoint
   - PID controller changes target from normal setpoint to eco setpoint
   - Heater reduces power or turns off (depending on current temperature)
   - Temperature gradually decreases to eco setpoint
   - Steam boiler remains at full temperature (unchanged)
   
4. **Steam unchanged** - Steam boiler temperature unchanged
   - Steam boiler stays at 145°C to maintain steam capability
   - This allows immediate steaming even in eco mode
   - Only brew boiler temperature is reduced

### Temperature Management

| Mode           | Brew Temp | Steam Temp         | Power Consumption | Recovery Time |
| -------------- | --------- | ------------------ | ----------------- | ------------- |
| Normal (READY) | ~93-95°C  | ~145°C             | ~150W average     | N/A (ready)   |
| Eco Mode       | ~80°C     | ~145°C (unchanged) | ~50W average      | 2-5 minutes   |

**Why 80°C Works Well:**
- The lower eco temperature (~80°C) significantly reduces heat loss and power consumption
- 80°C is warm enough that recovery is quick (2-5 minutes typical)
- Too low (e.g., 60°C) would save more energy but take 10+ minutes to recover
- Too high (e.g., 90°C) would recover faster but save less energy
- 80°C represents an optimal balance between energy savings and recovery time

**Temperature Saving Strategy:**
- **Immediate savings**: As soon as eco mode activates, heater duty cycle drops
- **Gradual cooling**: Temperature doesn't drop instantly - it cools naturally over several minutes
- **Maintained temperature**: Once at 80°C, the PID maintains it with minimal heating
- **Heat retention**: The machine's thermal mass helps maintain temperature

### State Flow

```
READY → [idle timeout] → ECO → [user activity] → HEATING → READY
```

### Wake on Activity

Eco mode exits automatically on:

- **User interaction** - Button press, encoder rotation
- **Mode change** - Changing machine mode
- **Brewing start** - Starting a shot
- **Any command** - Any user command

## Configuration

### Settings

Configure eco mode in Settings → Eco Mode:

- **Enabled** - Enable/disable auto-eco timeout
- **Eco Brew Temp** - Target temperature in eco mode (50-90°C, default: 80°C)
- **Auto-Eco After** - Minutes of idle before entering eco (0-480, default: 30)
  - 0 = disabled (no auto-eco)

### Recommended Settings

- **Eco temperature**: 80°C - Good balance of savings and recovery
- **Timeout**: 30 minutes - Good for typical home use
- **Adjust for usage**: If you brew every hour, increase timeout

## Power Savings

### Understanding Energy Consumption

**Normal Mode Power Consumption:**
- When at 95°C setpoint, the machine cycles the heater on/off to maintain temperature
- Average power consumption: ~150W (varies by machine, ambient temperature, insulation)
- Heater typically runs 30-50% of the time (duty cycle)
- Higher ambient temperature = less heating needed = lower power
- Better insulation = less heat loss = lower power

**Eco Mode Power Consumption:**
- At 80°C setpoint, much less heating is required
- Average power consumption: ~50W (approximately 67% reduction)
- Heater runs much less frequently (10-20% duty cycle)
- The lower temperature difference means less heat loss

**Estimated Savings:**

| Scenario               | Normal    | Eco Mode | Savings    | Annual Savings |
| ---------------------- | --------- | -------- | ---------- | -------------- |
| Idle power (brew only) | ~150W avg | ~50W avg | ~67%       | -              |
| Daily cost (8hr idle)  | ~$0.30    | ~$0.10   | ~$0.20/day | ~$73/year     |
| Monthly cost (8hr/day) | ~$9.00    | ~$3.00   | ~$6.00     | -              |

_Values are approximate and depend on:_
- **Ambient temperature**: Colder rooms require more heating
- **Machine insulation**: Better insulation = less heat loss
- **Local electricity rates**: Varies by region ($0.10-$0.30/kWh typical)
- **Machine type**: Dual boiler vs single boiler affects consumption
- **Usage patterns**: How often you brew affects idle time

**Real-World Example:**
- If you leave your machine on 12 hours per day
- With 30-minute eco timeout, machine enters eco after morning routine
- Saves energy during afternoon/evening idle periods
- Typical savings: $50-100 per year depending on usage and rates

**Calculating Your Savings:**
1. Check your electricity rate (on your bill, typically $/kWh)
2. Estimate daily idle hours (time machine is on but not brewing)
3. Calculate: `(idle_hours × 0.1kW × rate × 365) × 0.67 = annual_savings`
4. Example: 8 hours/day × $0.15/kWh = ~$73/year savings

## Manual Control

### Enter Eco Mode Manually

You can manually enter eco mode:

- **From web interface** - Use eco mode button
- **Via command** - Send eco command
- **From settings** - Enable eco mode manually

### Exit Eco Mode

Eco mode exits automatically on activity, or manually:

- **Wake button** - Click wake button in interface
- **Any activity** - Any user interaction
- **Mode change** - Changing to ready mode

## Recovery Time

### Typical Recovery

Recovery from eco mode to brewing temperature:

- **Time**: 2-5 minutes typical
- **Depends on**:
  - Temperature difference (normal - eco)
  - Heater power
  - Ambient temperature
  - Machine insulation

### Optimizing Recovery

- **Pre-wake** - Wake machine 5-10 minutes before brewing
- **Schedules** - Use schedules to wake before morning routine
- **Monitor** - Watch temperature during recovery
- **Adjust timeout** - Longer timeout = more savings, longer recovery

## Best Practices

### Timeout Selection

- **30 minutes** - Good balance for most users
- **60+ minutes** - If you brew every hour
- **Shorter** - If you want faster recovery
- **Consider usage** - Match timeout to your routine

### Temperature Selection

- **80°C** - Recommended, good balance
- **Lower** - More savings, longer recovery
- **Higher** - Faster recovery, less savings
- **Experiment** - Find what works for you

### Usage Patterns

- **Morning routine** - Use schedules to wake before first shot
- **Evening** - Let eco mode activate naturally
- **Frequent use** - Increase timeout or disable
- **Infrequent use** - Lower timeout for more savings

## Troubleshooting

### Eco Mode Not Activating

1. **Check enabled**:

   - Verify eco mode is enabled in settings
   - Check timeout is not 0 (disabled)

2. **Check machine state**:

   - Must be in READY state (not IDLE or HEATING)
   - Won't activate during brewing

3. **Check activity**:
   - Any activity resets idle timer
   - Verify no background processes

### Slow Recovery

1. **Check temperature difference**:

   - Larger difference = longer recovery
   - Consider higher eco temperature

2. **Check heater**:

   - Verify heater is working
   - Check power supply
   - Review diagnostics

3. **Normal behavior**:
   - 2-5 minutes is typical
   - Allow time for recovery

### Settings Not Persisting

1. **Check flash**:

   - Eco config saved to flash
   - Flash write requires ~100ms
   - Don't power off immediately after changing

2. **Verify save**:
   - Check settings are saved
   - Review configuration
   - Try saving again

## Related Features

- [Scheduling](Scheduling.md) - Auto-on/off schedules
- [Temperature Control](Temperature-Control.md) - Temperature management
- [Power Metering](Power-Metering.md) - Monitor energy savings

---

**Next:** [Statistics](Statistics.md) or [WiFi Connectivity](WiFi-Connectivity.md)
