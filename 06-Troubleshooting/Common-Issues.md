# Common Issues

Frequently encountered problems and their solutions.

## Communication Issues

### Pico Shows "Disconnected"

**Symptoms:**
- Pico status shows "Disconnected" in web interface
- No sensor readings displayed
- Machine functions not working

**Solutions:**
1. **Check UART wiring**:
   - Verify TX↔RX crossover (ESP32 TX → Pico RX, ESP32 RX ← Pico TX)
   - Check GND connection (common ground required)
   - Verify connections are secure

2. **Check baud rate**:
   - Verify baud rate is 921600
   - Check firmware configuration matches
   - Try lower baud rate for testing

3. **Check power sequencing**:
   - Ensure control board powers on before ESP32
   - Verify power sequencing is correct
   - Check for power-related issues

4. **Review serial logs**:
   - Check ESP32 serial output for errors
   - Check Pico serial output (if accessible)
   - Look for communication errors

### ESP32 Not Connecting to WiFi

**Symptoms:**
- Cannot connect to WiFi network
- Stuck in access point mode
- Connection drops frequently

**Solutions:**
1. **Check credentials**:
   - Verify WiFi password is correct
   - Check SSID matches exactly
   - Try re-entering credentials

2. **Check network**:
   - Verify 2.4GHz network (ESP32 doesn't support 5GHz)
   - Check signal strength
   - Move closer to router

3. **Check router**:
   - Some routers block new devices
   - Check router firewall settings
   - Try different network

4. **Reset and reconfigure**:
   - Hold reset button on ESP32
   - Reconfigure WiFi
   - Try static IP if DHCP fails

## Temperature Issues

### Temperature Not Reaching Setpoint

**Symptoms:**
- Temperature stuck below setpoint
- Temperature not rising
- Heaters not activating

**Solutions:**
1. **Check heater connections**:
   - Verify SSR trigger connections
   - Check SSR power connections (mains)
   - Verify SSR is receiving trigger signal

2. **Check power supply**:
   - Verify adequate electrical supply
   - Check circuit breaker
   - Verify voltage is correct

3. **Check SSR**:
   - Test SSR with multimeter
   - Verify SSR is switching
   - Check for damaged SSR

4. **Review diagnostics**:
   - Check for error messages
   - Review temperature logs
   - Check PID parameters

### Temperature Unstable

**Symptoms:**
- Temperature oscillating
- Large temperature swings
- Inconsistent readings

**Solutions:**
1. **Check PID parameters**:
   - Default values work for most machines
   - May need tuning for your machine
   - Make small adjustments

2. **Check sensor**:
   - Verify sensor is working correctly
   - Check sensor wiring
   - Verify sensor type matches configuration

3. **Check wiring**:
   - Loose connections cause instability
   - Verify all connections are secure
   - Check for damaged wires

4. **Review diagnostics**:
   - Check temperature graphs
   - Look for patterns
   - Review error logs

## Sensor Issues

### No Sensor Readings

**Symptoms:**
- Temperature readings show 0°C or invalid
- Pressure reading is 0
- Water level not detected

**Solutions:**
1. **Check sensor wiring**:
   - Verify sensor connections to control board
   - Check for loose connections
   - Verify correct terminals

2. **Check sensor types**:
   - Ensure NTC thermistors match configuration (100K vs 50K)
   - Verify thermocouple type (K-type)
   - Check pressure transducer range (0-16 bar)

3. **Check sensor installation**:
   - Verify sensors are properly installed
   - Check thermal paste on temperature sensors
   - Verify pressure transducer is connected to brew path

4. **Review diagnostics**:
   - Check diagnostic logs
   - Review sensor readings
   - Check for sensor errors

## Machine Control Issues

### Machine Won't Turn On

**Symptoms:**
- Power button doesn't work
- Machine stays in STANDBY
- No response to commands

**Solutions:**
1. **Check power connection**:
   - Verify mains power is connected
   - Check fuse is installed and not blown
   - Verify L, N, PE connections

2. **Check control board**:
   - Verify control board is powered
   - Check for error indicators
   - Review diagnostic logs

3. **Check for errors**:
   - Review error logs
   - Check for fault conditions
   - Verify safety interlocks

4. **Try manual reset**:
   - Power cycle machine
   - Check for recovery
   - Review logs after reset

### Pump Not Starting

**Symptoms:**
- Pump doesn't activate when brewing
- No pressure during shot
- Pump relay not switching

**Solutions:**
1. **Check relay**:
   - Verify pump relay connections
   - Test relay with multimeter
   - Check for damaged relay

2. **Check pump**:
   - Verify pump is connected
   - Check pump power supply
   - Test pump directly

3. **Check wiring**:
   - Verify pump wiring to relay
   - Check for loose connections
   - Verify correct terminals

4. **Review diagnostics**:
   - Check relay activation in logs
   - Review error messages
   - Check for pump-related errors

## Web Interface Issues

### Interface Not Loading

**Symptoms:**
- Web page doesn't load
- Blank page or errors
- Cannot access interface

**Solutions:**
1. **Check connection**:
   - Verify you're on same network
   - Check IP address is correct
   - Try `http://brewos.local` (mDNS)

2. **Check browser**:
   - Try different browser
   - Clear browser cache
   - Try incognito/private mode

3. **Check ESP32**:
   - Verify ESP32 is powered
   - Check WiFi connection
   - Review serial logs

4. **Check web files**:
   - Verify web files are uploaded
   - Try re-uploading web files
   - Check filesystem

### No Real-Time Updates

**Symptoms:**
- Data doesn't update
- Stale readings
- WebSocket connection issues

**Solutions:**
1. **Check WebSocket**:
   - Look for connection status indicator
   - Verify WebSocket is connected
   - Check browser console for errors

2. **Check network**:
   - Verify network connectivity
   - Check for firewall blocking WebSocket
   - Try different network

3. **Refresh page**:
   - Sometimes reconnection needed
   - Refresh browser page
   - Check connection status

4. **Review logs**:
   - Check for WebSocket errors
   - Review connection logs
   - Check for network issues

## Still Having Issues?

If you've tried the solutions above:
- Check [Error Codes](Error-Codes.md) for specific errors
- Use [Diagnostics](Diagnostics.md) tools
- See [Getting Help](Getting-Help.md) for community support

---

**Next:** [Error Codes](Error-Codes.md) or [Diagnostics](Diagnostics.md)

