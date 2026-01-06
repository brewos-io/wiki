# Dual Boiler Setup

Configuration guide for dual boiler espresso machines.

## Overview

Dual boiler machines have separate boilers for brewing and steaming:
- **Brew boiler** - Dedicated boiler for espresso extraction
- **Steam boiler** - Dedicated boiler for steaming milk
- **Independent control** - Each boiler controlled independently
- **Simultaneous operation** - Brew and steam simultaneously

## Machine Selection

During initial setup:
1. **Select machine type**: Dual Boiler
2. **Firmware**: Use `brewos_dual_boiler.uf2`
3. **Configuration**: Dual boiler configuration applied

## Temperature Configuration

### Brew Boiler

- **Typical setpoint**: 93-95°C (200-203°F)
- **Independent control** - Separate PID loop
- **Stability** - ±0.1°C typical
- **No interference** - Brewing doesn't affect steam

### Steam Boiler

- **Typical setpoint**: 140-145°C (284-293°F)
- **Independent control** - Separate PID loop
- **Auto-fill** - Automatic water level management
- **Steam ready** - Always ready for steaming

## Heating Strategies

### Recommended: Sequential

- **Brew first** - Heat brew boiler to setpoint
- **Then steam** - Heat steam boiler after brew ready
- **Faster brew ready** - Brew temperature reached first
- **Lower power** - Lower peak power consumption

### Alternative: Parallel

- **Both simultaneously** - Heat both boilers at once
- **Faster overall** - Both ready sooner
- **Higher power** - Requires more electrical capacity

### Alternative: Smart Stagger

- **Intelligent** - Power-aware staggered heating
- **Optimized** - Best balance of speed and efficiency
- **Recommended** - Best overall choice

## Sensor Configuration

### Required Sensors

- **Brew NTC** - Brew boiler temperature sensor
- **Steam NTC** - Steam boiler temperature sensor
- **Group thermocouple** - Group head temperature (recommended)
- **Pressure transducer** - Brew pressure (optional but recommended)
- **Steam level probe** - Steam boiler water level
- **Tank sensor** - Water reservoir level

### Sensor Placement

- **Brew sensor** - Side or top of brew boiler
- **Steam sensor** - Side or top of steam boiler
- **Group thermocouple** - Group head port
- **Pressure sensor** - Group head or brew path
- **Level probe** - Steam boiler interior

## Wiring Considerations

### Boiler Connections

- **Brew heater** - SSR trigger for brew boiler heater
- **Steam heater** - SSR trigger for steam boiler heater
- **Independent control** - Each boiler controlled separately

### Water Management

- **Steam auto-fill** - Automatic steam boiler filling
- **Level probe** - Monitors steam boiler water level
- **Fill solenoid** - Controls water flow to steam boiler
- **Brew priority** - Won't fill during brewing

## Best Practices

### Temperature Settings

- **Brew**: 93-95°C typical
  - Lower for lighter roasts
  - Higher for darker roasts
- **Steam**: 140-145°C typical
  - Higher for faster steaming
  - Lower for more control

### Preheating

- **Allow time** - 15-20 minutes for full heat
- **Group head** - Important for consistent shots
- **Use schedules** - Auto-on for morning routine

### Usage

- **Simultaneous** - Can brew and steam simultaneously
- **No interference** - Brewing doesn't affect steam
- **Consistent** - More consistent than single boiler

## Troubleshooting

### Brew Temperature Issues

- **Check sensor** - Verify brew sensor is working
- **Check SSR** - Verify brew heater SSR is working
- **Check PID** - May need PID tuning
- **Review diagnostics** - Check for errors

### Steam Temperature Issues

- **Check sensor** - Verify steam sensor is working
- **Check SSR** - Verify steam heater SSR is working
- **Check auto-fill** - Verify steam boiler is filling
- **Review diagnostics** - Check for errors

### Water Level Issues

- **Check level probe** - Verify probe is working
- **Check fill solenoid** - Verify solenoid is working
- **Check brew priority** - Won't fill during brewing
- **Review diagnostics** - Check for errors

## Related Documentation

- [Temperature Control](../04-Features/Temperature-Control.md)
- [Compatibility List](Compatibility-List.md)
- [Installation & Setup](../02-Installation-Setup/)

---

**Next:** [Compatibility List](Compatibility-List.md) or [Troubleshooting](../06-Troubleshooting/)

