# Single Boiler Setup

Configuration guide for single boiler espresso machines.

## Overview

Single boiler machines use one boiler for both brewing and steaming:

- **One boiler** - Shared between brewing and steaming
- **Temperature surfing** - Manual temperature management
- **Mode switching** - Switch between brew and steam modes
- **Simpler design** - Lower cost, simpler operation

## Machine Selection

During initial setup:

1. **Select machine type**: Single Boiler
2. **Firmware**: Use `brewos_single_boiler.uf2`
3. **Configuration**: Single boiler configuration applied

## Temperature Configuration

### Boiler Temperature

- **Brew mode**: 93-95°C (200-203°F)
- **Steam mode**: 140-145°C (284-293°F)
- **Mode switching** - Manual or automatic switching
- **Temperature surfing** - May need to wait for temperature

### Mode Management

- **Brew mode** - Lower temperature for brewing
- **Steam mode** - Higher temperature for steaming
- **Switching** - Wait for temperature change
- **Recovery** - Time to reach target temperature

## Heating Strategy

### Single Boiler

- **One heater** - Single heater for boiler
- **One PID loop** - Single temperature control
- **Mode-dependent** - Setpoint changes with mode
- **Recovery time** - Time to change between modes

## Sensor Configuration

### Required Sensors

- **Boiler NTC** - Boiler temperature sensor
- **Group thermocouple** - Group head temperature (recommended)
- **Pressure transducer** - Brew pressure (optional)
- **Tank sensor** - Water reservoir level

### Sensor Placement

- **Boiler sensor** - Side or top of boiler
- **Group thermocouple** - Group head port
- **Pressure sensor** - Group head or brew path

## Usage Patterns

### Brewing Workflow

1. **Ensure brew mode** - Verify in brew mode
2. **Check temperature** - Wait for brew temperature
3. **Pull shot** - Extract espresso
4. **Switch to steam** - Change to steam mode
5. **Wait for steam temp** - Heat to steam temperature
6. **Steam milk** - Steam milk
7. **Switch back** - Return to brew mode for next shot

### Temperature Surfing

- **Monitor temperature** - Watch temperature gauge
- **Wait for setpoint** - Allow time to reach temperature
- **Consistency** - Aim for consistent temperature
- **Practice** - Learn your machine's behavior

## Best Practices

### Temperature Management

- **Preheat** - Allow 15-20 minutes for full heat
- **Monitor** - Watch temperature during use
- **Consistency** - Aim for consistent temperatures
- **Recovery** - Allow time between mode switches

### Workflow Optimization

- **Plan ahead** - Know when you'll need steam
- **Batch steaming** - Steam all milk at once
- **Efficient switching** - Minimize mode switches
- **Practice** - Learn optimal workflow

## Troubleshooting

### Temperature Issues

- **Check sensor** - Verify sensor is working
- **Check heater** - Verify heater is working
- **Check PID** - May need PID tuning
- **Review diagnostics** - Check for errors

### Mode Switching Issues

- **Check mode** - Verify mode is switching
- **Check temperature** - Verify temperature is changing
- **Wait for recovery** - Allow time for temperature change
- **Review diagnostics** - Check for errors

### Inconsistent Shots

- **Temperature stability** - Ensure stable temperature
- **Group head** - Monitor group head temperature
- **Recovery time** - Allow time between shots
- **Practice** - Learn temperature surfing

## Related Documentation

- [Temperature Control](../04-Features/Temperature-Control.md)
- [Compatibility List](Compatibility-List.md)
- [Installation & Setup](../02-Installation-Setup/)

---

**Next:** [Heat Exchanger Setup](Heat-Exchanger-Setup.md) or [Compatibility List](Compatibility-List.md)
