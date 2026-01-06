# Scheduling

BrewOS supports automated scheduling for turning your machine on and off at specific times, plus automatic power-off after idle periods. Scheduling helps you automate your daily routine, save energy, and ensure your machine is ready when you need it.

## Overview

Scheduling features provide comprehensive automation:

- **Time-based schedules** - Turn machine on/off at specific times (cron-like scheduling)
- **Daily schedules** - Configure different schedules for different days of the week
- **Auto power-off** - Automatically turn off after idle period (energy saving)
- **Heating strategies** - Select heating strategy for scheduled power-on
- **Multiple schedules** - Create multiple schedules for different times and days
- **Enable/disable** - Toggle schedules without deleting them

## How Scheduling Works

### Time Synchronization

**NTP (Network Time Protocol):**

- Machine synchronizes time with internet time servers
- Ensures accurate time for schedule execution
- Requires internet connection (WiFi connected)
- Updates automatically (no manual configuration)
- Timezone configured in system settings

**Schedule Execution:**

- Schedules are checked every minute
- When current time matches schedule time, action is executed
- Executes at exact minute (e.g., 7:00:00 AM)
- Only executes if schedule is enabled
- Only executes on configured days

**Reliability:**

- Schedules stored in non-volatile memory (survives power loss)
- Time maintained by ESP32 real-time clock
- NTP sync ensures accuracy even after power outages
- Multiple schedules can run simultaneously

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

Auto power-off is an energy-saving feature that automatically turns off your machine after a period of inactivity. This prevents leaving the machine on unnecessarily and saves significant energy over time.

**How Auto Power-Off Works:**

- **Idle Timer**: Starts counting when machine is idle (no activity)
- **Activity Detection**: Any activity resets the timer to zero
- **Timeout**: After timeout period with no activity, machine turns off
- **Safe Shutdown**: Normal shutdown process (not abrupt power cut)
- **Protection**: Won't power off during active brewing or critical operations

**Energy Savings:**

- Machine left on 12 hours/day can cost $300-600/year
- Auto power-off can reduce this significantly
- Typical savings: $100-200/year depending on usage
- Works in combination with eco mode for maximum savings

### Idle Detection

**What Counts as Activity:**

- **Brewing**: Starting or stopping a shot resets timer
- **User Interaction**: Button presses, encoder rotation, web interface commands
- **Commands**: Any command sent via web interface, MQTT, or API
- **Mode Changes**: Changing machine mode (standby, ready, eco)
- **Temperature Adjustments**: Changing temperature setpoints
- **Settings Changes**: Modifying machine settings

**What Doesn't Count as Activity:**

- **Temperature Maintenance**: PID maintaining setpoint (normal operation)
- **Background Processes**: System maintenance tasks
- **Status Updates**: WebSocket status updates (passive)
- **Monitoring**: Viewing dashboard or statistics (read-only)

**Idle State:**

- Machine is ON and at temperature (READY state)
- No brewing activity
- No user interactions
- No commands being sent
- Machine is simply maintaining temperature

### Configuration

1. **Enable auto power-off**:

   - Go to Settings → Schedules
   - Enable "Auto Power-Off" toggle
   - Set timeout value (minutes)

2. **Set timeout**:
   - **Range**: 5-480 minutes (8 hours maximum)
   - **Typical Values**:
     - 60 minutes: Good for home use, prevents leaving on during breaks
     - 120 minutes: If you take longer breaks between shots
     - 180+ minutes: If you want more flexibility
   - **0 = Disabled**: Set to 0 to disable auto power-off
   - **Recommendation**: Start with 60-120 minutes, adjust based on usage

**Timeout Selection Guide:**

- **Short (30-60 min)**: Energy conscious, frequent use, small breaks
- **Medium (60-120 min)**: Balanced, typical home use
- **Long (120-240 min)**: Less frequent use, longer breaks, more flexibility
- **Very Long (240-480 min)**: Infrequent use, maximum flexibility

### Behavior

**When Auto Power-Off Triggers:**

- **Machine State**: Only when machine is ON (not in STANDBY)
- **Idle Period**: After timeout period with no activity
- **Safe Conditions**: Won't trigger during brewing, heating, or critical operations
- **Normal Shutdown**: Uses normal shutdown process (not abrupt)

**Protection Mechanisms:**

- **Brewing Protection**: Won't power off during active shot
- **Heating Protection**: Won't power off while heating to setpoint
- **Error Protection**: Won't power off during error conditions
- **Manual Override**: Can be disabled or timeout extended anytime

**Shutdown Process:**

- Normal shutdown sequence (same as manual power-off)
- Heaters turn off
- Machine enters STANDBY state
- All systems shut down safely
- No damage to machine or components

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
