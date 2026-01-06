# Brewing Features

BrewOS provides comprehensive brewing features including shot timer, pre-infusion, and brew-by-weight support.

## Shot Timer

### Automatic Timer

The shot timer starts automatically when brewing begins:
- **Elapsed time** - Shows how long shot has been running
- **Target time** - Your target shot time (if configured)
- **Visual indicator** - Progress bar showing shot progress
- **Auto-start** - Starts when pump activates

### Using the Shot Timer

1. **Start brewing** - Timer starts automatically
2. **Monitor time** - Watch elapsed time during shot
3. **Stop shot** - Timer stops when brewing ends
4. **Review time** - Shot time saved to statistics

### Target Time

Set a target shot time:
- **Default**: 25-30 seconds typical
- **Configurable**: Set in brewing settings
- **Visual indicator**: Shows progress toward target
- **Alert**: Optional alert when target reached

## Pre-Infusion

### What is Pre-Infusion?

Pre-infusion is a low-pressure phase before full extraction:
- **Low pressure** - Typically 2-3 bar
- **Wetting phase** - Saturates coffee grounds
- **Better extraction** - More even extraction
- **Reduced channeling** - Prevents channeling

### Pre-Infusion Support

BrewOS supports pre-infusion through:
- **Configurable timing** - Set pre-infusion duration
- **Pressure control** - Low pressure during pre-infusion
- **Automatic transition** - Switches to full pressure automatically

### Configuration

Configure pre-infusion in settings:
- **Enable/disable** - Turn pre-infusion on/off
- **Duration** - Set pre-infusion time (seconds)
- **Pressure** - Set pre-infusion pressure (if adjustable)

## Brew by Weight

### Overview

Brew-by-weight uses a connected scale to stop brewing at a target weight:
- **Precision** - More consistent than time-based
- **Automatic stop** - Stops at target weight
- **Scale integration** - Works with Bluetooth scales
- **Weight tracking** - Real-time weight display

### Supported Scales

BrewOS supports multiple Bluetooth scale brands:
- **Acaia** - Lunar, Pearl, Pyxis, Cinco, Orion
- **Bookoo** - Themis Mini, Themis Ultra
- **Felicita** - Arc, Parallel, Incline
- **Decent** - Decent Scale
- **Timemore** - Black Mirror 2
- **Hiroia** - Jimmy
- **Generic** - Bluetooth SIG Weight Scale Service

### Setup

1. **Enable scale**:
   - Go to Settings → Scale
   - Enable scale integration
   - Select scale type

2. **Pair scale**:
   - Put scale in pairing mode
   - ESP32 will discover and connect
   - Verify connection status

3. **Configure brew-by-weight**:
   - Set target weight (default: 36g)
   - Set tolerance (weight variation allowed)
   - Enable auto-stop

### Using Brew by Weight

1. **Prepare shot**:
   - Place scale under cup
   - Tare scale (zero weight)
   - Lock portafilter

2. **Start brewing**:
   - Click "Start Shot"
   - Weight updates in real-time
   - Shot stops automatically at target

3. **Monitor weight**:
   - Real-time weight display
   - Progress toward target
   - Flow rate calculation

### Weight Settings

- **Target weight** - Default target (typically 36g for double shot)
- **Tolerance** - Weight variation allowed (±1g typical)
- **Auto-stop** - Automatically stop at target
- **Tare function** - Zero scale before shot

## Pressure Monitoring

### Real-Time Pressure

During brewing:
- **Pressure display** - Real-time pressure reading
- **Pressure graph** - Visual pressure profile
- **Peak pressure** - Maximum pressure reached
- **Target pressure** - 8-9 bar typical

### Pressure Profile

The pressure graph shows:
- **Pressure curve** - Pressure over time
- **Peak pressure** - Maximum during shot
- **Average pressure** - Average extraction pressure
- **Pressure stability** - Consistency of pressure

## Shot Statistics

Each shot is automatically recorded:
- **Shot time** - Duration of shot
- **Temperature** - Temperature at shot start
- **Pressure** - Peak and average pressure
- **Weight** - Final shot weight (if scale connected)
- **Date/time** - When shot was pulled

See [Statistics](Statistics.md) for detailed shot history.

## Best Practices

### Shot Timing

- **Target time**: 25-30 seconds typical
- **Monitor time** - Watch timer during shot
- **Adjust grind** - Faster = finer, slower = coarser
- **Consistency** - Aim for consistent shot times

### Pre-Infusion

- **Duration**: 5-10 seconds typical
- **Pressure**: 2-3 bar
- **Experiment** - Find what works for your coffee
- **Monitor** - Watch pressure during pre-infusion

### Brew by Weight

- **Target weight**: 36g for double shot typical
- **Tare scale** - Always tare before shot
- **Consistent dose** - Use same coffee dose
- **Monitor flow** - Watch weight increase rate

### Pressure

- **Target**: 8-9 bar during extraction
- **Monitor** - Watch pressure graph
- **Adjust** - Grind affects pressure
- **Stability** - Pressure should be stable

## Troubleshooting

### Shot Timer Not Starting

- **Check pump** - Verify pump is activating
- **Check sensor** - Verify flow/pressure sensor
- **Review logs** - Check for errors
- **Manual start** - Try manual timer start

### Scale Not Connecting

- **Check Bluetooth** - Verify scale is in pairing mode
- **Check distance** - Scale should be close to ESP32
- **Check battery** - Low battery can cause issues
- **Try re-pairing** - Disconnect and reconnect

### Brew by Weight Not Stopping

- **Check target weight** - Verify target is set
- **Check tolerance** - Tolerance may be too large
- **Check scale reading** - Verify weight is updating
- **Check auto-stop** - Ensure auto-stop is enabled

### Pressure Not Reading

- **Check sensor** - Verify pressure sensor is installed
- **Check wiring** - Verify sensor connections
- **Check calibration** - Sensor may need calibration
- **Review diagnostics** - Check for sensor errors

## Related Features

- [Statistics](Statistics.md) - Shot history and analytics
- [Temperature Control](Temperature-Control.md) - Temperature management
- [Power Metering](Power-Metering.md) - Energy monitoring

---

**Next:** [Scheduling](Scheduling.md) or [Statistics](Statistics.md)

