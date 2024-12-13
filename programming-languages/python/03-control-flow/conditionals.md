---
tags:
- control-flow
---

<br>

# Python Conditional Statements

> Conditional statements in Python allow you to execute different code blocks based on specific conditions. They are fundamental to control flow and decision making in programs.

<br>

### Key Characteristics

> - Indentation-based block structure
> - Multiple condition checking
> - Short-circuit evaluation
> - Truthy and falsy values
> - Pattern matching support (Python 3.10+)
> - Context management capabilities

<br>

---

<br>

## if, elif, else Statements

> The basic conditional statement structure in Python using if, elif, and else.

<br>

### Basic if Statement

> Simple condition checking:

```python
# Signal strength in light-minutes from Earth
signal_strength = 5

if signal_strength > 0:
    print("Signal detected from deep space probe!")
    
print("Signal detection check complete.")
```

```sh
Signal detected from deep space probe!
Signal detection check complete.
```

<br>

### if-else Statement

> Two-way decision making:

```python
# Negative means moving away from Earth, positive means moving towards Earth
asteroid_trajectory = -5

if asteroid_trajectory > 0:
    print("WARNING: Asteroid approaching Earth!")
else:
    print("Safe: Asteroid is moving away from Earth")
```

```sh
Safe: Asteroid is moving away from Earth
```

<br>

### if-elif-else Chain

> Multiple condition checking:

```python
# Shield strength percentage
shield_strength = 85

if shield_strength >= 90:
    print("Shields OPTIMAL - All systems nominal")
elif shield_strength >= 80:
    print("Shields GOOD - Minor wear detected")
elif shield_strength >= 70:
    print("Shields FAIR - Repairs recommended")
elif shield_strength >= 60:
    print("Shields CRITICAL - Immediate repairs required")
else:
    print("SHIELDS FAILING - Emergency protocols initiated!")
```

```sh
Shields GOOD - Minor wear detected
```

<br>

### Nested Conditions

> Conditional statements within other conditional statements:

```python
fuel_level = 95  # Percentage of fuel tank filled
systems_check = True  # All systems are functioning
weather_clear = True  # Weather conditions are suitable

if fuel_level >= 90:
    print("Fuel levels optimal for launch.")
    if systems_check:
        print("All systems are go.")
        if weather_clear:
            print("Weather conditions perfect - Launch authorized!")
        else:
            print("Launch delayed - Weather conditions unfavorable.")
    else:
        print("Launch aborted - System check failed!")
else:
    print("Launch aborted - Insufficient fuel!")
```

```sh
Fuel levels optimal for launch.
All systems are go.
Weather conditions perfect - Launch authorized!
```

<br>

### Compound Conditions

> Using logical operators (and, or, not):

```python
age = 30  # Age in Earth years
space_training = 2000  # Hours of zero-gravity training
health_score = 85  # Physical adaptation score out of 100

if age >= 25 and space_training >= 1500:
    if health_score >= 80:
        print("Approved. Your adaptation profile is excellent!")
    elif health_score >= 70:
        print("Pending. Additional physical conditioning required!")
    else:
        print("Denied. Health score below minimum requirements.")
else:
    print("Denied. Must be 25+ years old with 1500+ hours of training.")
```

```sh
Approved. Your adaptation profile is excellent!
```

<br>

---

<br>

## Match Statement

> The match statement (introduced in Python 3.10) provides advanced pattern matching capabilities, similar to switch statements in other languages but with more powerful features.

<br>

### Basic Match Pattern

> Simple value matching:

```python
def classify_solar_event(signature):
    match signature:
        case "flare":
            print("Solar flare detected - Monitoring X-ray flux levels")
        case "cme":
            print("Coronal Mass Ejection detected - Tracking particle density")
        case _:  # Default case
            print("Analyzing unusual solar activity patterns")

# Test different solar events
events = ["flare", "cme", "prominence"]
for event in events:
    print(f"\nProcessing solar observation: {event}")
    classify_solar_event(event)
```

```sh
Processing solar observation: flare
Solar flare detected - Monitoring X-ray flux levels

Processing solar observation: cme
Coronal Mass Ejection detected - Tracking particle density

Processing solar observation: prominence
Analyzing unusual solar activity patterns
```

<br>

### Pattern Matching with Literals

> Matching against different types of literal values:

```python
def classify_seismic_activity(magnitude):
    match magnitude:
        case 0:
            print("No seismic activity detected")
        case 1 | 2 | 3:
            print("Minor seismic activity - typical background level")
        case 5:
            print("Moderate earthquake detected")
        case 7:
            print("Major earthquake - initiating emergency protocols")
        case None:
            print("Seismograph malfunction")
        case "":
            print("No seismograph reading available")
        case _:
            print(f"Earthquake magnitude: {magnitude} - assessing impact")

# Test with different magnitudes
magnitudes = [0, 2, 5, 7, None, "", 4.5]
for mag in magnitudes:
    print(f"\nProcessing seismic reading: {mag}")
    classify_seismic_activity(mag)
```

```sh
Processing seismic reading: 0
No seismic activity detected

Processing seismic reading: 2
Minor seismic activity - typical background level

Processing seismic reading: 5
Moderate earthquake detected

Processing seismic reading: 7
Major earthquake - initiating emergency protocols

Processing seismic reading: None
Seismograph malfunction

Processing seismic reading: 
No seismograph reading available

Processing seismic reading: 4.5
Earthquake magnitude: 4.5 - assessing impact
```

<br>

### Sequence Patterns

> Matching sequences with various patterns:

```python
def analyze_satellite_position(coords):
    match coords:
        case (0, 0):
            print("Satellite at geostationary position above equator (Null Island)")
        case (0, lat):
            print(f"Satellite positioned over prime meridian at {lat}° latitude")
        case (lon, 0):
            print(f"Satellite positioned over equator at {lon}° longitude")
        case (lon, lat):
            print(f"Satellite at position: {lon}°E/W, {lat}°N/S")
        case _:
            print("Invalid coordinate format")

# Test with different satellite positions
positions = [
    (0, 0),      # Over Null Island
    (0, 35),     # Over prime meridian at 35°N
    (-75, 0),    # Over equator at 75°W
    (105, -15),  # At 105°E, 15°S
    [100, 45]    # Invalid format
]

for pos in positions:
    print(f"\nAnalyzing satellite position: {pos}")
    analyze_satellite_position(pos)
```

```sh
Analyzing satellite position: (0, 0)
Satellite at geostationary position above equator

Analyzing satellite position: (0, 35)
Satellite positioned over prime meridian at 35° latitude

Analyzing satellite position: (-75, 0)
Satellite positioned over equator at -75° longitude

Analyzing satellite position: (105, -15)
Satellite at position: 105°E/W, -15°N/S

Analyzing satellite position: [100, 45]
Satellite at position: 100°E/W, 45°N/S
```

<br>

### Guard Patterns

> Adding conditions to pattern matches:

```python
def analyze_temperature(value):
    match value:
        case int(temp) if temp < -273:
            print(f"Error: Temperature {temp}°C below absolute zero")
        case int(temp) if temp < 0:
            print(f"Sub-zero temperature: {temp}°C")
        case float(temp) if -273.15 <= temp <= -273.14:
            print(f"Temperature near absolute zero: {temp}°C")
        case float(temp) if temp > 5500:
            print(f"Solar-core temperature range: {temp}°C")
        case _:
            print(f"Standard temperature reading: {value}°C")

# Test with different temperature values
temperatures = [-300, -5, -273.15, 5778, 20.5]
for temp in temperatures:
    print(f"\nAnalyzing temperature: {temp}")
    analyze_temperature(temp)
```

```sh
Analyzing temperature: -300
Error: Temperature -300°C below absolute zero

Analyzing temperature: -5
Sub-zero temperature: -5°C

Analyzing temperature: -273.15
Temperature near absolute zero: -273.15°C

Analyzing temperature: 5778
Standard temperature reading: 5778°C

Analyzing temperature: 20.5
Standard temperature reading: 20.5°C
```

<br>

---

<br>

## Conditional Expressions

> Conditional expressions (also known as ternary operators) provide a concise way to write simple if-else statements in a single line.

<br>

### Basic Syntax

> The syntax is: `<value_if_true> if <condition> else <value_if_false>`

```python
# Basic ternary operator
x = 5
result = "Positive" if x > 0 else "Non-positive"
print(f"Number is: {result}")
```

```sh
Number is: Positive
```

<br>

```python
# Compare with traditional if-else
if x > 0:
    traditional_result = "Positive"
else:
    traditional_result = "Non-positive"
    
print(f"Same result using if-else: {traditional_result}")
```

```sh
Same result using if-else: Positive
```