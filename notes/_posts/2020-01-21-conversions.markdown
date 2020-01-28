---
layout: post
title: conversions.py
---

# conversions.py 

```
def meters2feet(meters):
    feet = 3.28*meters
    return feet

def feet2meters(feet):
    meters = feet/3.28
    return meters

def miles2feet(miles):
    feet = 5280*miles
    return feet

def kilometers2meters(km):
    meters = 1000*km
    return meters

def meters2kilometers(meters):
    km = meters/1000
    return km

def miles2kilometers(miles):
    feet = miles2feet(miles)
    meters = feet2meters(feet)
    km = meters2kilometers(meters)
    return km

x0 = miles2kilometers("10")

x1 = meters2feet(100)
print("100 meters is %.2f feet" % x1)

# TASK: write a function that converts
# miles to kilometers using the functions defined above

# miles2feet -> feet2meters -> meters2kilometers
x2 = miles2kilometers(26.2)
print("A marathon is %.2f km" % x2)
```

