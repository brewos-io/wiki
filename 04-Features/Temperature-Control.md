# Temperature Control

BrewOS provides precise PID (Proportional-Integral-Derivative) temperature control for consistent espresso extraction.

## Overview

Temperature control is critical for espresso quality. BrewOS uses advanced PID control algorithms to maintain temperature within 0.1°C of your setpoint, ensuring consistent shots every time.

## Features

### Dual Boiler Control

For dual boiler machines:
- **Independent control** - Separate PID loops for brew and steam boilers
- **Independent setpoints** - Set brew and steam temperatures separately
- **No interference** - Brewing doesn't affect steam temperature

### Single Boiler Control

For single boiler machines:
- **Single PID loop** - Controls one boiler
- **Temperature surfing** - Manual temperature management required
- **Brew/steam switching** - Switch between brew and steam modes

### Heat Exchanger Control

For HX machines:
- **Steam boiler control** - PID controls steam boiler
- **Group head monitoring** - Thermocouple monitors group head temperature
- **HX management** - Automatic HX temperature management

## PID Control

### How It Works

PID control uses three components:
- **Proportional (P)** - Responds to current error
- **Integral (I)** - Eliminates steady-state error
- **Derivative (D)** - Reduces overshoot

### Temperature Stability

- **Target stability**: ±0.1°C
- **Response time**: Fast response to setpoint changes
- **Overshoot protection**: Minimal overshoot on startup

### PID Tuning

Default PID parameters work well for most machines. Advanced users can tune:
- **P value** - Proportional gain
- **I value** - Integral gain
- **D value** - Derivative gain

**Warning:** Incorrect PID tuning can cause instability. Only modify if you understand PID control.

## Temperature Zones

### Brew Boiler

- **Typical setpoint**: 93-95°C (200-203°F)
- **Control**: PID maintains setpoint
- **Monitoring**: Real-time temperature display
- **Stability**: ±0.1°C

### Steam Boiler

- **Typical setpoint**: 140-145°C (284-293°F)
- **Control**: Independent PID loop
- **Monitoring**: Real-time temperature display
- **Auto-fill**: Automatic water level management

### Group Head

- **Monitoring**: K-type thermocouple
- **Real-time display**: Group head temperature shown
- **Shot quality**: Critical for consistent extraction
- **No control**: Group head is passive (monitored only)

## Configuration

### Setting Temperatures

1. **From Dashboard**:
   - Click temperature gauge
   - Adjust setpoint slider
   - Changes apply immediately

2. **From Settings**:
   - Go to Settings → Temperature
   - Set brew and steam temperatures
   - Save changes

### Temperature Units

- **Celsius** - Default, standard for espresso
- **Fahrenheit** - Available in settings
- **Conversion** - Automatic conversion in display

### Max Temperatures

Safety limits:
- **Brew max**: 100°C (212°F)
- **Steam max**: 165°C (329°F) - Safety shutdown
- **Over-temperature protection**: Automatic shutdown at 165°C

## Heating Strategies

BrewOS offers multiple heating strategies that control how the boilers heat up when you turn the machine on. Each strategy has different characteristics in terms of speed, power consumption, and electrical requirements. Understanding these strategies helps you choose the best one for your situation.

### How Heating Strategies Work

**The Problem:**
- Dual boiler machines have two large heating elements (brew and steam boilers)
- Each heater can draw 1000-2000W depending on the machine
- Running both simultaneously can draw 2000-4000W total
- Many home circuits are 15-20A (1800-2400W capacity)
- Running both heaters can trip circuit breakers or exceed capacity

**The Solution:**
- Different strategies control when each heater turns on
- Some strategies heat sequentially to reduce peak power
- Others heat in parallel for maximum speed
- Smart strategies balance both concerns

### Sequential (Default)

**How It Works:**
- **Phase 1**: Brew boiler heater turns on first, heats to setpoint (typically 93-95°C)
- **Phase 2**: Once brew boiler reaches setpoint, steam boiler heater turns on
- **Phase 3**: Steam boiler heats to setpoint (typically 140-145°C)
- Both boilers maintain temperature once at setpoint

**Power Profile:**
- Peak power: ~1500W (only one heater at a time)
- Average during heat-up: ~1200W
- Circuit requirement: 15A circuit sufficient
- Time to brew ready: ~10-15 minutes (faster than parallel for first shot)
- Time to steam ready: ~20-25 minutes total

**Advantages:**
- **Power efficient** - Lower peak power consumption (only one heater active)
- **Faster brew ready** - Brew temperature reached first (can pull shots sooner)
- **Circuit friendly** - Won't trip most home circuit breakers
- **Lower electrical load** - Good for older homes or shared circuits

**Disadvantages:**
- **Slower steam ready** - Steam takes longer to be available
- **Longer total time** - Both boilers ready takes longer than parallel

**Best For:**
- Most home users (default choice)
- Homes with 15A circuits
- When you primarily brew espresso (steam less critical)
- Energy-conscious users

### Parallel

**How It Works:**
- **Both heaters on simultaneously** - Brew and steam boilers heat at the same time
- **Independent control** - Each boiler's PID controls its own heater independently
- **Maximum speed** - Both reach setpoint as quickly as possible

**Power Profile:**
- Peak power: ~3000-4000W (both heaters simultaneously)
- Average during heat-up: ~2500W
- Circuit requirement: 20A+ circuit recommended
- Time to brew ready: ~10-15 minutes
- Time to steam ready: ~15-20 minutes (faster than sequential)

**Advantages:**
- **Faster overall** - Both boilers ready sooner
- **Maximum speed** - Shortest total heat-up time
- **Simultaneous readiness** - Both ready at approximately the same time

**Disadvantages:**
- **Higher power** - Requires significant electrical capacity
- **Circuit breaker risk** - May trip 15A circuits
- **Electrical load** - High demand on electrical system
- **Not suitable for all homes** - Requires dedicated 20A circuit typically

**Best For:**
- Commercial or high-end home setups
- Dedicated 20A+ circuits
- When speed is more important than power consumption
- When you need both brew and steam ready quickly

### Smart Stagger

**How It Works:**
- **Intelligent power management** - Monitors total power consumption
- **Adaptive timing** - Adjusts heater timing based on conditions
- **Power-aware** - Staggers heaters to stay within safe limits
- **Optimized sequence** - Balances speed and power constraints

**Power Profile:**
- Peak power: ~2000-2500W (managed to stay within limits)
- Average during heat-up: ~1800W
- Circuit requirement: 15-20A circuit (adapts to available capacity)
- Time to brew ready: ~10-15 minutes
- Time to steam ready: ~18-22 minutes

**Technical Details:**
- Monitors current draw and adjusts heater timing
- May briefly run both heaters if power allows
- Automatically reduces to sequential if power limit approached
- Adapts to your electrical system's capacity

**Advantages:**
- **Intelligent** - Adapts to your electrical system
- **Optimized** - Balances speed and power automatically
- **Adaptive** - Works with different circuit capacities
- **Recommended** - Best balance for most users
- **Safe** - Prevents circuit overload

**Disadvantages:**
- **Slightly more complex** - Behavior depends on conditions
- **Variable timing** - Heat-up time may vary

**Best For:**
- Users who want the best of both worlds
- Uncertain about circuit capacity
- Want automatic optimization
- Most home users (recommended choice)

### Brew Only

**How It Works:**
- **Brew boiler only** - Only the brew boiler heater is used
- **Steam boiler off** - Steam boiler remains cold (no heating)
- **Energy focused** - Minimal power consumption

**Power Profile:**
- Peak power: ~1500W (only brew heater)
- Average during heat-up: ~1200W
- Circuit requirement: 15A circuit sufficient
- Time to brew ready: ~10-15 minutes
- Steam: Not available (boiler remains cold)

**Advantages:**
- **Energy saving** - Lowest power consumption
- **Fast brew ready** - Brew temperature reached quickly
- **Circuit friendly** - Minimal electrical load

**Disadvantages:**
- **No steam** - Steam not available (boiler stays cold)
- **Limited functionality** - Can only brew espresso

**Best For:**
- Espresso-only users (no milk drinks)
- Energy-conscious users
- When steam capability isn't needed
- Low-power situations

### Choosing the Right Strategy

**Consider Your Electrical System:**
- Check your circuit breaker rating (15A or 20A)
- Consider other devices on the same circuit
- Dedicated circuit recommended for espresso machines
- Consult electrician if unsure

**Consider Your Usage:**
- **Mostly espresso**: Sequential or Brew Only
- **Espresso + milk drinks**: Sequential or Smart Stagger
- **Speed critical**: Parallel (if circuit allows)
- **Energy conscious**: Sequential or Brew Only

**Consider Your Machine:**
- Check machine's heater ratings (in manual or specifications)
- Higher wattage machines may need Sequential or Smart Stagger
- Lower wattage machines may handle Parallel better

**Recommendation:**
- Start with **Smart Stagger** - best balance for most users
- If circuit issues occur, switch to **Sequential**
- If you need maximum speed and have 20A circuit, use **Parallel**
- If you only brew espresso, **Brew Only** saves energy

## Monitoring

### Real-Time Display

- **Dashboard gauges** - Visual temperature display
- **Color coding** - Blue (cold), green (ready), red (hot)
- **Setpoint indicator** - Shows target temperature
- **Current reading** - Real-time temperature value

### Temperature Graphs

- **Historical view** - See temperature over time
- **Shot analysis** - Temperature during shot
- **Stability check** - Verify PID performance
- **Troubleshooting** - Identify temperature issues

## Best Practices

### Temperature Selection

- **Brew temperature**: 93-95°C typical
  - Lower (90-92°C): Lighter roasts, brighter flavors
  - Higher (95-97°C): Darker roasts, more extraction
- **Steam temperature**: 140-145°C typical
  - Higher: Faster steaming, more power
  - Lower: More control, gentler steaming

### Preheating

- **Allow time** - 15-20 minutes for full heat
- **Group head** - Important for consistent shots
- **Stability** - Wait for stable temperature
- **Schedules** - Use auto-on for morning routine

### Shot Quality

- **Consistent temperature** - Key to good shots
- **Group head monitoring** - Critical for quality
- **Recovery time** - Allow time between shots
- **Temperature stability** - Monitor for drift

## Troubleshooting

### Temperature Not Reaching Setpoint

- **Check heater connections** - Verify SSR triggers
- **Check power** - Verify adequate electrical supply
- **Check PID tuning** - May need adjustment
- **Review logs** - Check for errors

### Temperature Unstable

- **Check PID parameters** - May need tuning
- **Check sensor** - Verify sensor is working
- **Check wiring** - Loose connections cause issues
- **Review diagnostics** - Check for problems

### Over-Temperature

- **Safety shutdown** - Automatic at 165°C
- **Check SSR** - May be stuck on
- **Check sensor** - Verify sensor reading
- **Review logs** - Check for errors

## Advanced Topics

### PID Tuning

For advanced users:
1. **Start with defaults** - Default values work for most machines
2. **Make small changes** - Adjust one parameter at a time
3. **Test thoroughly** - Verify stability after changes
4. **Document changes** - Keep notes on what works

### Sensor Calibration

If temperatures seem inaccurate:
1. **Verify sensor type** - Ensure correct sensor type configured
2. **Check installation** - Proper thermal contact required
3. **Compare readings** - Use known good thermometer
4. **Adjust offset** - Use temperature offset if needed

## Related Features

- [Brewing Features](Brewing-Features.md) - Shot timer and brewing
- [Statistics](Statistics.md) - Temperature history
- [Scheduling](Scheduling.md) - Auto-on for preheating

---

**Next:** [Brewing Features](Brewing-Features.md)

