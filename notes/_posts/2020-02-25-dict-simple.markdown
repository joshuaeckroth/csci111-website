---
layout: post
title: dict-simple.py
---

# dict-simple.py

```
# Dictionaries

# Chapter 11 in book


# Another datapoint to join int, float, string, boolean,
# and list. Now we add dictionary.

# Basic idea: dictionaries store key=>value pairs

weights = {}  # empty
weights = {"sugar glider": 140,
           "horse": 453592}
print(weights["horse"])
print(weights.keys())

if "cat" in weights:
    print(weights["cat"])
#print(weights["cat"]) # error

for k in weights:
    print(k, weights[k])
    
## Use list as value
ratings = {"Harry Potter": [4, 4, 5, 4, 3],
           "The Bible": [3, 4, 5, 3, 4, 2] }
from statistics import mean
print(mean(ratings["Harry Potter"]))

ratings["The Fountainhead"] = [2]
print(ratings)
ratings["The Fountainhead"].append(5)
print(ratings)

if "Catching Fire" not in ratings:
    ratings["Catching Fire"] = []
ratings["Catching Fire"].append(4)
print(ratings)
```

