---
layout: post
title: quadratic.py
---

# quadratic.py 

```
# My first program
# Author: Me
# Date: 1/14/2020


def quadratic(a, b, c):
    x = (-b + (b**2-4*a*c)**0.5)/(2*a)
    return x

# example:
#answer = quadratic(2, 7, 1)
#print("The result is %.2f" % answer)


# global variables
a = float(input("What is the value of a? "))
b = float(input("What is the value of b? "))
c = float(input("What is the value of c? "))

answer = quadratic(a, b, c)
print("The result is %.2f" % answer)
```

