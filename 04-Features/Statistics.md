# Statistics

BrewOS automatically tracks shot history, temperature data, and machine statistics for analysis and optimization. This comprehensive data collection helps you understand your machine's performance, identify trends, and improve your espresso quality over time.

## Overview

Statistics features provide comprehensive data collection and analysis:

- **Shot history** - Complete record of every shot with all parameters
- **Temperature graphs** - Historical temperature data over time
- **Pressure profiles** - Shot pressure curves for analysis
- **Machine statistics** - Uptime, shot counts, energy usage
- **Trend analysis** - Identify patterns and changes over time
- **Performance metrics** - Track consistency and quality

## How Statistics Work

### Data Collection

**Automatic Recording:**
- Every shot is automatically recorded when brewing completes
- No manual intervention required
- Data collected includes all available sensors and parameters
- Stored in non-volatile memory (survives power loss)

**What Gets Recorded:**
- **Shot Parameters**: Duration, temperature, pressure, weight
- **Timing**: Date, time, shot number
- **Machine State**: State at shot start, heating strategy used
- **Sensor Data**: All available sensor readings during shot
- **Calculated Metrics**: Flow rate, average pressure, peak pressure

**Data Storage:**
- Stored in ESP32 flash memory (LittleFS filesystem)
- Limited by available flash space (typically 1000+ shots)
- Older shots may be automatically purged when space is full
- Data can be exported for long-term storage

### Shot History

**Complete Shot Records:**

Each shot includes comprehensive data:

- **Date and Time**: When shot was pulled (timestamp)
- **Duration**: Shot time in seconds (from start to stop)
- **Temperature**: Brew temperature at shot start (critical for extraction)
- **Peak Pressure**: Maximum pressure during shot (typically 8-9 bar)
- **Average Pressure**: Average extraction pressure (consistency indicator)
- **Weight**: Final shot weight in grams (if scale connected)
- **Flow Rate**: Average flow rate (if calculable from weight/time)
- **Group Head Temp**: Group head temperature at shot start
- **Shot Number**: Sequential shot number (for tracking)

**Viewing Shot History:**

1. **Navigate to Statistics**:
   - Click "Statistics" in navigation menu
   - View list of recent shots (most recent first)
   - Scroll to see older shots

2. **Shot Details**:
   - Click any shot to view detailed information
   - See temperature and pressure graphs for that shot
   - Review all shot parameters
   - Compare with other shots

**Shot Analysis:**

- **Compare Shots**: See how shots differ in parameters
- **Identify Trends**: Track changes over time (temperature drift, pressure changes)
- **Optimize Settings**: Use data to improve shot quality
- **Track Quality**: Monitor consistency (are shots getting better or worse?)
- **Troubleshoot Issues**: Identify problems (temperature drops, pressure issues)

### Temperature Graphs

**Historical Temperature Data:**

View temperature over extended time periods:

- **Brew Temperature**: Historical brew boiler temperature
  - See temperature stability over time
  - Identify temperature drift or PID issues
  - Track temperature during different times of day
  - Compare temperature with ambient conditions

- **Steam Temperature**: Historical steam boiler temperature
  - Monitor steam boiler performance
  - Identify heating issues
  - Track steam temperature stability

- **Group Head Temperature**: Group head temperature history
  - Most important temperature for shot quality
  - See thermal stability and recovery
  - Identify preheating effectiveness
  - Track group head temperature during shots

**Time Range Selection:**
- **Last Hour**: Recent temperature behavior
- **Last Day**: Daily temperature patterns
- **Last Week**: Weekly trends and patterns
- **Custom Range**: Select specific time period

**Shot Temperature Analysis:**

Temperature during specific shot:

- **Shot Start Temperature**: Temperature when shot began (critical)
- **Temperature Stability**: How stable temperature was during shot
- **Temperature Recovery**: How quickly temperature recovered after shot
- **Thermal Management**: See if machine handled thermal load properly

### Pressure Profiles

**Shot Pressure Curves:**

Visual representation of pressure during extraction:

- **Pressure Graph**: Visual pressure profile over time
- **Peak Pressure**: Maximum pressure reached during shot
- **Average Pressure**: Average pressure during extraction
- **Pressure Stability**: Consistency of pressure (should be steady)
- **Pressure Ramp**: How pressure builds at shot start

**Analysis:**

- **Optimal Pressure**: 8-9 bar typical for espresso
- **Pressure Ramp**: Should build smoothly, not spike
- **Stability**: Pressure should be consistent during extraction
- **Issues**: Identify pressure problems (too high, too low, unstable)
- **Grind Impact**: See how grind affects pressure profile

**What Good Pressure Looks Like:**
- Smooth ramp-up to 8-9 bar
- Stable during extraction (minimal variation)
- Gradual decline at end (if pre-infusion or flow control)
- No spikes or drops

### Machine Statistics

**Summary Statistics:**

- **Total Shots**: Lifetime shot count (since last reset)
- **Shots Today**: Shots pulled today (resets at midnight)
- **Uptime**: Total machine uptime (how long machine has been on)
- **Energy Usage**: Daily and total kWh (if power meter installed)
- **Average Shot Time**: Average duration of shots
- **Average Temperature**: Average brew temperature

**Maintenance Statistics:**

- **Shots Since Cleaning**: Counter for maintenance reminders
- **Cleaning Reminders**: Automatic reminders based on shot count
- **Last Cleaning**: When machine was last cleaned (manual entry)
- **Maintenance Schedule**: Recommended cleaning intervals
- **Maintenance Alerts**: Warnings when cleaning is due

**Energy Statistics (if power meter installed):**

- **Daily Energy**: kWh consumed today
- **Total Energy**: Lifetime energy consumption
- **Average Power**: Average power consumption
- **Peak Power**: Maximum power draw
- **Cost Tracking**: Estimated energy costs

## Shot History

### Shot Records

Each shot is automatically recorded with:
- **Date and time** - When shot was pulled
- **Duration** - Shot time in seconds
- **Temperature** - Brew temperature at shot start
- **Peak pressure** - Maximum pressure during shot
- **Average pressure** - Average extraction pressure
- **Weight** - Final shot weight (if scale connected)
- **Flow rate** - Average flow rate (if available)

### Viewing Shot History

1. **Navigate to Statistics**:
   - Click "Statistics" in navigation
   - View list of recent shots

2. **Shot Details**:
   - Click any shot to view details
   - See temperature and pressure graphs
   - Review shot parameters

### Shot Analysis

- **Compare shots** - See how shots differ
- **Identify trends** - Track changes over time
- **Optimize** - Use data to improve shots
- **Track quality** - Monitor consistency

## Temperature Graphs

### Historical Temperature

View temperature over time:
- **Brew temperature** - Historical brew boiler temp
- **Steam temperature** - Historical steam boiler temp
- **Group head** - Group head temperature history
- **Time range** - Select time period to view

### Shot Temperature

Temperature during specific shot:
- **Shot start temp** - Temperature when shot started
- **Temperature stability** - How stable during shot
- **Recovery** - Temperature recovery after shot

## Pressure Profiles

### Shot Pressure Curves

View pressure during shot:
- **Pressure graph** - Visual pressure profile
- **Peak pressure** - Maximum pressure reached
- **Average pressure** - Average during extraction
- **Pressure stability** - Consistency of pressure

### Analysis

- **Optimal pressure** - 8-9 bar typical
- **Pressure ramp** - How pressure builds
- **Stability** - Pressure consistency
- **Issues** - Identify pressure problems

## Machine Statistics

### Summary Statistics

- **Total shots** - Lifetime shot count
- **Shots today** - Shots pulled today
- **Uptime** - Total machine uptime
- **Energy usage** - Daily and total kWh (if power meter installed)

### Maintenance Statistics

- **Shots since cleaning** - Counter for maintenance
- **Cleaning reminders** - Automatic reminders
- **Last cleaning** - When last cleaned
- **Maintenance schedule** - Recommended intervals

## Data Export

### Export Options

(If available)
- **CSV export** - Export shot data
- **JSON export** - Machine-readable format
- **Graph export** - Save temperature/pressure graphs
- **Backup** - Backup statistics data

## Best Practices

### Using Statistics

1. **Review regularly** - Check statistics weekly
2. **Track trends** - Look for patterns
3. **Optimize** - Use data to improve shots
4. **Compare** - Compare different settings

### Shot Quality

- **Consistent times** - Aim for consistent shot times
- **Stable temperature** - Monitor temperature stability
- **Optimal pressure** - Track pressure profiles
- **Weight consistency** - Monitor shot weights

### Maintenance

- **Cleaning schedule** - Use shot counter for cleaning
- **Track usage** - Monitor daily shot count
- **Energy monitoring** - Track power consumption
- **Identify issues** - Use data to find problems

## Troubleshooting

### Statistics Not Recording

- **Check logging** - Verify statistics are enabled
- **Check storage** - Verify filesystem space
- **Review logs** - Check for errors
- **Reset if needed** - May need to reset statistics

### Missing Data

- **Check sensors** - Verify sensors are working
- **Check connections** - Verify all connections
- **Review diagnostics** - Check for errors
- **Data may be limited** - Some data requires sensors

### Graphs Not Displaying

- **Check browser** - Try different browser
- **Clear cache** - Clear browser cache
- **Check data** - Verify data exists
- **Try refresh** - Refresh page

## Related Features

- [Brewing Features](Brewing-Features.md) - Shot timer and brewing
- [Temperature Control](Temperature-Control.md) - Temperature data
- [Power Metering](Power-Metering.md) - Energy statistics

---

**Next:** [WiFi Connectivity](WiFi-Connectivity.md) or [Cloud Access](Cloud-Access.md)

