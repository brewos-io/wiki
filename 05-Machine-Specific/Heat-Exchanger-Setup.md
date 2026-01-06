# Heat Exchanger Setup

Configuration guide for heat exchanger (HX) espresso machines.

## Overview

Heat exchanger machines use a steam boiler with a heat exchanger for brew water:
- **Steam boiler** - Main boiler for steaming
- **Heat exchanger** - Heats brew water via steam boiler
- **Simultaneous operation** - Can brew and steam simultaneously
- **Group head** - E61 group head with thermosyphon

## Machine Selection

During initial setup:
1. **Select machine type**: Heat Exchanger
2. **Firmware**: Use `brewos_heat_exchanger.uf2`
3. **Configuration**: HX configuration applied

## Temperature Configuration

### Steam Boiler

- **Typical setpoint**: 140-145°C (284-293°F)
- **PID control** - Precise steam boiler control
- **Auto-fill** - Automatic water level management
- **Steam ready** - Always ready for steaming

### Group Head Temperature

- **Monitoring** - Group head temperature monitored
- **Thermosyphon** - Natural circulation from HX
- **Stability** - Temperature stability important
- **No direct control** - Group head is passive

### HX Management

- **Automatic** - HX temperature managed automatically
- **Flush management** - May need cooling flushes
- **Temperature stability** - Monitor for consistency

## Heating Strategy

### Recommended: Sequential

- **Steam first** - Heat steam boiler to setpoint
- **HX ready** - HX ready when steam ready
- **Faster steam** - Steam ready first
- **Lower power** - Lower peak power consumption

### Alternative: Parallel

- **Faster overall** - Both ready sooner
- **Higher power** - Requires more electrical capacity

## Sensor Configuration

### Required Sensors

- **Steam NTC** - Steam boiler temperature sensor
- **Group thermocouple** - Group head temperature (critical)
- **Pressure transducer** - Brew pressure (optional but recommended)
- **Steam level probe** - Steam boiler water level
- **Tank sensor** - Water reservoir level

### Sensor Placement

- **Steam sensor** - Side or top of steam boiler
- **Group thermocouple** - Group head port (critical)
- **Pressure sensor** - Group head or brew path
- **Level probe** - Steam boiler interior

## HX-Specific Considerations

### Cooling Flushes

HX machines may need cooling flushes:
- **Purpose** - Cool group head if too hot
- **Timing** - Before first shot, after idle
- **Monitoring** - Watch group head temperature
- **Practice** - Learn your machine's needs

### Temperature Stability

- **Monitor group head** - Critical for shot quality
- **Thermosyphon** - Natural circulation maintains temperature
- **Flush management** - May need periodic flushes
- **Consistency** - Aim for stable group head temperature

## Best Practices

### Temperature Settings

- **Steam**: 140-145°C typical
  - Higher for faster steaming
  - Lower for more control
- **Group head**: Monitor closely
  - Should be stable around 93-95°C
  - May need cooling flushes

### Preheating

- **Allow time** - 20-30 minutes for full heat
- **Group head** - Critical for consistent shots
- **Thermosyphon** - Needs time to stabilize
- **Use schedules** - Auto-on for morning routine

### Usage

- **Monitor group head** - Watch temperature closely
- **Cooling flushes** - Use when needed
- **Consistency** - Aim for stable temperatures
- **Practice** - Learn your machine's behavior

## Troubleshooting

### Group Head Too Hot

- **Cooling flush** - Perform cooling flush
- **Monitor temperature** - Watch group head temp
- **Adjust steam temp** - Lower steam setpoint
- **Flush timing** - Learn optimal flush timing

### Group Head Too Cold

- **Wait longer** - Allow more preheat time
- **Check thermosyphon** - Verify circulation
- **Check steam temp** - Verify steam boiler temp
- **Review diagnostics** - Check for issues

### Inconsistent Shots

- **Temperature stability** - Ensure stable group head temp
- **Flush management** - Consistent flush routine
- **Monitor closely** - Watch temperature during use
- **Practice** - Learn optimal workflow

## Related Documentation

- [Temperature Control](../04-Features/Temperature-Control.md)
- [Compatibility List](Compatibility-List.md)
- [Installation & Setup](../02-Installation-Setup/)

---

**Next:** [Compatibility List](Compatibility-List.md) or [Troubleshooting](../06-Troubleshooting/)

