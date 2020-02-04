---
layout: post
title: laptop-wifi-flowchart.py
---

# laptop-wifi-flowchart.py

```
# Laptop wifi flowchart: https://www.ifitjams.com/connect.htm

answer = input("See wireless network? ")
if answer == "yes":
    answer = input("Works with security off? ")
    if answer == "yes":
        print("Password or verification selected incorrect")
    else:
        answer = input("Works with ethernet? ")
        if answer == "yes":
            print("Check default settings on router")
        else:
            print("Check firewall")
else:
    answer = input("Is it turned on? ")
    if answer == "yes":
        print("Check if router is in range")
    else:
        print("Turn it on!")

```

