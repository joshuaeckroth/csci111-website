---
layout: post
title: spongebob.py
---

# spongebob.py 

```
import turtle
import math

def draw_circle(t, x, y, r, fill="white", pen="black", size=10):
    t.penup()
    t.goto(x, y)
    t.pendown()
    t.pensize(size)
    t.pencolor(pen)
    t.fillcolor(fill)
    t.begin_fill()
    t.circle(r)
    t.end_fill()

def eye(t, x):
    draw_circle(t, x, 0, 100, "white", "black", 2)
    draw_circle(t, x, 50, 50, "blue", "black", 2)
    draw_circle(t, x, 80, 20, "black", "black", 2)

myturtle = turtle.Turtle()
myturtle.home()
myturtle.speed(0)
myturtle.color('red')
myturtle.pensize(10)

# eyes
eye(myturtle, -100)
eye(myturtle, 100)

# mouth
myturtle.penup()
myturtle.goto(-200, -100)
myturtle.right(90)
myturtle.pendown()
myturtle.circle(200, 180)
```

