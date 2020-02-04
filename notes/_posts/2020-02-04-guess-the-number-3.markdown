---
layout: post
title: guess-the-number-3.py
---

# guess-the-number-3.py

```
# Conditionals: if/elif/else

# Task: Guess-the-number game

import random
answer = random.randint(1, 100)

tries = 0

while True:
    guess = int(input("Guess: "))
    tries = tries + 1

    if guess == answer:
        print("Correct!")
        break
    elif guess > answer:
        print("Too high")
    else:
        print("Too low")

print("You took %d tries" % tries)
```

