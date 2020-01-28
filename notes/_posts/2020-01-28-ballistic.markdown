---
layout: post
title: ballistic.py
---

# ballistic.py 

```
import turtle

# define a function for making fractional ranges
def fractional_range(start, end, step):
    values = [start]
    # generate all the steps we need
    step_count = int((end-start)/step)
    for i in range(step_count):
        # take last value in list, add step value to it,
        # and put this new value at the end
        new_val = values[-1] + step
        # add this new_val to the list
        values.append(new_val)
    return values

def line(t, x, y, x2, y2, size=5, color="black"):
    t.penup()
    t.goto(x, y)
    t.pensize(size)
    t.pencolor(color)
    t.pendown()
    t.goto(x2, y2)

def point(t, x, y, size=5, color="black"):
    t.penup()
    t.goto(x, y)
    t.pensize(size)
    t.pencolor(color)
    t.pendown()
    t.dot()

def ballistic_horizontal(vx0, t):
    return vx0*t

g = 9.8
def ballistic_vertical(vy0, t):
    return vy0*t-0.5*g*t**2

myturtle = turtle.Turtle()
line(myturtle, -200, -1000, -200, 1000)
line(myturtle, -1000, 0, 1000, 0)

vx0 = float(input("vx0 = ? "))
vy0 = float(input("vy0 = ? "))

# create a list of times to plot
times = fractional_range(0, 5, 0.1)
for t in times:
    x = 20*ballistic_horizontal(vx0, t)-200
    y = 20*ballistic_vertical(vy0, t)
    point(myturtle, x, y)
```

