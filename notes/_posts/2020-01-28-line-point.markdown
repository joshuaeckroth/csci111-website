---
layout: post
title: line-point.py
---

# line-point.py 

```
# Lines & points for turtles

import turtle

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
    

myturtle = turtle.Turtle()
line(myturtle, 100, 100, 200, 200)
point(myturtle, 0, 0)
line(myturtle, 10, 300, -100, -500)
```

