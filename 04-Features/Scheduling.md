# Scheduling

BrewOS supports automated scheduling for turning your machine on and off at specific times, plus automatic power-off after idle periods.

## Overview

Scheduling features include:
- **Time-based schedules** - Turn machine on/off at specific times
- **Daily schedules** - Configure different schedules for different days
- **Auto power-off** - Automatically turn off after idle period
- **Heating strategies** - Select heating strategy for scheduled power-on

## Time-Based Schedules

### Creating a Schedule

1. **Navigate to Schedules**:
   - Go to Settings → Schedules
   - Or use Schedules page in navigation

2. **Add Schedule**:
   - Click "Add Schedule"
   - Configure schedule options
   - Save schedule

### Schedule Configuration

Each schedule includes:
- **Name** - Friendly name (e.g., "Morning Coffee")
- **Action** - Turn On or Turn Off
- **Time** - Hour and minute (24-hour format)
- **Days** - Days of week (weekdays, weekends, specific days)
- **Heating Strategy** - For Turn On actions (sequential, parallel, etc.)

### Schedule Examples

**Morning Coffee (Weekdays)**:
- Action: Turn On
- Time: 7:00 AM
- Days: Monday-Friday
- Strategy: Sequential

**Evening Shutdown**:
- Action: Turn Off
- Time: 10:00 PM
- Days: Every day
- Strategy: N/A (turn off)

**Weekend Brunch**:
- Action: Turn On
- Time: 9:30 AM
- Days: Saturday, Sunday
- Strategy: Parallel

### Managing Schedules

- **Edit** - Modify existing schedule
- **Delete** - Remove schedule
- **Enable/Disable** - Toggle schedule without deleting
- **Multiple schedules** - Up to 10 schedules supported

## Auto Power-Off

### Overview

Auto power-off automatically turns off the machine after a period of inactivity:
- **Idle detection** - Detects when machine is idle
- **Configurable timeout** - Set idle time before power-off (5-480 minutes)
- **Activity detection** - Resets timer on any activity
- **Brewing protection** - Won't power off during active brewing

### Configuration

1. **Enable auto power-off**:
   - Go to Settings → Schedules
   - Enable "Auto Power-Off"
   - Set timeout (minutes)

2. **Set timeout**:
   - Range: 5-480 minutes
   - Typical: 60-120 minutes
   - 0 = disabled

### Activity Detection

Auto power-off resets on:
- **Brewing** - Starting or stopping a shot
- **User interaction** - Button presses, encoder rotation
- **Commands** - Any command sent to machine
- **Mode changes** - Changing machine mode

### Behavior

- **Only when ON** - Only triggers when machine is ON
- **Not during brewing** - Won't power off during active shot
- **Safe shutdown** - Normal shutdown process
- **Notification** - Optional notification before power-off

## Best Practices

### Schedule Planning

1. **Morning routine**:
   - Schedule power-on 15-20 minutes before first shot
   - Allows time for preheating
   - Use sequential heating for faster brew ready

2. **Evening shutdown**:
   - Schedule power-off after last use
   - Saves energy overnight
   - Prevents leaving machine on

3. **Weekend schedules**:
   - Different times for weekends
   - Later start times typical
   - Separate schedule for weekends

### Auto Power-Off Settings

- **Timeout selection**:
  - 60 minutes: Good for home use
  - 120 minutes: If you take breaks
  - Longer: If you want more flexibility
- **Consider usage**:
  - How often you brew
  - Typical time between shots
  - Your daily routine

### Heating Strategy Selection

For scheduled power-on:
- **Sequential** - Faster brew ready, lower power
- **Parallel** - Faster overall, higher power
- **Smart Stagger** - Best balance (recommended)

## Troubleshooting

### Schedule Not Triggering

1. **Check NTP sync**:
   - Schedule requires valid time
   - Ensure WiFi is connected
   - Verify NTP has synced
   - Check time is correct

2. **Verify schedule**:
   - Check schedule is enabled
   - Verify days match current day
   - Check time is correct
   - Verify action is correct

3. **Check time**:
   - Schedules trigger at exact minute
   - Ensure system time is accurate
   - Check timezone is correct

### Auto Power-Off Not Working

1. **Check enabled**:
   - Verify auto power-off is enabled
   - Check timeout is > 0

2. **Check machine state**:
   - Only triggers when machine is ON
   - Won't trigger in STANDBY

3. **Check activity**:
   - Any activity resets timer
   - Verify no ongoing activity
   - Check for background processes

### Schedules Not Persisting

1. **Check filesystem**:
   - Verify LittleFS is mounted
   - Check for filesystem errors
   - Verify free space

2. **Check configuration**:
   - Verify settings are being saved
   - Check configuration files
   - Review serial logs

## Related Features

- [Eco Mode](Eco-Mode.md) - Energy-saving idle mode
- [Temperature Control](Temperature-Control.md) - Temperature management
- [Statistics](Statistics.md) - Track energy usage

---

**Next:** [Statistics](Statistics.md) or [Eco Mode](Eco-Mode.md)

