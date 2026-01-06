# Statistics

BrewOS automatically tracks shot history, temperature data, and machine statistics for analysis and optimization.

## Overview

Statistics features include:
- **Shot history** - Complete record of every shot
- **Temperature graphs** - Historical temperature data
- **Pressure profiles** - Shot pressure curves
- **Machine statistics** - Uptime, shot counts, energy usage

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

